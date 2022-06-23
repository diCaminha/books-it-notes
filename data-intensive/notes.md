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



