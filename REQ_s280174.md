# Stakeholders

| Stakeholder name  | Description | 
| ----------------- |:-----------:|
| User              | He's the end user |
| Gas retailer     | The organization which provides petrol to drivers through its own petrol stations; data about prices and week schedule |
| Developer or Developer company | It's us |
| Buyer | City's administration |
| Map system | Google Maps: to keep trace on a map about petrol station, allow a user-friendly selection of them and computing the best path to reach the petrol station |
| Petrol stations DB administrator | Who takes care about updating the DB |
| GPS system | Provided by the mobile itself, it's exploited only to know the center of the circle |
| Applications space | App Store |
| Petrol stations DB | Contains a table with schema (Petrol station ID, Coordinates, Type of fuel, price) whose updating is performed through an agreement with Gas retailer |

# Glossary
| Identificator | Definition |
| ------------- |:----------:|
| Previous price | Given a moment in which User visualizes a given petrol station, it's the price of all types of fuels of the petrol station of the previous day |
| Current session | Time and state of the application between its opening and closure |
| City | The city where the system is adopted, such as Rome |

# Context diagram


## Interfaces
| Actor | Logical Interface | Physical Interface  |
| ------------- |:-------------:| -----:|
| User | GUI of mobile | Screen, keyboard |
| Map system | APIs | Servers |
| GPS system | APIs | Electronics and physics |
| Application space | Standard protocol decided by the application space | Servers |
| Petrol stations DB | Queries and DB protocols | Mobile |

# Stories and personas
## Stories
### Story 1
John is a blue collar worker; he gets up early and have diverse things to do, such as fueling his car, hoping the price is the same as the day before and at a low price and with not much queue; his car is hybrid, so he can choose the more advantagious type of fuel. John has no much time, if we think that he must bring his children to school; he thinks that maybe he will do the refuel after he brought his children. When John exits the work, he cast a glance to see the price of fuel of his favourite petrol station, for the next day, and tries to memorize it.

### Story 2
Alex is a high school student and he usually goes travelling around the city by motorbike, with his friends. He is annoyed to fuel his vehicle immediately, given that the indicator is just beyond the red part. During his trip, a red led turns on, given that fuel is going to finish. He hopes to encounter a petrol station somewhere, or reach the stations he already knows but not near to its path. Unfortunately, after a few minutes, he must leave his friends at least for 10 minutes, to fuel his motorbike in the nearest petrol station.

### Story 3
Marianne is going to train on tennis field with her friend and, before she exits home, she wishes to know whether the usual petrol station is open and both the current price and the Previous price. Marianne doesn't remember well the path toward the petrol station, so she uses Google Maps directly, hoping that the week schedule is correct.

### Story 4
Frederick is going to visit the historical centre of City directly from work; he has no idea about how much time it will take, but he has all the weekend. Therefore, he enters the car and realize that the gas tank is nearly empty. He searches for a petrol station on the Net to know which is open and possibly cheap. The nearest petrol station is 8 km distant, so he has to go there, resigned. He hopes there won't be much queue, given that most people are going home from work.

### Story 5
Alistair is a blue collar and he struggles with fuel management every week. He has some favourite petrol stations at this point, given that he has been living in an apartment with his family for over 20 years; therefore, he already knows where they are located and reachable, but he doesn't know which are the variations for today, so he decides to watch the news broadcast for a general trend on fuel prices, although this don't help him in choosing the best petrol station for today.


## Personas
### Persona 1
female, commuter, live in suburbs, young, in touch with IT, not married.
Working day: gets up early, drives to work, exits the work, fuels car where queue is small given that a plenty of commuters are going home, checks price of fuel and compare it with those of previous days according to personal memory range; go back home.
Non-working day: gets up, wants to do shopping, thinking about which supermarkets have discounts or a particular product seen last time, hopes the car has enough fuel, not really, fuel the car somewhere known, do shopping, go back home.
### Persona 2
male, blue collar, live in city, middle aged, beginner with IT, married.
Weekend day: decide whether to travel somewhere, go to the habitual petrol station, do the visit
### Persona 3
male, blue collar, live in city, middle aged, not really interested in IT but thought essential nowadays, married.
Weekend day: has a desire to go to the stadium for an important match at the opposite corner of the city, gets annoyed about fuel consumption, checks an acceptable. petrol station according to his knowledge along the chosen path, goes for supporting his team, go back home and check again the fuel reserve.
### Persona 4
male, student, live in city, 16 years old, expertise on IT, not married.
School day: gets up quite early, start travelling towards school, encounters a petrol station, decide whether to do refueling according to reserve and money availability; go to school
### Persona 5
Persona 5: male, worker, live in city, middle aged, middle-skilled on IT, married.


# Relevant scenarios

## Scenario 1

| Scenario ID: SC1        | Corresponds to UC1  |
| ------------- |:-------------| 
| Description | User is going to move from an abitual position |
| Type | Normal |
| Precondition |   |
| Postcondition | Service delivered  |
| Step#        |  Step description   |
|  1     | User opens the application |  
|  2     | Picks the usual petrol station from the tab "favourites" |
|  3     | Checks if it is open |
|  4     | Checks quickly the price of GPL and the Previous price |
|  5     | Close the application |

| Scenario ID: SC2        | Corresponds to UC1  |
| ------------- |:-------------| 
| Description | Update necessary |
| Type | Exceptional |
| Precondition |   |
| Postcondition |   Service not delivered, check will be done on next day |
| Step#        |  Step description   |
|  1     | User opens the application |  
|  2     | A compulsory update is available for the application  |
|  3     | Install the update |
| 4      | Forget to see prices / Boredom to wait until the update completes |

| Scenario ID: SC3        | Corresponds to UC3  |
| ------------- |:-------------| 
| Description | User interested in the fuel market |
| Type | Normal |
| Precondition |  Be in spare time |
| Postcondition |  Have a deeper knowledge of fuel prices' trend in the city, for instance to know which type of fuel is convenient for the car he's going to buy |
| Step#        |  Step description   |
|  1     | User opens the application |  
|  2     | Select the subset of petrol stations in the area of a friend's house |
|  3     | Compare the petrol stations by caring about fluctuations and the absolute price in the last month |
| 4      | Close the application |

| Scenario ID: SC4        | Corresponds to UC1  |
| ------------- |:-------------| 
| Description | User is going to move from an unknown position |
| Type | Normal |
| Precondition |   |
| Postcondition |  Service delivered |
| Step#        |  Step description   |
|  1     | User opens the application |  
|  2     | Sets the radius of the circle to 3 km centered in current position, according to the fuel reserve |
|  3     | Select the petrol station which best fits closeness  |
|  4     | Drive to the petrol station |
| 5      | Close the application |

| Scenario ID: SC5        | Corresponds to UC2  |
| ------------- |:-------------| 
| Description | User adds a petrol station to favourites |
| Type | Normal |
| Precondition |   |
| Postcondition |  Service delivered |
| Step#        |  Step description   |
|  1     | User opens the application |  
|  2     | Search for the petrol station just used |
|  3     | Add it to the favourites  |
| 4      | Close the application |

- The DB keeps trace about price in the last month (30 days * 3 types of fuel * number_of_fuel_stations_in_city)
- The application could show the variation of price in the tab of favourites to the side of the actual absolute price, just about the previous day;
- The application should provide a GUI to compare trends in the last month
- Every update to the app is compulsory before its usage;
- The application may send a notification to the user autonomously thanks to the application space;
- Which type of entrance for the buyer? Asset, advertising, freeware, shareware?

# Use case diagram and use cases

## Use case diagram

## Use Cases

### Use case 1, UC1 - Moving

| Actors Involved        | User, Map system, Petrol stations DB, GPS |
| ------------- |:-------------:| 
|  Precondition     | No update from SC2 is necessary  |  
|  Post condition     |  Service delivered | 
|  Nominal Scenario     | User opens the app, select a petrol station, switches to Google Maps and opens the GPS, drives, refuel|
|  Variants     | Doesn't switch to Google Maps, just selection and comparison |

### Use case 2, UC2 - Managing favourites

| Actors Involved        | User, Map system, Petrol stations DB, GPS (optional) |
| ------------- |:-------------:| 
|  Precondition     | No update from SC2 is necessary  |  
|  Post condition     |  Service delivered | 
|  Nominal Scenario     | User opens the application, search for a petrol station, add it to the favourites, close the application |
|  Variants     | User cancels a petrol station from favourites |

### Use case 3, UC3 - Inspecting

| Actors Involved        | User, Map system, Petrol stations DB, GPS (optional) |
| ------------- |:-------------:| 
|  Precondition     | No update from SC2 is necessary  |  
|  Post condition     |  Service delivered | 
|  Nominal Scenario     | User opens the application, selects a subset of petrol stations, compare prices during the last month, close the application |
|  Variants     |  |


# Functional and non functional requirements

## Functional Requirements

| ID        | Description  |
| ------------- |:-------------:| 
|  FR1     | Select a petrol station in favourites from FR7, eventually switch to Map system from FR4 |  
|  FR2     | Show petrol stations across an area, request for a radius, query the DB for them from FR5, show result on the map, switch to Map system from FR4 |
|  FR3     | Select the favourites tab, query the DB for the favourites and petrol stations from FR5 only if it wasn't done in Current session, show both actual and Previous price |
|  FR4     | Switch to Map system |
|  FR5     | Update a given content by querying the DB |
|  FR6     | Redirect to applications space for updates |
|  FR7     | Manage favourites: add, remove, select, show |
|  FR8     | Do from FR2, compare prices |

## Non Functional Requirements

| ID        | Type (efficiency, reliability, .. see iso 9126)           | Description  | Refers to |
| ------------- |:-------------:| :-----:| -----:|
|  NFR1     | Performance | DB querying and report rendering completes in < 0.3 s  | All FR |
|  NFR2     | Performance | Application opens in < 1.0 s  | |
|  NFR3     | Portability | Application runs on iOS and Android  | |
|  NFR4     | Space | The application stores no prices and opening time, just the favourites list | FR3, FR2 |
|  NFR5     | Localisation | Currency is that one of City | |
|  NFR6     | Ethical | The absolute error between the real price and the price visualized has to be null | |
|  NFR7     | Usability | Open petrol stations have to be visualized, only | FR2 |
|  NFR8     | Usability | The application visualizes if petrol stations are open and send a warn if a closed petrol station is selected | FR1, FR3, FR7, FR8 |