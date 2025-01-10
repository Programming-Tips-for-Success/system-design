caching mechanism- varnish, Memcached, Redis(data structure server)

· Different caching strategy.

What are the caching types for Web APIs?

Caching: (Distributed System concept)

caching will enable you to make vastly better use of the resources you already have.

Caches take advantage of the locality of reference principle: recently requested data is likely to be requested again. They are used in almost every layer of computing: hardware, operating systems, web browsers, and web applications,

cache is like short-term memory: it has a limited amount of space, but is typically faster than the original data source and contains the most recently accessed item.

Application server cache

Content Distribution Network (CDN)

CDNs are a kind of cache that comes into play for sites serving large amounts of static media. A request will first ask the CDN for a piece of static media; the CDN will serve that content if it has it locally available. If it isn’t available, the CDN will query the back-end servers for the file, cache it locally, and serve it to the requesting user.

If the system we are building isn’t yet large enough to have its own CDN, we can ease a future transition by serving the static media off a separate subdomain (e.g. static.yourservice.com) using a lightweight HTTP server like Nginx, and cut over the DNS from your servers to a CDN later.

The benefit of CDN is Pre-Caching, Distributed Regional Servers, and Reduce Load and Bandwidth.

Cache Invalidation

caching is fantastic, but it does require some maintenance for keeping the cache coherent with the source of truth (e.g., database). If the data is modified in the database, it should be invalidated in the cache; if not, this can cause inconsistent application behaviour.

Most common cache eviction policies:

First In First Out (FIFO): The cache evicts the first block accessed first without any regard to how often or how many times it was accessed before.

Last In First Out (LIFO): The cache evicts the block accessed most recently first without any regard to how often or how many times it was accessed before.

Least Recently Used (LRU): Discards the least recently used items first.

Most Recently Used (MRU): Discards, in contrast to LRU, the most recently used items first.

Least Frequently Used (LFU): Counts how often an item is needed. Those that are used least often are discarded first.

Random Replacement (RR): Randomly selects a candidate item and discards it to make space when necessary.

Redis : Redis is an open-source (BSD licensed), in-memory data structure store used as a database, cache, and message broker.

 Redis is an in-memory database, its data access operations are faster than any other disk-bound database could deliver

 Redis for real-time analytics

Redis for session management - f your application uses sessions to track authenticated users and manage user-specific data, Redis is a perfect fit to use as session storag

Redis as a Queue

Caching-
Caching is a state management technique that can store a copy of the data in memory.
To increase the performance of the application and improve the access time, caching is used. 
It exists in temporary storage, in other words when the data is no longer used then it expires. 
Using a cache we can retrieve the data from a database directly.
3 types-
Output Caching
Data Caching
Fragment Caching

What is a Session, in a web application?
A session is a unique instance of the browser. A single user can have multiple sessions, by visiting your application, with multiple instances of the browser running with a different session-id on his machine. 

Cloudflare