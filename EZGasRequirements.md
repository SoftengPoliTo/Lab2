# Official Requirements Document

Authors: Maurizio Morisio, Luca Ardito, Riccardo Coppola

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


# Interfaces

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

#
