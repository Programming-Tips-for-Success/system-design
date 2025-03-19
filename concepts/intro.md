approach to tackle system design interviews problem:

1. Discuss functional and non functional requirements
2. Identify users and channels
3. Discuss scale of traffic
4. Come up with basic design for 1 user ( make sure you don't use any load balancer or queues, just service and database)
5. Now introduce message queue, load balancer, websocket etc later only if they are needed
6. Discuss each component, what if things break or there is a bottleneck (hotspot) how would you handle this. This is most important part.
7. Discuss data in transit and data in persistence.
8. Discuss Choice of DB (remember don't mention specific name like aerospike but use a basic database term like in-memory db also why would you need it)
9. Discuss replication,  caching, and partitioning (mention partition key and sort key).
10. Do a quick storage capacity estimation for next 5 years
11. Finally see if you need any specific data structure to improve upon the time complexity of core operation. Example: bloom filter, sorted set.

Things to cover while designing
High-Level Design - how hld works
Low-Level Design

System design is the process of designing a system(any software application). So when we start designing any software system few things we keep in mind.

What all features application will have?
How many users will access this?
At a time how many requests will come to the application?
How much do we want to scale our application and what is the allowed cost for that?

design for many billions of users Live System?

Design and implementation of low-latency, high-availability, and performant applications.  

functional and non-functional requirements

High-Level Design:

It includes top-level design of our entire application Like how much scalability, cost, and request applications can handle at a time. This work is mostly done by the Principle Engineers or Product Managers. 

What are Load balancers, Caching, Compute Power, SQL vs NoSQL, Streaming, Data Modeling, etc? 

Low-Level Design:
Suppose in the given problem like(Create a note-taking app) interviewer will ask questions like how you will organize data, how to fetch data, which data structure to use and why, test cases, UML, ER Diagram, etc.

UML is used for planning software development, and is used in many different diagrams for various purposes. ER diagrams do not focus on the software, but rather the modelling of databases, which are usually part of a software system. UML diagrams are broader, and have many uses, and ERDs only have one purpose.

In organizations when any project comes then HLD is done by the PMs, and solution architects but the low-level design is done by the SDE-1 and SDE-2.

Scalable System & Distributed System -
a distributed system is a collection of computers that work together to form a single computer for the end-user. All these distributed machines have one shared state and operate concurrently.
, there are three kinds of distributed computing systems with the following goals:

Distributed Information Systems: distribute information across different servers via multiple communication models
Distributed Pervasive Systems: use embedded computer devices (i.e. ECG monitors, sensors, mobile devices)
Distributed Computing Systems: computers in a network communicate via message passing
Benefits of a distributed system

Scaling: A distributed system allows you to scale horizontally so you can account for more traffic.
Modular growth: There is almost no cap on how much you can scale.
Fault tolerance: Distributed systems are more fault tolerant than a single machine.
Cost effective: The initial cost is higher than a traditional system, but because of their scalability, they quickly become more cost effective
Low latency: Users can have a node in multiple locations, so traffic will hit the closet node
Efficiency: Distributed systems break complex data into smaller pieces
Parallelism: Distributed systems can be designed for parallelism, where multiple processors divide up a complex problem into pieces

The Scalable System in Distributed System refers to the system in which there is a possibility of extending the system as the number of users and resources grows with time.
Horizontal scaling means adding more servers into your pool of resources. Vertical scaling means scaling by adding more power (CPU, RAM, Storage, etc.) to your existing servers.
Horizontal-scaling is easier to scale dynamically, and vertical-scaling is limited to the capacity of a single server.
Good examples of horizontal scaling are Cassandra and MongoDB. They make it easy to scale horizontally by adding more machines. An example of vertical scaling is MySQL, as you scale by switching from smaller to bigger machines.

Design issues with distributed systems
Failure Handling: Failure handling can be difficult with distributed systems because some components fail while others continue to function. This can often serve as an advantage to prevent large-scale failures, but it also lead to more complexity when it comes to troubleshooting and debugging.
Concurrency: A common issue occurs when several clients attempt to access a shared resource simultaneously. You must ensure that all resources are safe in a concurrent environment.
Security issues: Data security and sharing have increased risks in distributed computer systems. The network has to be secured, and users must be able to safely access replicated data across multiple locations.
Higher initial infrastructure costs: The initial deployment cost of a distributed system can be higher than a single system. This pricing includes basic network setup issues, such as transmission, high load, and loss of information.

Cloud computing and distributed systems are different, but they use similar concepts. Distributed computing uses distributed systems by spreading tasks across many machines. Cloud computing, on the other hand, uses network hosted servers for storage, process, data management

Priorities like load-balancing, replication, auto-scaling, and automated back-ups can be made easy with cloud computing. Cloud building tools like Docker, Amazon Web Services (AWS), Google Cloud Services, or Azure make it possible to create such systems quickly, and many teams opt to build distributed systems alongside these technologies.

implement Distributed system software to ensure high reliability, fault tolerance, and scalability

class diagrams, database designs, and flowcharts    

Low Level Design (SOLID, OOP, Schema Design, Machine Coding)
High Level Design (load balancing, caching, NoSQL, .. )       

Disaster recovery, Consistency, Idempotence ( insta posts count number does not increase on multiple taps, payment system, twitter button tweet button click )

Idempotence is executing the same action multiple times, but the result is as if the operation was applied just once.

throttling
It is a defensive measure and 3 possible reactions could be
slowing down the incoming requests
rejecting the surplus requests
ignoring the surplus requests
Why do we need throttling in the first place?
to prevent system abuse
to allow the amount of traffic we could handle
control the consumption cost
prevent cascading failures leading to a massive outage

splitting a db across multiple machines called sharding

Vertical sharding is splitting a database by the tables. Shards will hold a subset of tables. For example, all payments-related tables go to one shard, while all auth-related tables go to another

Sharding is super-important when you want to handle the traffic that cannot be handled through one server. Sharding comes in two flavors - Horizontal and Vertical. In horizontal sharding, we split the table by rows and keep them on separate servers. In vertical sharding, we distribute the tables across multiple database servers.

use existing HTTP Clients like Postman, cURL, Requests
use caches like Ngnix, HA Proxy, and Varnish to boost performance
use monitoring tools like Distributed Tracing
use load balancers to uniformly distribute the load
use SSL to get out-of-the-box security

The simplest definition of ‘scalability’ is the potential of your application to cope with increasing numbers of users simultaneously interacting with it

https://tianpan.co/notes/2016-02-13-crack-the-system-design-interview  hld

https://www.hiredintech.com/classrooms/system-design/lesson/53  complete guide

https://www.youtube.com/watch?v=1JYGv-t1PX0&feature=youtu.be   Insights about System Design Interview

https://leetcode.com/discuss/general-discussion/1105898/System-Design%3A-Introduction-to-Distributed-Systems-or-Designing-a-highly-available-system

medium.com/partha-pratim-sanyal/system-design-doordash-a-prepared-food-delivery-service-bf44093388e2

https://docs.google.com/document/d/1BXmVmU_2bgFVBa_xnBto7KYDfVz2IYQ7/edit  books, keywords, channels, algos, design pattern

https://gitee.com/awesome-lib/awesome-scalability        topics

https://mlsdev.com/blog/70-how-to-develop-an-app-like-instagram  insta

http://blog.gainlo.co/index.php/category/system-design-interview-questions/  different design avail

https://www.interviewbit.com/system-design-interview-questions

https://arpitbhayani.me/masterclass/    topics

https://practice.geeksforgeeks.org/courses/system-design-live?  course details

failover servers - horizontal scaling
periodic backup -> cold standby
replication of db -> warm standby

horizontal scaling of db : sharding

normalized and denormalized data
Updates in a denormalized table can involve iterating through every row, looking for copies of data that must be updated. They also take up more space.

Cassandra consists of nodes where any node can serve as the master. It accomplishes this at the expense of consistency.

Single-master designs favor consistency and partition tolerance. Although in principle availability it what's given up, in practice modern NoSQL databases have highly redundant master nodes that can quickly replace themselves in the event of failure.

A "least recently used" policy is most commonly used, and evicts data that hasn't been accessed in the longest amount of time once memory for the cache fills up. LRU

If you need to minimize client latency for retrieving static data around the world at any cost, you would use:
Content Delivery Networks (CDN's) are aimed at the problem of global traffic and minimizing latency due to long network hops. Load balancers and caching technologies such as Redis can also be parts of low-latency designs, but are not specifically for the problem of global traffic.

binary search table - in order traversal- recursively

With a nominal complexity of O(1) for inserts, lookups, and deletions, hash tables are hard to beat. It is important however to have a good hash function and a sufficient number of buckets to avoid hash collisions, which could cause the complexity to degenerate to O(n) worst case. - lookup

Event-driven architecture (EDA) -
scalable, extensible, and resilient
Real-time processing
Loose Coupling
https://www.linkedin.com/pulse/event-driven-architecture-abhay-kumar/

https://www.udemy.com/course/system-design-a-comprehensive-guide/
https://www.udemy.com/course/rocking-system-design/
https://www.udemy.com/course/pragmatic-system-design/

https://bytebytego.com/pricing for system design
https://www.tryexponent.com/?ref=javinpaul2
https://www.designgurus.io/?aff=84Y9hP

UML- Unified Modeling Language
An easy to read system of symbols, Definition shapes, and notations used in software system modeling and planning
Class diagrams
Object diagrams
Key attributes
Sequence diagrams
Uses
Activity diagrams
Communication diagrams
Plan and model software systems Show how entities operate within a system, with all possible interactions

ERD
Entity Relationship Diagram
A diagram that shows real-world items that exist in a database, and uses symbols and shapes to show relationships, attributes, and other important details
Entities Attributes Cardinality
Ordinality
Number of relationship instances
Plan databases
Ensure all entities function properly Defines attributes of entities

+ relationships between classes- Association,Bi-directional, Multiplicity, Aggregation, Composition, Generalization, Dependency, inheritance

(DR) Disaster recovery testing is the process to ensure that an organization can restore data and applications and continue operations after an interruption of its services, critical IT failure or complete disruption. It is necessary to document this process and review it from time to time with their clients.

https://www.hellointerview.com/learn/system-design/problem-breakdowns/ticketmaster