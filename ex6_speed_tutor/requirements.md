# Speed Monitoring System on Highways

Traditional speed monitoring systems measure the instantaneous speed of a car on a street,
following the car for few meters with radar based appliances.

The idea of the Tutor system instead is to measure the average speed of a car on a long distance (in
the order of 1-10 kilometers). 

This is made by measuring the time when a car passes at point A, the time when the same car passes at point B, and doing simple math to compute the average speed. In point A and B
on the highway a gate is built with one or more cameras that take pictures of cars passing, triggered by a
motion sensor. 

The pictures, along with the time when they were shot, are sent to a computer based system
for processing. 

The output is the average speed of each car passed through the gates.

In the following you should model this system, including hardware (cameras, computers) and
software (notably functions provided). 

+ Define the stakeholders analysis
+ Define the context diagram (including relevant interfaces) 
+ Define the glossary with a class diagram.
+ Define the functional requirements
+ Define the non functional requirements 
+ Define the use case diagram 
+ Define one scenario describing a successful measurement of the speed of a vehicle. 
+ Define one scenario describing an unsuccessful measure. 
+ Define the system design

We are assuming that the speed report is sent to the police.

