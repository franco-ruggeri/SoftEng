# Internship

In order to perform the internship, each student has to select a proposal from a list. Each proposal is acknowledged by a company agreement with the university.

The Stage & Job office receives the request, verifies the formal correctness (e.g. by checking if the student has enough credits for applying the internship) and then it activates the internship
At this point the student must find an academic tutor (a professor) who wants to follow the training program, and then the student enters his/her name in the request. The academic tutor must countersign the request as well as the company tutor (already defined by the company in the proposal).

Once the Stage & Job office accepts the proposal the company (in accordance with the student)
defines for the internship a start date, and an end date

The student begins the internship at the specified date.
At the end of the internship, the student must deliver to the office Stage & Job the attendance sheet In addition, both the company tutor and the student must complete a specific evaluation questionnaire.

The professor must then assign a mark for the internship.

At this point the internship is recorded in the student's academic career.

- Provide the UML Use Case Diagram for the case study described above
- Identify the three main use cases, and for each use case describe the related scenarios


## Use Case Diagram
```plantuml
left to right direction

:Student: as s
:Stage&Job office: as sjo
:Company: as c
:Company Tutor: as ct
:Academic tutor: as at

(Load proposal) as lp
(Apply for internship) as ai
(Check formal correctness) as cfc
(Check credits) as cc
(Accept proposal) as ap
(Rate internship) as ri
(Put mark) as pm

c --> lp
s --> ai
sjo --> cfc
sjo --> ap
s --> ri
ct --> ri
at --> pm

cfc .> cc : include
```
![use case diagram](pictures/use_case_diagram.png)

## Scenarios


