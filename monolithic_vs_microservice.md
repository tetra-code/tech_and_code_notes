# Monolithic architecture
A monolithic architecture is when the software is built as a single unit.

A monolithic software is easier to maintain than a microservice software since the whole system is in a single unit

Properties of monlithic architecture:
- one code base where ALL business logic is grouped together
- everything can be managed in one single point. 
- suited for small scale projects/softwares
- usually a single database for all the data storage of the software

Pros
- convenient in the early stages of a software's life cycle. 
- easy of deployment - one executable file or directory
- easy to develop as only one code base
- one API that manages the entire communication of the software and its clients
- easier end-to-end testing

Cons
- hard to scale; can't scale individual components without affecting the other
- can't incorporate new technology as it is constrained by the technologies already in use
- small update requires deployment of the entire project
- one node failure will affect the entire project

# Microservice architecture
In a microservice architecture, a software is broken down into smaller services. Each of these services serve a specific purpose or specific business need. 

Transition from monolithic to microservice architecture doesn't reduce the complexity. It just makes the complexity more visible and more manageable. 

A microservice-based enterprise software can have hundreds, even thousands of service.

Properties of mircroservice architecture:
- decoupled servies; they are independent of each other
- separate code base for each service
- separate and private databases for each service
- often hand-to-hand with DevOps as it is the basis for continuous delivery practices; allow quick adaptation to user requirements. 
- often API gateway required to handle all the different APIs from multiple services
- suited for large scale enterprise projects/softwares

Pros:
- independent development, deployment, and management
- small focused team per service; easier communication and easier to understand code
- small codebase; minimized dependency and easier to add new features
- can add new technologies on top of preexisting one in a service
- fault tolerance; one node (service) failure doesn't affect the entire system
- easier scalability; isolated services mean each service can be easily scaled 
- data isolation; easier to update database schema

Cons
- each service requires independent deployment
- if services depend on each other, writing tests become more complicated. Mock tests are required
- multiple APIs mean an increase in network latency 
- complex API mapping across multiple services
- a service update may cause some backward or forward compatibility issues
