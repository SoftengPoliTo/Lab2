# Official Requirements Document

Authors: Maurizio Morisio, Luca Ardito, Riccardo Coppola

Date: 29/05/2019

Version: 5

Change history

| Version | Changes | 
| ----------------- |:-----------|
| 2 | Fixed defect in [scenario 2](#scenario-2): precondition was wrong  |
| | Fixed defect in scenario [format](#relevant-scenarios): added post conditions |
| | Fixed defect in [use case 2](#use-cases): variants text canceled |
| 3 | Fixed defect in [use case 3]: recharge only positive|
| |  Added Non functional requirement NFR5 |
| 4 | Fixed defect in [use case 3]: post condition is on Colleague account, and LaTazza|
| | Fixed defect in [use case 1]: post condition is on Colleague account, not LaTazza|
| 5 | Fized defect in [use case 4]: precondition modified |

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
- [Glossary](#glossary)
- [System design](#system-design)
- [Deployment diagram](#deployment-diagram)

# Abstract

Some colleagues share a coffee machine in a common space for breaks. Capsules are left aside the machine. Whoever uses a capsule writes this down in a notebook left aside the coffee machine. One of the colleagues (called *administrator*) copies consumptions in an excel sheet and collects money from colleagues to (re)order capsules.

One of the colleagues, the *hacker*, volunteers to develop a simple application to support the administrator. To keep things simple the application is standalone, and is meant to be used only by the administrator. Possibly the administrator role is taken by different colleagues over time. Instead of the notebook, the hacker sets up a WhatsApp group. Whenever a colleague uses a capsule, he sends a message to the group.


# Stakeholders

| Stakeholder name  | Description | 
| ----------------- |:-----------:|
| Administrator     |Uses the application to manage the business.| 
| Users             |They uses the appplication directly. They are interested in  collecting the prices of fuels in different workstation. |
| Developer         |Develops the web application| 

# Context Diagram and interfaces

## Context Diagram

```plantuml
left to right direction
actor Administrator as a
a -- (La Tazza)
```

## Interfaces
| Actor | Logical Interface | Physical Interface  |
| ------------- |:-------------:| -----:|
|User |Web Service |PC,Phone,Internet|


# Stories and personas
The CEO develops a web application through which the users can check the prices of the fuels in different work station.
Mr.Harry got a transport company. The Sundays of every weekend he was to put fuel to his 3 trucks so that they can start working from Monday again. 

He opens the web application from his smartphones.He checks the prices of fuels of different gas station. He decides to use Q8 as finds out that the price of Q8 is less then others for example repsol. He informs his workers and share the location of the gas station in whatsapp and ask him to go there and fill the fuel to the trunk. 

Sometimes it even happens that while the worker are on their work the gas finishes the workers can quickly login in the platform of EZgas and compare the prices of the gases in different fuels and decide the one they prefer. The google Map will easily help to locate the nearest fuel station.


# Functional and non functional requirements

## Functional Requirements

| ID        | Description  |
| ------------- |:-------------:| 
|  FR1     | Record the change of price of fuel each day |  
|  FR2     | Record the number of user visiting the fuel station |
|  FR3     | Record the new fuel stations built |
|  FR4     | Manage the types of gas and fuel |
|  FR5     | Produce a report about daily sale|
|  FR6     | Produce a report about daily traffic |
|  FR7     | Manage users and accounts|


## Non Functional Requirements

| ID        | Type (efficiency, reliability, .. see iso 9126)           | Description  | Refers to |
| ------------- |:-------------:| :-----:| -----:|
|  NFR1     | Usability | Application should be used with no training by any users in the office  | All FR |
|  NFR2     | Performance | All functions should complete in < 1 sec  | All FR |
|  NFR3     | Portability | The application runs on MS Windows (7 and more recent) and andriod smartphones  | All FR |
|  NFR4     | Efficieny   | The application should always show the uptodate prices.|


# Use case diagram and use cases

## Use case diagram

```plantuml
left to right direction
actor Administrator as a
a -- (FR1  Record usage of capsules by colleague)
a -- (FR2 Record usage of capsules by visitor)
a -- (FR3 Record recharge of account of colleague)
a -- (FR4 Record purchase of capsules)
a -- (FR5 Produce report on consumption of colleague)
a -- (FR6 Produce report on all consumptions)
```
## Use Cases

### Use case 1, UC1 - FR1  Record usage of capsules by colleague

| Actors Involved        | Administrator |
| ------------- |:-------------:| 
|  Precondition     | Capsule T exists, colleague C exists |  
|  Post condition     | T.quantity_post < T.quantity_pre |
| | C.PersonalAccount.balance_post < C.PersonalAccount.balance_pre |
|  Nominal Scenario     | Administrator selects capsule type T, selects colleague C, Deduce quantity for capsule T, deduce price of T by account of colleague C|
|  Variants     | Account of colleague C has not enough money, issue warning |

### Use case 2, UC2 - FR2 Record usage of capsules by visitor

| Actors Involved        | Administrator |
| ------------- |:-------------:| 
|  Precondition     | Capsule T exists, visitor has no account |  
|  Post condition     | T.quantity_post < T.quantity_pre |
| | LaTazzaAccount.amount_post > LaTazzaAccount.amount_pre |
|  Nominal Scenario     | Administrator selects capsule type T, Deduce quantity for capsule T, add price of T on LaTazzaAccount.amount|
|  Variants     |  |

### Use case 3, UC3 - FR3 Record recharge of account of colleague

| Actors Involved        | Administrator |
| ------------- |:-------------:| 
|  Precondition     | Personal Account PA exists , quantity >0 |  
|  Post condition     | PA.balance_post = PA.balance_pre + quantity |
|  | LaTazzaAccount.balance_post = LaTazzaAccount.balance_pre + quantity  |
|  Nominal Scenario     | Administrator selects account PA of colleague C, increase account of  quantity, increase LaTazza account of quantity|
|  Variants     |  |

### Use case 4, UC4 - FR4 Record purchase of capsules

| Actors Involved        | Administrator |
| ------------- |:-------------:| 
|  Precondition     | Capsule type CT exists,  LaTazzaAccount.balance has enough money for the purchase|  
|  Post condition     | CT.quantity_post > CT.quantity _pre |
| | LaTazzaAccount.balance_post < LaTazzaAccount.balance_pre|
|  Nominal Scenario     | At time of order Administrator records money spent for order. At time of reception administrator selects capsule type CT, increases its quantity by a given number|
|  Variants     |  |

### Use case 5, FR5 Produce report on consumption of colleague

| Actors Involved        | Administrator  |
| ------------- |:-------------:| 
|  Precondition     | Colleague C exists |  
|  Post condition     |  |
|  Nominal Scenario     | Administrator selects colleague C, defines a time range,  application collects all transactions for C (recharges and capsules taken) in the time range and presents them|
|  Variants     | |

### Use case 6, FR6 Produce report on all consumptions

| Actors Involved        | Administrator |
| ------------- |:-------------:| 
|  Precondition     |  |  
|  Post condition     |  |
|  Nominal Scenario     | Administrator defines a time range,  application collects all transactions (recharges, purchases, and capsules taken) in the time range and presents them |
|  Variants     | |


# Relevant scenarios

## Scenario 1

| Scenario ID: SC1        | Corresponds to UC1  |
| ------------- |:-------------| 
| Description | Colleague uses one capsule of type T|
| Precondition |  account of C has enough money to buy capsule T|
| Postcondition |  account of C updated, count of T updated |
| Step#        |  Step description   |
|  1     | Administrator selects capsule type T |  
|  2     |  Administrator selects colleague C |
|  3     | Deduce one for quantity of capsule T |
| 4 | Deduce price of T from account of C|

## Scenario 2

| Scenario ID: SC2        | Corresponds to UC1  |
| ------------- |:-------------| 
| Description | Colleague uses one capsule of type T, account negative|
|Precondition |  account of C has not enough money to buy capsule T|
|Postcondition |  account of C updated, count of T updated |
| Step#        | Step description  |
|  1     | Administrator selects capsule type T |  
|  2     | Administrator selects colleague C |
|  3     | Deduce one for quantity of capsule T  |
|  4     | Deduce price of T from account of C  |
|  5     | Account of C is negative, issue warning  |


# Glossary

```plantuml
class LaTazza
class Colleague {
+ name
+ surname
}

class PersonalAccount {
+ balance
}

class CapsuleType {
+ name
+ price
+ quantity
}

class LaTazzaAccount {
+ balance
}

class BoxPurchase {
+ quantity
}

class Transaction {
+ date
+ amount
}

class Recharge
class Consumption


LaTazza -- "*" Colleague
LaTazza -- "*" CapsuleType
LaTazza -- LaTazzaAccount

LaTazzaAccount -- "*" BoxPurchase
LaTazzaAccount -- "*" Consumption

CapsuleType -- "*" Consumption
CapsuleType -- "*" BoxPurchase

Colleague -- PersonalAccount
PersonalAccount -- "*" Transaction

Transaction <|-- Recharge
Transaction <|-- Consumption
Transaction <|-- BoxPurchase

```

# System Design
Not really meaningful in this case. Only one personal computer is needed.

```plantuml
class "Personal Computer"
```

# Deployment Diagram
As a stand-alone application only one node is needed.

```plantuml
artifact "La Tazza Application" as a
node "Personal Computer" as n
a -- n
```

