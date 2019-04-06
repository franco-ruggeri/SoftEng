```plantuml
together {
  class University
  class Classroom
  class Department
  class Office
}

together {
  class Person
  class Professor
  class "Full professor"
  class "Associate professor"
  class "Assistant professor"
}

University o-- "1..*" Classroom
University o-- "1..*" Department
University o-- "1..*" Office
Department o-- "1..*" Office
Department : name

Person "1..*" - "1" University : works in >
Person : ID
Person <|-- Professor
Person <|-- Employee

Professor <|-- "Full professor"
Professor <|-- "Associate professor"
Professor <|-- "Assistant professor"
Department "1" - "*" Professor : is enrolled <

Office : ID
Classroom : ID
Classroom : "number of seats"

Office "1" - "*" Employee : works in <
```
