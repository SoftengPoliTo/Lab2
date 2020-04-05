# Official Requirements Document

Author: Alessandro Di Vincenzo

Date: 25/03/2020

# Contents
- [Abstract](#abstract)
- [Stakeholders](#stakeholders)
- [Context Diagram and interfaces](#context-diagram-and-interfaces)
	+ [Context Diagram](#context-diagram)
	+ [Interfaces](#interfaces) 
	
- [Stories and personas](#stories-and-personas)
- [Functional and non functional requirements](#functional-and-non-functional-requirements)
	+ [Functional Requirements](#functional-requirements)
	+ [Non functional requirements](#non-functional-requirements)
- [Use case diagram and use cases](#use-case-diagram-and-use-cases)
	+ [Use case diagram](#use-case-diagram)
	+ [Use cases](#use-cases)
	+ [Relevant scenarios](#relevant-scenarios)

# Abstract

Drivers need to know informations about gas stations. In particular, they want to know prices and precise position of gas stations in their neighboring area or in the middle of their road. They share these informations through EZGas, an application used to:

1 - collect prices of fuels in different gas stations

2 - locate gas stations in an area, along with the prices they practice.

# Stakeholders

| Stakeholder name  | Description | 
| ----------------- |:-----------:|
Gas station owner   | Has to verify the correctness of data inserted by the drivers regarding his GS|
Driver              | Can insert/get data and informations about gas station |

# Context Diagram and interfaces

## Context Diagram

```plantuml
left to right direction
actor Driver as d
actor GSOwner as gso
d -- (EZGas) 
gso -- (EZGas)
```

## Interfaces

| Actor | Logical Interface | Physical Interface  |
| ------------- |:-------------:| -----:|
|Gas station owner|GUI|Screen, buttons, keyboard|
|Driver|GUI|Screen, buttons, keyboard|

# Stories and personas

Tom is a bank worker who has been transferred in a office pretty far from his house. The bank has not provided Tom with a company car, so he must use his own vehicle. He would like to know what are the gas station in the middle of the road between his house and the bank and what are the ones with the lowest price. He also would like to communicate these informations to his colleagues and friends, in an efficient way. He discovers a new app, EZGas, where he can find gas stations located around his position and check their price.

Mark is the owner of a gas station located in a quite unknown road where there is little traffic every day. Affairs are not going well for Mark because few customers stop to his gas station, despite the fact that it has the lowest price of the entire province. He would like to find a way to make his station to be known to as many drivers as possible in a simple and zero-cost way. In order to do this, he use EZGas app. He can register his own gas station, keeping attenction to not insert wrong informations because they must be confirmed by drivers.

# Functional and non functional requirements

## Functional Requirements

| ID        | Description  |
| ------------- |:-------------:| 
| FR1           | Manage operations of registration, log in and log out |
| FR2           | Show to the driver two possible operations: search or confirm data |
| FR3           | Show to the driver the cheapest gas station |
| FR4           | Show to the driver the closest gas station |
| FR5           | Show to the driver the path to a gas station chosen by him |
| FR6           | Driver can confirm modifications from GS owner or not | 
| FR7           | Show to the GS owner two possible operations: modify or insert its own GS |
| FR8           | Record that GS owner has inserted new gas station or updated data about a gas station already existing | 

## Non Functional Requirements

| ID        | Type           | Description  | Refers to |
| ------------- |:-------------:| :-----:| -----:|
| NFR1          | Performance | All functions should be completed in less than 1 second  | All FR |
| NFR2          | Portability | The app must be available for every OS and browser | ALL FR |
| NFR3          | Functionality | Notify an error from driver to the GS owner that has inserted wrong data | FR6, FR8 |
| NFR4          | Usability | Every user can select a specific language | ALL FR |

# Use case diagram and use case

## Use case diagram
 
 ```plantuml
 left to right direction
 actor Driver as d
 actor GSOwner as o
 d -- (FR2 Selection of search or confirm operation)
 (FR2 Selection of search or confirm operation) => (FR5 Selection of a specific gas station)
 (FR2 Selection of search or confirm operation) => (FR6 List insertions of new data from the GS owner)
 o -- (FR7 Selection of modify or insert operation)
 (FR7 Selection of modify or insert operation) => (FR8 New data from GS owner)
```

## Use Cases

### Use case 1, UC1 - FR2 Selection of driver operation

| Actors Involved 		| Driver |
| ------------- |:-------------:| 
|  Precondition     | The driver logs in and have to choice between search or read GS owner insertions |
|  Post condition 	| Corresponding funcionality will be activated |
|  Nominal Scenario | The driver authenticates himself and can select one of the two options that appear |
|  Variants			| Error message if log in fails |

### Use case 2, UC2 - FR5 Selection of GS

| Actors Involved 		| Driver |
| ------------- |:-------------:| 
|  Precondition     | Driver has chosen to search a GS |
|  Post condition 	| Path to the GS selected appears |
|  Nominal Scenario | The driver can choice to search GS by price or by distance |
|  Variants			|  |

### Use case 3, UC3 - FR6 Confirm or ignore 

| Actors Involved 		| Driver |
| ------------- |:-------------:| 
|  Precondition     | Driver ha chosen to read GS owner insertions |
|  Post condition 	| If driver confirms, modification will be saved |
|  Nominal Scenario | A list of all the informations inserted by GS owner appears. The driver, after having read them, can confirm or ignore these insertions |
|  Variants			| Notification to GS owner in case of 'ignore' |

### Use case 4, UC4 - FR7 Selection of GS owner operation

| Actors Involved 		| GS owner |
| ------------- |:-------------:| 
|  Precondition     | The GS owner logs in and has to choice if he insert a new GS or modify an already existing one |
|  Post condition 	| New data inserted |
|  Nominal Scenario | The GS owner authenticates himself and two options appear |
|  Variants			| Error message if log in fails |

### Use case 5, UC5 - FR8 Insertion of new data

| Actors Involved 		| GS owner |
| ------------- |:-------------:| 
|  Precondition     | GS owner has chosen to insert new data |
|  Post condition 	| Data inserted but waiting to be confirmed by driver(s) |
|  Nominal Scenario | GS owner add a new GS or modify one of its own GS  |
|  Variants			|  |

# Relevant scenarios

| Scenario ID: SC1        | Corresponds to UC2  |
| ------------- |:-------------| 
| Description		| User select a GS |
| Precondition		| Log in success |
| Post condition	| Path to the chosen GS |
| Step#				| Step description |
| 1					| The driver can choise from a list of GS with low price or from a list of nearby GS |
| 2					| The driver selects the GS |
| 3					| Path to the corresponding GS appears |

| Scenario ID: SC2        | Corresponds to UC3  |
| ------------- |:-------------| 
| Description		| User confirm or ignore GS owner insertions |
| Precondition		| Log in success |
| Post condition	| New data available if confirmed |
| Step#				| Step description |
| 1					| The driver can read modifications of a specific GS or insertion of a new one |
| 2					| The driver must check if new data are correct |
| 3					| If correct, driver confirms them and data will be available |
| 4					| If incorrect, driver ignores them and notification will be sent to the corresponding GS owner |

| Scenario ID: SC3        | Corresponds to UC5  |
| ------------- |:-------------| 
| Description		| Insertion of new data from GS owner |
| Precondition		| Log in success |
| Post condition	| New data can be read by drivers to be confirmed |
| Step#				| Step description |
| 1					| The GS owner can choise to insert a new GS or modify one of his own GS |
| 2					| GS owner inserts new data |
| 3					| Data must be confirmed to be available to all users |
