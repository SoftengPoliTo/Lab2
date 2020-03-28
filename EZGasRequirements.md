# Official Requirements Document

Authors: Peraccini Simone

Date: 29/05/2019

Version: 5

#Change history


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
  Every car driver who travels a lot looks for the cheaper gas station where he can refuel his car. EZGAs maps all the gas stations  showing for each of them the current price.
  With this application the drivers can find the closer gas station that offers a convenient price whereas the gas station owner can keep the price updated and certify the updates of  the drivers.


# Stakeholders

  | STAKEHOLDER NAME  | DESCRIPTION                                                                                                                                          |
  |-------------------|------------------------------------------------------------------------------------------------------------------------------------------------------|
  | Driver            | Searchs for position and price of fuel of the station. Add a station to the map specifying position and price. Update the prices of the gas station. |
  | Gas Station owner | Updates and certifies the prices.                                                                                                                    |
  | Maps System       | System that provides a map where the gas stations are geolocalized                                                                                   |
  | Administrator     | System that mantains the application                                                                                                                 |

# Context Diagram and interfaces

## Context Diagram

@startuml

  actor Driver
  actor Gas_Station_Owner
  /'actor MapSystem'/
  /'actor Admin'/
  usecase EZGas
  Driver -right-> EZGas
  Gas_Station_Owner  -left-> EZGas
  MapSystem -up-> EZGas

@enduml

#Interfaces

  | Actor             | Logical Interface | PHYSICAL INTERFACE                               |
|-------------------|-------------------|----------------------------------------------------|
| Driver            | GUI               | Smartphone display, touch screen                   |
| Gas Station owner | GUI               | Smartphone display, touch screen, Screen, Keyboard |
| Map System        | API               | Network, GPS                                       |


#Stories and personas

Giovanni  is a lorry driver that travels all around Europe. During  his working days he is used to take some breaks in order to have a snack and also refuel his car.  Over the years, Giovanni thought to keep track of the changing of the prices for all the gas station he met, in order to remember them for the future times. Unfortunately, he experienced that in almost all the gas stations the price is rarely the same of the previous time.Speaking with his colleagues John has understood that many of them  adopted the same strategy and he  decided to create a whats app group (Lorry friends) where they could  communicate with each other any change of the prices.

However, Giovanni experienced that even this strategy was not good enough to keep the prices  updated and he decided to contact his friend John, who is a computer engineer. Together they decided develop an application able to collect and show these data.

Maurizio is a gas station owner. He noticed that his earnigs were not so satisfying so he decided to decrease the prices but even this strategy does not allow him to reach improvements.
Because of this he thought that his gas station may been a little far from the main streets of the city so he started to browse the web in order to find useful services.
Among all the application he found a free one that offers a good services both for drivers and gas stations owners: EZGas.

#Functional Requirements


| ID     | Description                                                                               |
|--------|-------------------------------------------------------------------------------------------|
| FR 1   | The driver searches gas stations                                                          |
| FR 1.1 | The driver filters gas stations by distance                                               |
| FR 1.2 | The driver filters gas station by price                                                   |
| FR 2   | The driver  registers to the service                                                      |
| FR 3   | The driver logs in                                                                        |
| FR 3.1 | The driver updates prices of gas station  only if he is registered and logged in          |
| FR 4   | The gas station owner can register to the service                                         |
| FR 5   | The gas station owner logs in                                                             |
| FR 5.1 | The gas station owner confirms the updated prices  only if he is registered and logged in |
| FR 5.2 | The gas station owner can update the prices only  if he is registered and logged in       |



#Non-Functional Requirements

| ID   | Type (efficiency, reliability, .. see iso 9126) | Description                                                             |         |
|------|-------------------------------------------------|-------------------------------------------------------------------------|---------|
| NFR1 | Usability                                       | User-friendly GUI                                                       | All FRs |
| NFR2 | Portability                                     | The application must be deployed on portable devices                    | All FRs |
| NFR3 | Reliability                                     | The application should not have failures when executing functionalities | All FRs |
| NFR4 | Functionality                                   | The application should provide consistent data                          | All FRs |
| NFR5 | Performance                                     | All functions must be completed in < 1 sec                              | All FRs |


##Use case diagram and use cases

#Use case diagram

@startuml

left to right direction
skinparam packageStyle rectangle

actor GasStationAdmin as g
actor Driver as d
actor MapSystem as m

rectangle Ezgas {
  ("Search gas Station") as uc1
  ("Filter by distance and price") as uc2
  ("EZGas registration") as uc3
  ("Update price") as uc4
  ("Certify price") as uc5
  ("EZGas Log in") as uc7

  m <-- uc1
  uc1 <.. uc2 :<<extend>>
  d -- uc1
  d -- uc3
  d -- uc4

  g -- uc4
  g -- uc5
  g -- uc3

  uc3 ..> uc7 :<<extend>>
  uc4 ..> uc7 :<<include>>
  uc5 ..> uc7 :<<include>>
}

@enduml


#Use cases

#UC1[ FR 1,FR 1.1, FR 1.2]: Search for a gas station


| Actors involved  | Driver                                                                                                       |
|------------------|--------------------------------------------------------------------------------------------------------------|
| Pre-condition    | Internet and Gps connections and Map System work                                                             |
| Post-conditions  | Get results                                                                                                  |
| Nominal Scenario | The driver opens the applications and looks the map in  order to find the closer or the cheaper gas station. |
| Variants         | The user filters the gas stations  in order to see only  the ones under a specific price or distance.        |


#UC2: FR 2: Driver registration

| Actors involved  | Driver                                                                                     |
|------------------|--------------------------------------------------------------------------------------------|
| Pre-condition    | Driver account does not exist.                                                             |
| Post-conditions  | Driver account exists.                                                                     |
| Nominal Scenario | Driver inserts Username, email and password. The system creates a new profile.             |
| Variants         | The Username has been already used or the password does not follow the security standards. |

#UC3.: FR 3.1: Driver updates price

| Actors involved  | Driver                                                                                   |
|------------------|------------------------------------------------------------------------------------------|
| Pre-condition    | Prices are outdated                                                                      |
| Post-conditions  | Prices are updated but marked as not certified                                           |
| Nominal Scenario | Driver notices that the prices related to a gas station are outdated so he updates them. |
| Variants         |                                                                                          |

#UC4.: FR 4: Gas station registration

| Actors involved  | Gas station owner.                                                                                    |
|------------------|-------------------------------------------------------------------------------------------------------|
| Pre-condition    | Gas station is not associated to any account.                                                         |
| Post-conditions  | Gas station owner is created.                                                                         |
| Nominal Scenario | A gas station owner inserts Username, Password and a certification. The system creates a new account. |
| Variants         | Who is trying to create the account is not certified.                                                 |

#UC5.: FR 5.1: The gas station owner certifies an updated price

| Actors involved  | Gas station owner                                             |
|------------------|---------------------------------------------------------------|
| Pre-condition    | Gas station prices are updated by a driver but not certified. |
| Post-conditions  | Gas station prices are certified.                             |
| Nominal Scenario | Gas station owner checks and confirms prices.                 |
| Variants         | Gas station owner checks and updates wrong prices.            |

#UC5.: FR 5.2: The gas station owner updates prices

| Actors involved  | Gas station owner.                                       |
|------------------|----------------------------------------------------------|
| Pre-condition    | Prices are outdate and gas station owner has an account. |
| Post-conditions  | Prices are updated.                                      |
| Nominal Scenario | Gas station owner checks and confirms prices.            |
| Variants         |                                                          |


##Relevant scenarios

#Scenatio 1: Driver updates price

| Scenario ID    | SC1                                                            |
|----------------|----------------------------------------------------------------|
| Description    | The driver notices an outdated price and decides to update it. |
| Pre-condition  | Price is outdated                                              |
| Post-condition | Price is updated                                               |
| Steps          | Step description                                               |
| 1.             | The driver selects the gas station.                            |
| 2.             | The driver selects the âUpdate Priceâ button.                  |
| 3.             | The driver inserts the new price.                              |
| 4.             | The driver submits the modification.                           |
| 5.             | The price is updated but not certified.                        |


#Scenatio 2: Gas station owner certifies update

| Scenario ID    | SC2                                        |
|----------------|--------------------------------------------|
| Description    | The gas station owner receives the update. |
| Pre-condition  | Price is updated but not certified.        |
| Post-condition | Price update is certified.                 |
| Steps          | Step description                           |
| 1.             | The gas station owner selects the request. |
| 2.             | The gas station owner confirms the prices. |
| 3.             | The prices are correctly updated           |

#Scenatio 3: Gas station owner refuses a price update

| Scenario ID    | SC3                                                       |
|----------------|-----------------------------------------------------------|
| Description    | The gas station owner receives a wrong update.            |
| Pre-condition  | Price is updated but wrong.                               |
| Post-condition | The price is updated by the owner with the correct value. |
| Steps          | Step description                                          |
| 1.             | The gas station owner selects the request.                |
| 2.             | The gas station owner changes the prices.                 |
| 3.             | The prices are correctly updated                          |
