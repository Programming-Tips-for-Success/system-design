Encoding actual URL

Design a URL shortening solution

How to design a URL shortening service like goo.gl?

This one is another common system design question. If you are given a (typically) long URL, how would you design a service that would generate a shorter and unique alias for it? If you are not familiar with the URL shortener service, have a look at some of the popular ones like goo.gl from Google and bit.ly, which is used by Twitter.

Make sure to provide a database schema and rationale behind some design decisions, e.g. how long you keep the data, how to get stats and analytics, etc. 


Designing a URL Shortening service like TinyURL
Let's design a URL shortening service like TinyURL. This service will provide short aliases redirecting to long URLs.

Similar services: bit.ly, goo.gl, qlink.me


1. Why do we need URL shortening?
2. Requirements and Goals of the System
3. Capacity Estimation and Constraints
4. System APIs
5. Database Design
Database Schema:
6. Basic System Design and Algorithm
a. Encoding actual URL
b. Generating keys offline
7. Data Partitioning and Replication
8. Cache
9. Load Balancer (LB)
10. Purging or DB cleanup
11. Telemetry
12. Security and Permissions


Our URL shortening system should meet the following requirements:

Functional Requirements:

Given a URL, our service should generate a shorter and unique alias of it. This is called a short link. This link should be short enough to be easily copied and pasted into applications.
When users access a short link, our service should redirect them to the original link.
Users should optionally be able to pick a custom short link for their URL.
Links will expire after a standard default timespan. Users should be able to specify the expiration time.
Non-Functional Requirements:

The system should be highly available. This is required because, if our service is down, all the URL redirections will start failing.
URL redirection should happen in real-time with minimal latency.
Shortened links should not be guessable (not predictable).
Extended Requirements:

Analytics; e.g., how many times a redirection happened?
Our service should also be accessible through REST APIs by other services.

Capacity Estimation and Constraints
Our system will be read-heavy. There will be lots of redirection requests compared to new URL shortenings. Let’s assume a 100:1 ratio between read and write.

Traffic estimates: Assuming, we will have 500M new URL shortenings per month, with 100:1 read/write ratio, we can expect 50B redirections during the same period:

100 * 500M => 50B
What would be Queries Per Second (QPS) for our system? New URLs shortenings per second:

500 million / (30 days * 24 hours * 3600 seconds) = ~200 URLs/s
Considering 100:1 read/write ratio, URLs redirections per second will be:

100 * 200 URLs/s = 20K/s
Storage estimates: Let’s assume we store every URL shortening request (and associated shortened link) for 5 years. Since we expect to have 500M new URLs every month, the total number of objects we expect to store will be 30 billion:

500 million * 5 years * 12 months = 30 billion
Let’s assume that each stored object will be approximately 500 bytes (just a ballpark estimate–we will dig into it later). We will need 15TB of total storage:

30 billion * 500 bytes = 15 TB

Bandwidth estimates: For write requests, since we expect 200 new URLs every second, total incoming data for our service will be 100KB per second:

200 * 500 bytes = 100 KB/s
For read requests, since every second we expect ~20K URLs redirections, total outgoing data for our service would be 10MB per second:

20K * 500 bytes = ~10 MB/s
Memory estimates: If we want to cache some of the hot URLs that are frequently accessed, how much memory will we need to store them? If we follow the 80-20 rule, meaning 20% of URLs generate 80% of traffic, we would like to cache these 20% hot URLs.

Since we have 20K requests per second, we will be getting 1.7 billion requests per day:

20K * 3600 seconds * 24 hours = ~1.7 billion
To cache 20% of these requests, we will need 170GB of memory.

0.2 * 1.7 billion * 500 bytes = ~170GB
One thing to note here is that since there will be many duplicate requests (of the same URL), our actual memory usage will be less than 170GB.

We can have SOAP or REST APIs to expose the functionality of our service. Following could be the definitions of the APIs for creating and deleting URLs:

System APIs-
createURL(api_dev_key, original_url, custom_alias=None, user_name=None, expire_date=None)
Parameters:
api_dev_key (string): The API developer key of a registered account. This will be used to, among other things, throttle users based on their allocated quota.
original_url (string): Original URL to be shortened.
custom_alias (string): Optional custom key for the URL.
user_name (string): Optional user name to be used in the encoding.
expire_date (string): Optional expiration date for the shortened URL.

Returns: (string)
A successful insertion returns the shortened URL; otherwise, it returns an error code.

deleteURL(api_dev_key, url_key)
Where “url_key” is a string representing the shortened URL to be retrieved; a successful deletion returns ‘URL Removed’.


A few observations about the nature of the data we will store:
We need to store billions of records.
Each object we store is small (less than 1K).
There are no relationships between records—other than storing which user created a URL.
Our service is read-heavy.
Database Schema: 
We would need two tables: one for storing information about the URL mappings and one for the user’s data who created the short link.

Since we anticipate storing billions of rows, and we don’t need to use relationships between objects – a NoSQL store like DynamoDB, Cassandra or Riak is a better choice. A NoSQL choice would also be easier to scale.
