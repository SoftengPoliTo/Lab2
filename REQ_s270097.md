# Official Requirements Document

Authors: Carlo Borsarelli

Date: 25/03/2020


# Contents
- [Stakeholders](#stakeholders)
- [Context Diagram and interfaces](#context-diagram-and-interfaces)
	+ [Context Diagram](#context-diagram)
	+ [Interfaces](#interfaces) 
	
- [Official Requirements Document](#official-requirements-document)
- [Contents](#contents)
- [Stakeholders](#stakeholders)
- [Context Diagram and interfaces](#context-diagram-and-interfaces)
	- [Context Diagram](#context-diagram)
	- [Interfaces](#interfaces)
- [Stories and personas](#stories-and-personas)
- [Functional and non functional requirements](#functional-and-non-functional-requirements)
	- [Functional Requirements](#functional-requirements)
	- [Non Functional Requirements](#non-functional-requirements)
- [Use case diagram and use cases](#use-case-diagram-and-use-cases)
	- [Use case diagram](#use-case-diagram)
	- [Use Cases](#use-cases)
		- [Use case 1, UC1 - F 1  Record new gas-station](#use-case-1-uc1---f-1-record-new-gas-station)
		- [Use case 1.1, UC1.1 - F 1.1 Record the location of a gas station](#use-case-11-uc11---f-11-record-the-location-of-a-gas-station)
		- [Use case 1.2, UC1.2 - F 1.2 Record prices of each type of fuel for a gas station](#use-case-12-uc12---f-12-record-prices-of-each-type-of-fuel-for-a-gas-station)
		- [Use case 2, UC2 -  F 2 Produce a list of all gas station in a choosen area](#use-case-2-uc2---f-2-produce-a-list-of-all-gas-station-in-a-choosen-area)
		- [Use case 3,UC3 - F6 Manage closed gas stations](#use-case-3uc3---f6-manage-closed-gas-stations)
- [Relevant scenarios](#relevant-scenarios)
	- [Scenario 1](#scenario-1)
	- [Scenario 2](#scenario-2)


# Stakeholders

| Stakeholder name  | Description | 
| ----------------- |:-----------:|
| User     |Uses the application to locate gas stations and the prices in an area | 
| Admin    |Uses the application to add/remove gas station and manage errors | 
| GoogleMaps system    |Map system providing by Google that allows locating all gas station easily and it can be attached to the application to have a map. | 

# Context Diagram and interfaces

## Context Diagram

```plantuml
left to right direction
actor User as a
actor "GoogleMaps System" as b
a -- (EZGas)
(EZGas) -- Admin
(EZGas) -- b
```

## Interfaces
| Actor | Logical Interface | Physical Interface  |
| ------------- |:-------------:| :-----:|
|User|GUI |Touch Screen|
|Admin|Data interface / GUI |Screen, keyboard|
|GoogleMaps System| Web services |Internet connection|
# Stories and personas
Joseph is a boy and has no money. Joseph decides to fill the car. He must find the cheapest and closest gas-station, he has a car in reserve. Must find the gas station quickly.

Mark is a statistician. He has to develop a project for his course at the university, Mark decides to evaluate the number of gas-station in each geographic area to evaluate if there is some correlation with the geographical position and how the technological advantage of an area affect the gas station distribution. 

Mary is foreign and she doesn't know anything about the country where she is. She wants to fill up the car but she doesn't find gas-stations, She has to find a way to solve her problem just using an internet connection.

# Functional and non functional requirements

## Functional Requirements

| ID        | Description  |
| ------------- |:-------------:| 
|  F 1     | Record new gas station opened |  
|  -F 1.1     | Record the location of a gas station  |
|  -F 1.2     | Record prices of each type of fuel for a gas station |
|  F 2     | Produce a list of all gas station in a choosen area |
|  F 3     | Produce the indication of each fuel type from a chosen gas station |
|  F 4     | Manage types fuels |
|  F 5     | Manage areas of gas stations |
|  F 6     | Manage closed gas stations |
## Non Functional Requirements

| ID        | Type            | Description  | 
| ------------- |:----------:| :-----:| 
|  NFR1     | Usability | Application should be intuitive and easy to used for any types of user  | 
|  NFR2     | Performance | All functions should complete in < 0.5 sec  | 
|  NFR3     | Portability | The application runs on android / iOS (from android 5.0 / iOS 6)  | 
|  NFR4     | Maintainability | Administrator add/remove information from application. The time to do a change should be little ||


# Use case diagram and use cases

## Use case diagram

```plantuml
left to right direction
actor Admin as a 
actor "GoogleMaps System" as b
rectangle system{
a -> (F 1  Record new gas-station)
a --> (FR8 Manage closed gas stations)
(F 1  Record new gas-station) .|> (F 1.2 Record location of gas-station):<include>
(F 1  Record new gas-station) .|> (F 1.3 Record prices prices of each type of fuel ):<include>
(F 4 Visualize fuel types from a chosen gas-station ) .|> (F 5 Visualize gas-stations in an area):<include>
(F 5 Visualize gas-stations in an area)--> b
 (F 4 Visualize types of fuels prices).|> (F 5 Visualize gas-stations in an area):<include>
}
```
## Use Cases

### Use case 1, UC1 - F 1  Record new gas-station

| Actors Involved        | Administrator / User|
| ------------- |:-------------:| 
|  Precondition     | gas-stations G exists, users U exists |  
|  Post condition     | gas station inserted in the system properly |
|  Nominal Scenario     | Administrator want to insert in the app new gas-station. He acquires info about all fuel types and he uses GoogleMaps to identify on the map. He can acquire the information also from users|
|  Variants     |Admin acquires the information about new gas-station but google maps already don't have recorded it. Admin should inform google maps about their existence. |

### Use case 1.1, UC1.1 - F 1.1 Record the location of a gas station 

| Actors Involved        | Administrator / Google Maps|
| ------------- |:-------------:| 
|  Precondition     | Gas-station G, GoggleMaps has gas-station in DB |  
|  Post condition     | G inserted in the application properly |
|  Nominal Scenario     | The administrator looks for the gas-station on Google Maps and marks it. He uses the location to visualization from the user.|


### Use case 1.2, UC1.2 - F 1.2 Record prices of each type of fuel for a gas station

| Actors Involved        | Administrator |
| ------------- |:-------------:| 
|  Precondition     | Gas-station G , fuel type F, fuel price P  |  
|  Post condition     | G = [(F1,p1),(F2,p2),(F3,p3)...] |
|  Nominal Scenario     | The administrator takes information about gas-station fuel types and prices. And he inserts them in an indicator that appears when the user touches on the gas-station on the map. When an user touches on the gas-station on the maps should appear all the types of fuel with their price. Administrator implement this functionality by adding the function on Goggle Maps visualization |
|  Variants     |  |

### Use case 2, UC2 -  F 2 Produce a list of all gas station in a choosen area

| Actors Involved        | Administrator / Google Maps|
| ------------- |:-------------:| 
|  Precondition     | Gas station on GoogleMaps GG,location L|  
|  Post condition     | search L -> GG1,GG2,GG3,GG4 ... |
|  Nominal Scenario     | The administrator should personalize google Maps visualization by showing just gas stations, after the insertion of the location.|


### Use case 3,UC3 - F6 Manage closed gas stations 

| Actors Involved        | Administrator / User |
| ------------- |:-------------:| 
|  Precondition     |  |  
|  Post condition     |  |
|  Nominal Scenario     | If a gas-station is still present on GoogleMaps but is closed, a user can report the problem to the Administrator who should remove it. In general when GoogleMaps remove a gas-station from the map the system automatically removes also the additional information from the application.  |
|  Variants     | |


# Relevant scenarios

## Scenario 1

| Scenario ID: SC1        | Corresponds to UC1  |
| ------------- |:-------------| 
| Description | Record new gas-station |
| Precondition |  gas-stations G , users U,  |
| Postcondition |   gas station inserted in the system properly |
| Step#        |  Step description   |
|  1     | Administrator acquires informations of a new gas-station (from user, Google Maps or external DB) |  
|  2     |  Administrator searches on Google Maps |
|  3     | Add a properly marks of the gas-station on the Map |
| 4 | The administrator takes information about gas-station fuel types and prices. |
| 5 |  The administrator inserts them in an indicator that appears when the user touches on the gas-station on the map|
| 6 | User touches on the gas-station on the maps |
| 7 | It appear all the types of fuel with their price |

## Scenario 2

| Scenario ID: SC2        | Corresponds to UC3  |
| ------------- |:-------------| 
| Description | Manage closed gas stations  |
|Precondition |  Gas-Station G|
|Postcondition |  G removed|
| Step#        | Step description  |
|  1     | A User report gas-station closing ( gas-station is still present on GoogleMaps)  |  
|  2     | Administrator confirms the segnalation |
|  3     | If it is correct -> Administrator reports the closing to Google Maps and remove from   |
|  4     | Administrator reports the closing to Google Maps and removes from the application  |
