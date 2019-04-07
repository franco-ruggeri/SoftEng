# Multiplex cinema management.

A multiplex cinema is composed of several rooms, each room may show a different movie, with a different schedule. Each room has a specific seat capacity, to be strictly enforced for safety regulations.

Each seat in a room has an id. A management system for a multiplex cinema has to be built because there are several multiplex cinemas across Italy.

The management system will be used by **clerks** to **sell tickets** at a counter in the cinema. The sale of a ticket can also be done via Internet, the **customers** buy it connecting to a web site. A ticket is valid for a specific seat, in a specific room, for a specific show (movie and start time).

A ticket is unique and has a bar code. The ticket must be printed to guarantee admission. A ticket is sold only in the same day of the show, and only if there is a seat available. The user can choose the seat. A ticket is refundable, if not used.

Another function of the system is **admitting (or rejecting) people** to the rooms. Admission is regulated by a gate, which opens after showing a valid ticket to a bar code reader. There is a first row of gates controlling access to all rooms, then a gate controlling access to each room.

Other functions supported by the system are **refund of a ticket**; various **monitor** functions for the clerks (how many persons are in a room, how many seats available for a room/movie session, average occupation of a room per day/ per session); **definition of the schedule** for the day (what movie for what room at what time); **printout of the schedule** of the day.

- Define the context diagram (including relevant interfaces)
- Define the class diagram
- Define the use case diagram
- Define one scenario describing a successful sale for a ticket for a movie. 
- Define one scenario describing a successful admission to a room. 
- Define the system design diagram


## Context diagram and Interfaces

### Context diagram
```plantuml
left to right direction
skinparam packageStyle rectangle

:User: as u
:Credit Card System: as ccs

rectangle system {
	(Multiplex Cinema Management System) as mcms
}

u -- mcms
mcms -- ccs
```
![context diagram](pictures/context_diagram.png)

### Interfaces
| Actor              | Physical            | Logical 									|
|:------------------:|:-------------------:|:------------------------------------------:|
| User               | Screen and keyboard | GUI (web page accessible through Internet) |
| Credit Card System | Internet connection | Web service (APIs) 						|


## Glossary
```plantuml
class MultiplexCinema
class Room
class Movie
class Seat
class Ticket
class Show

MultiplexCinema : ID
MultiplexCinema : name
Room : ID
Room : seat capacity
Movie : ID
Movie : title
Seat : ID
Ticket : bar code
Ticket : used
Ticket : refundable
Show : start time
Show : end time

MultiplexCinema o-- "1..*" Room
Room o-- "1..*" Seat
Ticket "*" -- "1" Seat : books >
Ticket "*" -- "1" Show : is for >
Show "*" -- "1" Movie : projects >
Show "*" -- "1" Room : takes place >

Note top of Ticket : sold only in the same day of the show\nand if there is a seat available
```
![glossary](pictures/glossary.png)


## Use case diagram
```plantuml
left to right direction

:Clerk: as cl
:Customer: as cu
:Credit Card System: as ccs

together {
	(Sell ticket) as st
	(Choose seat) as cs
	(Handle payment) as hp
}
(Admit to room) as ar
(Refund ticket) as rt
(Monitor) as m
(Define schedule) as ds
(Print schedule) as ps

st <-- cl
cu --> st
st --> ccs
cu --> ar
cu --> rt
m <-- cl
ds <-- cl
ps <-- cl

st .> cs : include
st .> hp : include

note right of st : Clerk and customer uses\nthe same procedure (web site)
```
![use case diagram](pictures/use_case_diagram.png)