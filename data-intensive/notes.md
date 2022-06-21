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

