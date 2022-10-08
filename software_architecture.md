# Software Development Life Cycle or SDLC
Before focusing on the software design (implementation) any software engineer worth his salt will do the following tasks:
1. Spend 'reasonable' amount of time gathering the **business requirement** with/from a business analyst.
2. Create the **Software Requirement Specification** or **SRS** that covers all aspects such as testing, acceptance, deployment, maintenance, etc. 
3. Define and document the software architecture 

# Sofware Design vs Software Architeceture

## Software Design
Software design focuses on the lower-level (implementation) of the software. It is about designing the individual modules, classes, functions, usage, etc. This falls under the Sofware Development Life Cycle. 

It avoids uncertainty.

Examples of software design patterns:
- creational
- structural 
- behavioral

## Software Architecture
Software architecture focuses on the higher-level (structure) of the software. It refers to the fundamental structure or the process of the overall system. The goal is to define the software's fundamental properties. 

It manages uncertainty.

Examples of software architecture patterns:
- microservice 
- client-server pattern
- layered pattern (most common)
- server-less
- event-driven
- microkernel

Software architecture is one of the elements of the SDLC. The goal is to define (and document) processes that will make the actual development process easier. 

An architect seperates architecture characteristics into broad categories depending on the operation, structure, requirements, etc. Some important characteristics:

- Operational Architecture Characteristics
Availability
Performance
Reliability
Low fault tolerance
Scalability

- Structural Architecture Characteristics :
Configurability
Extensibility
Supportability
Portability
Maintainability

- Cross-Cutting Architecture Characteristics :
Accessibility
Security
Usability
Privacy
Feasibility

The **SOLID** principles helps to avoid any strategy or developmental failures:
- Single Responsibility: each service should have a single objective
- Open-Closed principle: software modules should be independent and expandable
- Liskov substitution pricinple: independent services should be able to communicate and substitute each other
- Interface segregation principle: Divide software into microservices such that there are no redundancies
- Dependency inversion principle: Higher-level modules shouldn't depend on lower-level modules and changes in higher level shouldn't affect the lower level

Limits to software architectures:
- Sometimes getting good tools and standardization becomes a problem for software architecture.
- Initial prediction of success of project based on architecture is not always possible.

# Layered architecture

# Monolithic architecture vs Microservice architecture

## Monolithic architecture
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

## Microservice architecture
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
