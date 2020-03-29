# Official Requirements Document

Authors: Mostafa Tavasoli Norouzi

Date: 29/05/2020

Version: 5

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

One of the main issues of the major cities and the big one, is finding the best and less crowded Gas Station. which people always try to find this kind of place to do their task as soon as posible. So, an online system is required in this way to service people to find the Gas station soon and find the location of it in its cell phone and other E-devices by using the GPS system easily. Additionally, it is necessary to collect the fuel price in the different gas locations to make the right decision.


# Stakeholders

| Stakeholder name  | Description | 
| ----------------- |:-----------:|
| Owner     		|Manages the system such as improve it, update it interms of hardware and sofrware | 
| Customers       	|Use the system directly with their cell phones or other electronic devices| 
| The GPS System    |Use by the customers to find the location of GAS stations| 
| Shareholders      |The system need them, so it can develop and impelment| 

# Context Diagram and interfaces

## Context Diagram

<img src="https://www.mediafire.com/convkey/d3cf/auarew5bdgsc7r46g.jpg" />

## Interfaces
| Actor | Logical Interface | Physical Interface  |
| ------------- |:-------------:| -----:|
|Administrator|GUI |Screen, keyboard|


# Stories and personas
John works in the office and has an inclination for order and discipline. So he volunteers to keep track of what happens on the coffee machine. When a capsule of a certain type is close to sold out John reorders. Capsules can be purchased only in multiples of a minimum quantity (ex 40). On the money side, John computes how much each colleague should pay for what she has consumed. In practice every colleague has a virtual account, initially charged with a reasonable amount of cash given to John (ex 10 euros). John maintains this account and asks to recharge it when close to zero. Physically the money for capsules is in cash, and John manages it as if it where his personal money.

All colleagues trust each other, so negative accounts are allowed. John uses his personal money if needed to reorder capsules. 

John is happy to do this work, but would like to hand over to someone else after a certain amount of time. In any case when he is on vacation another colleague takes over temporarily.

John would like to have a simple way to report (ex every one or two weeks) to each colleague all expenses and consumption for LaTazza. Without this report nobody has a clear idea of how much was the consumption.

Mary works in the office and likes to share time with her colleagues in front of the coffee machine. On the side of the coffee machine is a tray with capsules. When she wants a coffee (or else) she takes a capsule from the tray and tells to John. To do so she uses a whatsapp group (LaTazza friends).

Mr. Guest is a visitor in the office. As such he does not have the privilege of having an account. In case he can directly pay the capsule, cash, to John.

# Functional and non functional requirements

## Functional Requirements

| ID        | Description  |
| ------------- |:-------------:| 
|  FR1     | Record that a colleague has used n capsules of a certain type, update his account |  
|  FR2     | Record that a visitor has used n capsules of a certain type |
|  FR3     | Record that a colleague has recharged x euros on her account |
|  FR4     | Record that n capsules of a certain type have been received, and paid for |
|  FR5     | Produce a report about consumption and recharges of a colleague over a certain period of time |
|  FR6     | Produce a report about all consumption and recharges over a certain period of time |
|  FR7     | Manage types of capsules and prices |
|  FR8     | Manage colleagues and accounts |

## Non Functional Requirements

| ID        | Type (efficiency, reliability, .. see iso 9126)           | Description  | Refers to |
| ------------- |:-------------:| :-----:| -----:|
|  NFR1     | Usability | Application should be used with no training by any colleague in the office  | All FR |
|  NFR2     | Performance | All functions should complete in < 0.5 sec  | All FR |
|  NFR3     | Portability | The application runs on MS Windows (7 and more recent)  | All FR |
|  NFR4     | Portability | The application (functions and data) should be portable from a PC to another PC in less than 5 minutes | All FR |
|  NFR5     | Localisation | Decimal numbers use . (dot) as decimal separator ||


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

