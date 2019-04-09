# Internship


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
### Internship proposal
Precondition: the company is registered in the university information system  
Post condition: the proposal is in the list

| Scenario ID: SC1 | Corresponds to UC: Load proposal |
|:----------------:| -------------------------------- |
| Step #           | Description  					  |
| 1                | Company selects 'add new proposal' |
| 2                | System shows forms for describing proposal |
| 3                | Company adds proposal details in the form and confirms |
| 4                | System adds the proposal to the list |

### Internship selection
Precondition: the student is enrolled in the university and he is logged in  
Post condition: the request is sent to the stage&job office

| Scenario ID: SC2 | Corresponds to UC: apply for internship |
|:----------------:| -------------------------------- |
| Step #           | Description  					  |
| 1                | Student selects 'show proposals' |
| 2                | System shows the list of proposals |
| 3                | Student selects the proposal |
| 4                | System shows details of the proposal |
| 5                | Student inserts the professor's name and clicks 'apply' |
| 6                | System stores the request and sends it to the Stage&Job office |

### Internship evaluation
Precondition: the professor is the tutor of the internship  
Post condition: the grade is registered in the student's career

| Scenario ID: SC3 | Corresponds to UC: Put mark |
|:----------------:| -------------------------------- |
| Step #           | Description  					  |
| 1                | Academic tutor selects the internship |
| 2                | System shows the form for evaluating |
| 3                | Academic tutor compiles the form (mark, etc.) and clicks 'confirm' |
| 4                | System stores the grade in the student's career |
