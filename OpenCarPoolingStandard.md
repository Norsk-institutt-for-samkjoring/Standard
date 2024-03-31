# Open CarPool Standard

**General information**
Version: 0.5

  Work in progress, feel free to add


This document contains specifications for carpooling.

  


## Table of Contents
* [User](#user)
* [Driver](#driver)
* [Car](#car)
* [Passenger](#passenger)
* [Ride](#ride)
* [Waypoint](#waypoint)
* [Destination](#destination)
* [Payment](#payment)
* [Language](#language)
* [Groups and Companies](#groups-and-companies)
* [API](#api)

### User
Information about the users

| Field             | Type     | Description                                                    |
|-------------------|----------|----------------------------------------------------------------|
| `userId`          | `string` | Unique identifier for the user                                |
| `name`            | `string` | Name of the user                                              |
| `phone`           | `string` | Phone number(s) of the user                                   |
| `email`           | `string` | Email address of the user                                     |
| `pictureUrl`      | `string` | URL to the user's profile picture                             |
| `language`        | `string` | User's preferred language                                     |
| `paymentOptions`  | `array`  | User's preferred payment options (e.g., credit card, PayPal)  |
| `groups`          | `array`  | List of groups the user belongs to                            |
| `companies`       | `array`  | List of companies the user is associated with                 |

[top](#table-of-contents)

### Driver
Information about the driver or owner

| Field             | Type      | Description                                                    |
|-------------------|-----------|----------------------------------------------------------------|
| `driverId`        | `string`  | Unique identifier for the driver                              |
| `userId`          | `string`  | Unique identifier of the user associated with the driver      |
| `name`            | `string`  | Name of the driver                                            |
| `email`           | `string`  | Email address of the driver                                   |
| `phone`           | `string`  | Phone number(s) of the driver                                 |
| `carId`           | `string`  | Unique identifier of the driver's car                         |
| `pictureUrl`      | `string`  | URL to the driver's profile picture                           |
| `licenseVerified` | `boolean` | Indicates if the driver's license has been verified           |

[top](#table-of-contents)

### Car

| Field               | Type      | Description                                                    |
|---------------------|-----------|----------------------------------------------------------------|
| `carId`             | `string`  | Unique identifier for the car                                 |
| `color`             | `string`  | Color of the car                                              |
| `type`              | `string`  | Type of the car (e.g., sedan, SUV, electric, hybrid)          |
| `engine`            | `string`  | Type of propulsion (e.g., gasoline, electric, hybrid)         |
| `insurance`         | `object`  | Insurance information for the car                             |
| `capacity`          | `number`  | Total capacity of the car, including the driver               |
| `reservedCapacity`  | `number`  | Number of seats reserved for the driver (should be 1 for non-autonomous cars) |
| `plateId`           | `string`  | License plate number or other means of verification           |
| `amenities`         | `array`   | List of amenities available in the car (e.g., air conditioning, Wi-Fi, child seat) |

[top](#table-of-contents)

### Passenger
Could be multiple passengers

| Field             | Type     | Description                                                    |
|-------------------|----------|----------------------------------------------------------------|
| `passengerId`     | `string` | Unique identifier for the passengers, could be multiple       |
| `userId`          | `string` | Unique identifier of the user associated with the passengers  |
| `name`            | `string` | Name of the passenger                                         |
| `email`           | `string` | Email address of the passenger                                |
| `phone`           | `string` | Phone number(s) of the passenger with international prefix    |
| `pictureUrl`      | `string` | URL to the passenger's profile picture (needs protection or public image) |
| `luggage`         | `object` | Information about the passenger's luggage (e.g., number of bags, size) |

[top](#table-of-contents)


### Ride

| Field             | Type     | Description                                                    |
|-------------------|----------|----------------------------------------------------------------|
| `rideId`          | `string` | Unique identifier for the ride                                |
| `driverId`        | `string` | Unique identifier of the driver                               |
| `carId`           | `string` | Unique identifier of the car                                  |
| `passengers`      | `array`  | List of passenger IDs                                         |
| `state`           | `string` | Current state of the ride (e.g., requested, accepted, started, ended) |
| `startTime`       | `string` | Start time of the ride (ISO 8601 format)                      |
| `endTime`         | `string` | End time of the ride (ISO 8601 format)                        |
| `waypoints`       | `array`  | List of waypoints for the ride                                |
| `destination`     | `object` | Destination details                                           |
| `payment`         | `object` | Payment information for the ride                              |
| `estimatedDuration` | `number` | Estimated duration of the ride in seconds                     |
| `estimatedDistance` | `number` | Estimated distance of the ride in kilometers                  |
| `dealsUsed` | `string` | Listed types of deals in use for current ride                      |

[top](#table-of-contents)

### Waypoint

| Field             | Type     | Description                                                    |
|-------------------|----------|----------------------------------------------------------------|
| `waypointId`      | `string` | Unique identifier for the waypoint                            |
| `name`            | `string` | Name of the waypoint                                          |
| `latitude`        | `number` | Latitude of the waypoint                                      |
| `longitude`       | `number` | Longitude of the waypoint                                     |
| `localNames`      | `array`  | List of local names or slang for the waypoint                 |
| `slangNames`      | `array`  | List of local slang names for the waypoint                    |

[top](#table-of-contents)

### Destination

| Field             | Type     | Description                                                    |
|-------------------|----------|----------------------------------------------------------------|
| `destinationId`   | `string` | Unique identifier for the destination                         |
| `name`            | `string` | Name of the destination                                       |
| `latitude`        | `number` | Latitude of the destination                                   |
| `longitude`       | `number` | Longitude of the destination                                  |
| `localNames`      | `array`  | List of local names or slang for the destination              |
| `slangNames`      | `array`  | List of local slang names for the destination                 |
| `Destination@DistanceKm`  |  `number`     | Distance from the destination location            |


[top](#table-of-contents)


### Payment
List of payment options for the service

| Field                 | Type     | Description                                                    |
|-----------------------|----------|----------------------------------------------------------------|
| `paymentOptions`      | `array`  | Available payment options (e.g., credit card, PayPal, cash)   |
| `deals`               | `array`  | Information about available deals or promotions               |
| `dealTime`            | `string` | Time-limited deals or promotions                              |
| `dealLocation`        | `string` | Location-based deals or promotions                            |
| `dealDistance`        | `number` | Distance-based deals or promotions                            |
| `passengerIdLookup`   | `object` | Lookup for passenger-specific deals (e.g., public transport card, work deals) |

[top](#table-of-contents)

### Language
Information about language preferences

| Field             | Type     | Description                                                    |
|-------------------|----------|----------------------------------------------------------------|
| `preference`      | `string` | User's preferred language for the interface(ISO 639-1)        |
| `name`            | `string` | Name of the language                                          |
| `nativeName`      | `string` | Native name of the language                                   |


[top](#table-of-contents)

### Groups and Companies
Information about user groups and associated companies.


| Field             | Type     | Description                                                    |
|-------------------|----------|----------------------------------------------------------------|
| `companyId`       | `string` | Unique identifier for the company                             |
| `name`            | `string` | Name of the company                                           |
| `deals`           | `array`  | Deals or promotions available to employees of the company     |

| Field             | Type     | Description                                                    |
|-------------------|----------|----------------------------------------------------------------|
| `groupId`         | `string` | Unique identifier for the group                               |
| `name`            | `string` | Name of the group                                             |
| `type`            | `string` | Type of the group (e.g., public, private, hidden)             |
| `deals`           | `array`  | List of deals or promotions available to group members        |

[top](#table-of-contents)




### API
Information about the API endpoints and their functionality

| Endpoint          | Method   | Description                                                    |
|-------------------|----------|----------------------------------------------------------------|
| `API@Integration`     | `Text`          | Integration with third-party APIs    |
| `API@Endpoints`        | `Text`         | List of available endpoints              |
| `API@Authentication`   | `Text`        | Authentication methods                    |
| `/users`          | `GET`    | Retrieve a list of users                                      |
| `/users`          | `POST`   | Create a new user                                             |
| `/users/{userId}` | `GET`    | Retrieve a specific user by ID                                |
| `/users/{userId}` | `PUT`    | Update a specific user by ID                                  |
| `/users/{userId}` | `DELETE` | Delete a specific user by ID                                  |
| `/drivers`        | `GET`    | Retrieve a list of drivers                                    |
| `/drivers`        | `POST`   | Create a new driver                                           |
| `/drivers/{driverId}` | `GET`    | Retrieve a specific driver by ID                          |
| `/drivers/{driverId}` | `PUT`    | Update a specific driver by ID                            |
| `/drivers/{driverId}` | `DELETE` | Delete a specific driver by ID                            |
| `/cars`           | `GET`    | Retrieve a list of cars                                       |
| `/cars`           | `POST`   | Create a new car                                              |
| `/cars/{carId}`   | `GET`    | Retrieve a specific car by ID                                 |
| `/cars/{carId}`   | `PUT`    | Update a specific car by ID                                   |
| `/cars/{carId}`   | `DELETE` | Delete a specific car by ID                                   |
| `/rides`          | `GET`    | Retrieve a list of rides                                      |
| `/rides`          | `POST`   | Create a new ride                                             |
| `/rides/{rideId}` | `GET`    | Retrieve a specific ride by ID                                |
| `/rides/{rideId}` | `PUT`    | Update a specific ride by ID                                  |
| `/rides/{rideId}` | `DELETE` | Delete a specific ride by ID                                  |
| `/waypoints`      | `GET`    | Retrieve a list of waypoints                                  |
| `/waypoints`      | `POST`   | Create a new waypoint                                         |
| `/waypoints/{waypointId}` | `GET`    | Retrieve a specific waypoint by ID                    |
| `/waypoints/{waypointId}` | `PUT`    | Update a specific waypoint by ID                        |
| `/waypoints/{waypointId}` | `DELETE` | Delete a specific waypoint by ID                        |
| `/destinations`   | `GET`    | Retrieve a list of destinations                               |
| `/destinations`   | `POST`   | Create a new destination                                      |
| `/destinations/{destinationId}` | `GET`    | Retrieve a specific destination by ID            |
| `/destinations/{destinationId}` | `PUT`    | Update a specific destination by ID                |
| `/destinations/{destinationId}` | `DELETE` | Delete a specific destination by ID                |
| `/payments`       | `GET`    | Retrieve a list of payments                                   |
| `/payments`       | `POST`   | Create a new payment                                          |
| `/payments/{paymentId}` | `GET`    | Retrieve a specific payment by ID                        |
| `/payments/{paymentId}` | `PUT`    | Update a specific payment by ID                            |
| `/payments/{paymentId}` | `DELETE` | Delete a specific payment by ID                            |


    MIT License 2024 Norwegian Carpooling Embassy
