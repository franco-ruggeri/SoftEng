# Multiplex cinema management.


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
Seat : occupied
Ticket : bar code
Ticket : used
Ticket : refundable
Show : start time
Show : end time
Show : number of available seats

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


## Scenarios
### Successful sale for a ticket for a movie

Precondition: there is at least one seat available for the show and it is the same day of the show  
Post condition: the selected seat is occupied

| Scenario ID: SC1 | Corresponds to UC: Sell ticket |
|:----------------:| ------------------------------ |
| Step # | Description |
| 1 | User selects show |
| 2 | User selects seat |
| 3 | User pays |
| 4 | System sets the seat as occupied, decreases the total number of seats available |

### Successful admission to a room

Precondition: customer has a valid ticket and has already passed the first row of gates  
Post condition: the ticket is used

| Scenario ID: SC2 | Corresponds to UC: Admit to room |
|:----------------:| -------------------------------- |
| Step # | Description |
| 1 | Customer shows ticket to the barcode reader |
| 2 | System checks if the ticket is valid for show |
| 3 | Room gate opens and customer enters |
| 4 | System sets the ticket as used |


## System design
```plantuml
class "Multiplex Cinema Management System"
class Server
class Printer
class Gate
class "Barcode Reader"

Server : +sellTicket()
Server : +refundTicket()
Server : +admitToRoom()
Server : +defineSchedule()
Server : +printSchedule()
Gate : +readTicket()
Gate : +open()
"Barcode Reader" : +readTicket()

"Multiplex Cinema Management System" o-- "1" Server
"Multiplex Cinema Management System" o-- "1..*" Gate
Gate o-- "1" "Barcode Reader"
Server -- Printer
```
![](pictures/system_design.png)
