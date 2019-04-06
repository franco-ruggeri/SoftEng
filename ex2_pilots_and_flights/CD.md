```plantuml
class Airline
class Flight
class Airport
class Pilot
class "Aircraft Type"
class Aircraft
class Company

Pilot <|-- Captain
Pilot <|-- "Co-pilot"
Pilot <|-- Navigator

Airline : ID
Airline : name
Flight : ID
Flight : departure time
Flight : arrival time
Airport : ID
Airport : name
Pilot : ID
Pilot : name
Pilot : experience level
"Aircraft Type" : ID
"Aircraft Type" : name
"Aircraft Type" : under repair
"Aircraft Type" : landed
Aircraft : ID

Aircraft "*" -- "1" "Aircraft Type" : is a >
Airline "1" -- "*" Flight : operates >
Airport "1" -- "*" Flight : departs from <
Airport "1" -- "*" Flight : arrive to <
Flight "*" -- "1" Captain : capitan of <
Flight "*" -- "1" "Co-pilot" : co-pilot of <
Flight "*" -- "0..1" Navigator : navigator of <
Flight "*" -- "1" Aircraft : uses >
Airline "1" -- "*" Aircraft : owns >
Company "1" -- "*" Pilot : has >

note left of Aircraft #orange: if the aircraft is under repair it cannot fly
note right of Pilot #orange: experience level can be 1, 2 or 3
note bottom of Captain #orange: experience level is 3
```
