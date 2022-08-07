# Event-Sourcing
Technical Paper on Event Sourcing Architecture


## Event Sourcing :
It's a way of storing data that is probably very different than what you're used to.
For example lets take you some database in which some data is stored, if some user makes the changes to database and saved it. Finally, the database you will be seeing is final one you will not have any idea or the informaton of data before the user changed it. Where as in Event Sourcing ensures that all changes to database are stored as a sequence of events i.e each of the event is recorded in append only mode whenever some activity happens. Not just can we query these events, we can also use the event log to reconstruct past states, and as a foundation to automatically adjust the state to cope with retroactive changes.

Lets understand Event Sourcing through e-commerce shopping. Whenever the user add any items or delete the items in the cart, each it is stored as sequence of events as shown in the image below.

![image](https://user-images.githubusercontent.com/104886848/183288955-2870c920-d2a5-48d5-911e-7f93b63593b2.png)

We can see all the changes that had happened each time i.e through adding, deleting or modifying through event log.

## Advantages of Event Sourcing Architecture:
 - We can restore the data at any certain point in time, as data is stored in database as a chain/sequence of events.
 - Events are simple objects that describe some action that had occurred, together with any associated data required to describe the action represented by the event. Events don't directly update a data store. They're simply recorded for handling at the appropriate time. This can simplify implementation and management.
 - In a database it’s difficult to determine how data may have arrived at its current state.  With event sourcing we can always retrace the steps that had happended.
 - With append only mode, we can chunk the data into small units and process that parallely which will resuce the processing time.
 - The event store raises events, and tasks perform operations in response to those events. This decoupling of the tasks from the events provides flexibility and extensibility.
 - Because event sourcing maintains the complete history of each operation, implementing temporal queries and reconstructing the historical state at point in time is possible
 - Event soucring provide 100 percent accurate audit logging.

 
 ## Event Sourcing Implementation:
 Event sourcing can be implemented by storing the data and reading it from the event log. This can be simply implemented by using text or any other file in append only mode in which the each line will represent the events that had occured.Logs are the very common pattern in software industry, used via technologies such as messaging integrations (brokers, MOMs) and event streaming systems. 

## Conclusion:
Event sourcing is offering a pattern with some good advantages. Event log also serves as a long-timeframe pub/sub mechanism. New, addition, deletion and modification  events will easily get added serially at any point, where they can then process the event log parallely.
However as with large architectural design decision, great care needs to be taken to ensure it is appropriate for a particular use case. Constraints around domain model complexity, data consistency/availability requirements, data growth rates and system lifespan/long-term scalability all needed to be considered. Consideration also needs to be given for the teams that will be developing and supporting such a system over its lifespan as it is unfamiliar style of programming for most of the developrs.
