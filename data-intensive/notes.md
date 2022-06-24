## Chapter 1

When you create a whole solution, combining several tools in order to provide a service, the API (application programming interface) usually hides those implementations from the client. 

When you have a system like that, you are not only an application developer, but also a **data system designer**.

Trick questions related to developing a data system:
1. how to ensure the data remains correct and complete, even when things go wrong internally?
2. how to provide consistently good performance to clients, even when part of the system is down?
3. how to scale to handle increase of requests?


The book focus on three concerns:
- Reliability: the system should continue to work correctly (doing its activities in a desired level of performance) even in the face of adversity (hardware/software faults, and even human error)
- Scalability: As the system grows (data volume, traffic, complexity) there should be reasonable ways of dealing with that growth.
- Maintainability: New people should work on the system productively.


### Reliability:
Continue to work properly, even when things go wrong.

- the application performs what the user expects
- it can tolerate the user making mistakes or acting in unexpected ways
- prevents unhautorized access


=> Wardware Faults
- hard disk crashs
- memory leak
- power grid has a blackout

The first and immediate response to this type of fault is **redundance**.
  - disk in RAID configuration
  - dual power supplies
  - hot-swappable CPU
  - datacenters

BUT, nowadays the data volume and application's computing demands increased a lot, and more applications have begun using larger numbers of machines, increasing the rate of hardware faults.

AWS, for instance, where its virtual machine is very common to become unavaliable without even warning.
(aws prioritize elasticity and flexibility, over single-machine reliability)



=> Software Errors
Bugs and broken code

=> Human Errors
Manual work


### Scalability:
it means considering questions like: if the system grows in a particular way, what are our options for coping with the growth? and how can we add computing resource to handle the additional load?

Describing Load:
  - requests per second to a web server
  - number of reads to writes in a database
  - number of active users at the same time in a chat room
  - the hit rate on a cache

Sometimes your bottleneck is dominated by a small part of extreme cases:
#### Twitter's case:
In order to deliver the tweets, twitter would should beetween two approaches:
1. saves the tweet (from author A) in a global/unique place. And any time an follower user from author A goes to his timeline, a query join is done to get the tweets from author A (and all others following authors)
2. creates a cache timeline for each user. When author A tweet something, this tweet is added to ALL the timeline caches for each following. Then when the user goes to his timeline, it will just get from the cache timeline, super fast.

First, twitter started with the 1 approach. Then, as it scales in number of users and authors, the processe of building a timeline by querying and joing info started to become very painful and expensive. (And twitter promises to deliver a tweet for the following timeline in 5 seconds). So, to solve this problem, twitter adopted the solution 2. BUT, this also didnt work out. Considering famous authors (with millions of followers), imagine how many tweets they send, and how many updates in tweet timelines it will have to apply. Also painful. So, the final/current solution is to get something mixed betweeen solutions 1 and 2. For famous author, do 1. For others, do 2.
"""

Describing Performance:

*response time*
  > The time between the user sending a request and receiving a response form the online system.

We need to measure response time not only based in a single number. But as a distribution of many analysis, that you can measure.

It's common to see the average of response time. Some use the mean to calculate it, but it is not the best way. Because we need to get a value that most of the users wait, and the mean doesnt tell us how many actually experience that delay. 
for example: Suppos 90% of the users experience a response time of 100ms, and a single request expend 5s. So this unique expensive request will elevate the mean. 

a better way to measure is using the **median**.


Curiosity: Amazon had notice that 100ms increase in response time reduce sales in 1%, and 1s increase response time reduce in 16%

Percentiles is very used in SLA and SLO

Example of contract:
 - the service is considered to be up if it has a median response time of 300ms
 - the service is considered to be up if has a percentiles of 99th under 1s
