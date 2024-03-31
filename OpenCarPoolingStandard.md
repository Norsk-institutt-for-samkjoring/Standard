# Open CarPool Standard

**General information**
Version: 0.6

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

| Field                | Description                                                                 | Type     |
|----------------------|-----------------------------------------------------------------------------|----------|
| `userId`             | Unique identifier for the user                                             | `string` |
| `name`               | Name of the user                                                           | `string` |
| `phone`              | Phone number(s) of the user                                                | `string` |
| `email`              | Email address of the user                                                  | `string` |
| `pictureUrl`         | URL to the user's profile picture                                          | `string` |
| `language`           | User's preferred language                                                  | `string` |
| `paymentOptions`     | User's preferred payment options (e.g., credit card, PayPal)               | `array`  |
| `groups`             | List of groups the user belongs to                                         | `array`  |
| `companies`          | List of companies the user is associated with                              | `array`  |
| `rating`             | User's rating                                                              | `number` |
| `deals`              | List of active deals for the user                                          | `array`  |
| `defaultApp`         | User's default carpooling app                                              | `string` |

[top](#table-of-contents)

### Driver
Information about the driver or owner

| Field                | Description                                                                 | Type     |
|----------------------|-----------------------------------------------------------------------------|----------|
| `driverId`           | Unique identifier for the driver                                           | `string` |
| `userId`             | Unique identifier of the user associated with the driver                   | `string` |
| `name`               | Name of the driver                                                         | `string` |
| `email`              | Email address of the driver                                                | `string` |
| `phone`              | Phone number(s) of the driver                                              | `string` |
| `carId`              | Unique identifier of the driver's car                                      | `string` |
| `pictureUrl`         | URL to the driver's profile picture                                        | `string` |
| `licenseVerified`    | Indicates if the driver's license has been verified                        | `boolean` |
| `rating`             | Driver's rating                                                            | `number` |

[top](#table-of-contents)

### Car

| Field                | Description                                                                 | Type     |
|----------------------|-----------------------------------------------------------------------------|----------|
| `carId`              | Unique identifier for the car                                              | `string` |
| `color`              | Color of the car                                                           | `string` |
| `type`               | Type of the car (e.g., sedan, SUV, electric, hybrid)                       | `string` |
| `engine`             | Type of propulsion (e.g., gasoline, electric, hybrid)                      | `string` |
| `insurance`          | Insurance information for the car                                          | `object` |
| `capacity`           | Total capacity of the car, including the driver                            | `number` |
| `reservedCapacity`   | Number of seats reserved for the driver (should be 1 for non-autonomous cars) | `number` |
| `plateId`            | License plate number or other means of verification                        | `string` |
| `amenities`          | List of amenities available in the car (e.g., air conditioning, Wi-Fi, child seat) | `array`  |

[top](#table-of-contents)

### Passenger
Could be multiple passengers

| Field                | Description                                                                 | Type     |
|----------------------|-----------------------------------------------------------------------------|----------|
| `passengerId`        | Unique identifier for the passenger                                        | `string` |
| `userId`             | Unique identifier of the user associated with the passenger                | `string` |
| `name`               | Name of the passenger                                                      | `string` |
| `email`              | Email address of the passenger                                             | `string` |
| `phone`              | Phone number(s) of the passenger with international prefix                 | `string` |
| `pictureUrl`         | URL to the passenger's profile picture (needs protection or public image)  | `string` |
| `luggage`            | Information about the passenger's luggage (e.g., number of bags, size)     | `object` |
| `rating`             | Passenger's rating                                                         | `number` |

[top](#table-of-contents)

### Ride

| Field                | Description                                                                 | Type     |
|----------------------|-----------------------------------------------------------------------------|----------|
| `rideId`             | Unique identifier for the ride                                             | `string` |
| `driverId`           | Unique identifier of the driver                                            | `string` |
| `carId`              | Unique identifier of the car                                               | `string` |
| `passengers`         | List of passenger IDs                                                      | `array`  |
| `state`              | Current state of the ride (e.g., requested, accepted, started, ended)      | `string` |
| `startTime`          | Start time of the ride (ISO 8601 format)                                   | `string` |
| `endTime`            | End time of the ride (ISO 8601 format)                                     | `string` |
| `waypoints`          | List of waypoints for the ride                                             | `array`  |
| `destination`        | Destination details                                                        | `object` |
| `payment`            | Payment information for the ride                                           | `object` |
| `estimatedDuration`  | Estimated duration of the ride in seconds                                  | `number` |
| `estimatedDistance`  | Estimated distance of the ride in kilometers                               | `number` |
| `dealsUsed`          | Listed types of deals in use for the current ride                          | `string` |
| `comments`           | Comments about the ride                                                    | `array`  |
| `pickupRange`        | Acceptable range for pickup location (in kilometers)                       | `number` |
| `pickupTimeRange`    | Acceptable time range for pickup (in minutes)                              | `object` |
| `apps`               | List of apps used by the driver and passengers for the ride                | `array`  |
| `isPublic`           | Indicates if the ride is public or private                                 | `boolean` |
| `requestDate`        | Date when the ride was requested (ISO 8601 format)                         | `string` |
| `rideDate`           | Date of the ride (ISO 8601 format)                                         | `string` |

[top](#table-of-contents)

### Waypoint

| Field                | Description                                                                 | Type     |
|----------------------|-----------------------------------------------------------------------------|----------|
| `waypointId`         | Unique identifier for the waypoint                                         | `string` |
| `name`               | Name of the waypoint                                                       | `string` |
| `latitude`           | Latitude of the waypoint                                                   | `number` |
| `longitude`          | Longitude of the waypoint                                                  | `number` |
| `localNames`         | List of local names or slang for the waypoint                              | `array`  |
| `slangNames`         | List of local slang names for the waypoint                                 | `array`  |
| `fuzzyPickup`        | Indicates if the pickup/drop-off location is flexible                 | `boolean` |
| `pickupTime`            | Pickup time window (start and end time)                                    | `object` |
| `country`            | Country of the waypoint                                                    | `string` |
| `pickupComments`         | Comments about the pickup                                    | `array` |

[top](#table-of-contents)

### Destination

| Field                | Description                                                                 | Type     |
|----------------------|--------------------------|----------|
| `destinationId`      | Unique identifier for the destination                                      | `string` |
| `name`               | Name of the destination                                                    | `string` |
| `latitude`           | Latitude of the destination                                                | `number` |
| `longitude`          | Longitude of the destination                                               | `number` |
| `localNames`         | List of local names or slang for the destination                           | `array`  |
| `slangNames`         | List of local slang names for the destination                              | `array`  |
| `country`            | Country of the destination                                                 | `string` |
| `distanceKm`         | Distance from the destination location                                     | `number` |
| `destiComments`         | Comments about the destination                                    | `array` |


[top](#table-of-contents)

### Payment
List of payment options for the service

| Field                | Description                                                                 | Type     |
|----------------------|-----------------------------------------------------------------------------|----------|
| `paymentOptions`     | Available payment options (e.g., credit card, PayPal, cash)                | `array`  |
| `deals`              | Information about available deals or promotions                            | `array`  |
| `dealTime`           | Time-limited deals or promotions                                           | `string` |
| `dealLocation`       | Location-based deals or promotions                                         | `string` |
| `dealDistance`       | Distance-based deals or promotions                                         | `number` |
| `passengerIdLookup`  | Lookup for passenger-specific deals (e.g., public transport card, work deals) | `object` |

[top](#table-of-contents)

### Language
Information about language preferences

| Field                | Description                                                                 | Type     |
|----------------------|-----------------------------------------------------------------------------|----------|
| `preference`         | User's preferred language for the interface (ISO 639-1)                    | `string` |
| `name`               | Name of the language                                                       | `string` |
| `nativeName`         | Native name of the language                                                | `string` |

[top](#table-of-contents)

### Groups and Companies
Information about user groups and associated companies

| Field                | Description                                                                 | Type     |
|----------------------|-----------------------------------------------------------------------------|----------|
| `companyId`          | Unique identifier for the company                                          | `string` |
| `name`               | Name of the company                                                        | `string` |
| `deals`              | Deals or promotions available to employees of the company                  | `array`  |

| Field                | Description                                                                 | Type     |
|----------------------|-----------------------------------------------------------------------------|----------|
| `groupId`            | Unique identifier for the group                                            | `string` |
| `name`               | Name of the group                                                          | `string` |
| `type`               | Type of the group (e.g., public, private, hidden)                          | `string` |
| `deals`              | List of deals or promotions available to group members                     | `array`  |

[top](#table-of-contents)

### API
Information about the API endpoints and their functionality

| Endpoint     | Method    | Description                
|----------------------|-----------|-----------------------------------------------------------------------------------|
| `API@Integration`         | `Text`    | Integration with third-party APIs                                     |
| `API@Endpoints`     | `Text`    | List of available endpoints                                                 |
| `API@Authentication`  | `Text`  | Authentication methods                                                      |
| `/users`             | `GET`     | Retrieve a list of users                                                   |          |
| `/users`             | `POST`    | Create a new user                                                          |          |
| `/users/{userId}`    | `GET`     | Retrieve a specific user by ID                                             |          |
| `/users/{userId}`    | `PUT`     | Update a specific user by ID                                               |          |
| `/users/{userId}`    | `DELETE`  | Delete a specific user by ID                                               |          |
| `/drivers`           | `GET`     | Retrieve a list ofdrivers                                                                 |          |
| `/drivers`           | `POST`    | Create a new driver                                                        |          |
| `/drivers/{driverId}`| `GET`     | Retrieve a specific driver by ID                                           |          |
| `/drivers/{driverId}`| `PUT`     | Update a specific driver by ID                                             |          |
| `/drivers/{driverId}`| `DELETE`  | Delete a specific driver by ID                                             |          |
| `/cars`              | `GET`     | Retrieve a list of cars                                                    |          |
| `/cars`              | `POST`    | Create a new car                                                           |          |
| `/cars/{carId}`      | `GET`     | Retrieve a specific car by ID                                              |          |
| `/cars/{carId}`      | `PUT`     | Update a specific car by ID                                                |          |
| `/cars/{carId}`      | `DELETE`  | Delete a specific car by ID                                                |          |
| `/rides`             | `GET`     | Retrieve a list of rides                                                   |          |
| `/rides`             | `POST`    | Create a new ride                                                          |          |
| `/rides/{rideId}`    | `GET`     | Retrieve a specific ride by ID                                             |          |
| `/rides/{rideId}`    | `PUT`     | Update a specific ride by ID                                               |          |
| `/rides/{rideId}`    | `DELETE`  | Delete a specific ride by ID                                               |          |
| `/waypoints`         | `GET`     | Retrieve a list of waypoints                                               |          |
| `/waypoints`         | `POST`    | Create a new waypoint                                                      |          |
| `/waypoints/{waypointId}` | `GET`     | Retrieve a specific waypoint by ID                                 |          |
| `/waypoints/{waypointId}` | `PUT`     | Update a specific waypoint by ID                                     |          |
| `/waypoints/{waypointId}` | `DELETE`  | Delete a specific waypoint by ID                                     |          |
| `/destinations`      | `GET`     | Retrieve a list of destinations                                            |          |
| `/destinations`      | `POST`    | Create a new destination                                                   |          |
| `/destinations/{destinationId}` | `GET`     | Retrieve a specific destination by ID                         |          |
| `/destinations/{destinationId}` | `PUT`     | Update a specific destination by ID                             |          |
| `/destinations/{destinationId}` | `DELETE`  | Delete a specific destination by ID                             |          |
| `/payments`          | `GET`     | Retrieve a list of payments                                                |          |
| `/payments`          | `POST`    | Create a new payment                                                       |          |
| `/payments/{paymentId}` | `GET`     | Retrieve a specific payment by ID                                     |          |
| `/payments/{paymentId}` | `PUT`     | Update a specific payment by ID                                         |          |
| `/payments/{paymentId}` | `DELETE`  | Delete a specific payment by ID                                         |          |

[top](#table-of-contents)

MIT License 2024 Norwegian Carpooling Embassy

This is the complete Open CarPool Standard (v0.6). The document includes specifications for users, drivers, cars, passengers, rides, waypoints, destinations, payments, languages, groups and companies, and API endpoints. 

