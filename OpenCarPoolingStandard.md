# Open CarPool Standard

**General information**
Version: 0.7
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
| `email`              | Email address of the user                                                  | `string` |
| `phone`              | Phone number(s) of the user                                                | `string` |
| `pictureUrl`         | URL to the user's profile picture (protected)                              | `string` |
| `language`           | User's preferred language (ISO 639-1)                                      | `string` |
| `accessibilityNeeds` | User's accessibility needs (e.g., wheelchair access)                       | `array`  |
| `paymentOptions`     | User's preferred payment options (e.g., credit card, PayPal)               | `array`  |
| `groups`             | List of group IDs the user belongs to                                      | `array`  |
| `companies`          | List of company IDs the user is associated with                            | `array`  |
| `rating`             | User's rating                                                              | `number` |
| `deals`              | List of active deal IDs for the user                                       | `array`  |
| `defaultApp`         | User's default carpooling app                                              | `string` |

[top](#table-of-contents)

### Driver
Information about the driver

| Field                | Description                                                                 | Type     |
|----------------------|-----------------------------------------------------------------------------|----------|
| `driverId`           | Unique identifier for the driver                                           | `string` |
| `userId`             | Unique identifier of the user associated with the driver                   | `string` |
| `licenseVerified`    | Indicates if the driver's license has been verified                        | `boolean` |

[top](#table-of-contents)

### Car

| Field                | Description                                                                 | Type     |
|----------------------|-----------------------------------------------------------------------------|----------|
| `carId`              | Unique identifier for the car                                              | `string` |
| `driverId`           | Unique identifier of the driver associated with the car                    | `string` |
| `color`              | Color of the car                                                           | `string` |
| `type`               | Type of the car (e.g., sedan, SUV, electric, hybrid)                       | `enum`   |
| `engine`             | Type of propulsion (e.g., gasoline, electric, hybrid)                      | `enum`   |
| `insurance`          | Insurance information for the car                                          | `object` |
| `capacity`           | Total capacity of the car, including the driver                            | `number` |
| `reservedCapacity`   | Number of seats reserved for the driver (should be 1 for non-autonomous cars) | `number` |
| `carpicture`   | URL to picture of the car) | `string` |
| `plateId`            | License plate number or other means of verification                        | `string` |
| `amenities`          | List of amenities available in the car (e.g., air conditioning, Wi-Fi, child seat) | `array`  |

[top](#table-of-contents)

### Passenger
Could be multiple passengers

| Field                | Description                                                                 | Type     |
|----------------------|-----------------------------------------------------------------------------|----------|
| `passengerId`        | Unique identifier for the passenger                                        | `string` |
| `userId`             | Unique identifier of the user associated with the passenger                | `string` |
| `luggage`            | Information about the passenger's luggage (e.g., number of bags, size)     | `object` |

[top](#table-of-contents)

### Ride

| Field                | Description                                                                 | Type     |
|----------------------|-----------------------------------------------------------------------------|----------|
| `rideId`             | Unique identifier for the ride                                             | `string` |
| `driverId`           | Unique identifier of the driver                                            | `string` |
| `carId`              | Unique identifier of the car                                               | `string` |
| `passengerIds`       | List of passenger IDs                                                      | `array`  |
| `state`              | Current state of the ride (e.g., requested, accepted, started, ended)      | `enum`   |
| `startTime`          | Start time of the ride (ISO 8601 format)                                   | `string` |
| `endTime`            | End time of the ride (ISO 8601 format)                                     | `string` |
| `waypointIds`        | List of waypoint IDs for the ride                                          | `array`  |
| `destinationId`      | Destination ID                                                             | `string` |
| `paymentId`          | Payment ID for the ride                                                    | `string` |
| `estimatedDuration`  | Estimated duration of the ride in seconds                                  | `number` |
| `estimatedDistance`  | Estimated distance of the ride in kilometers                               | `number` |
| `dealIds`            | List of deal IDs used for the current ride                                 | `array`  |
| `comments`           | Comments about the ride                                                    | `array`  |
| `pickupRange`        | Acceptable range for pickup location (in kilometers)                       | `number` |
| `pickupTimeRange`    | Acceptable time range for pickup (in minutes)                              | `object` |
| `appIds`             | List of app IDs used by the driver and passengers for the ride             | `array`  |
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
| `country`            | Country of the waypoint                                                    | `string` |
| `pickupComments`         | Comments about the waypoint                                    | `array` |

[top](#table-of-contents)

### Destination

| Field                | Description                                                                 | Type     |
|----------------------|-----------------------------------------------------------------------------|----------|
| `destinationId`      | Unique identifier for the destination                                      | `string` |
| `name`               | Name of the destination                                                    | `string` |
| `latitude`           | Latitude of the destination                                                | `number` |
| `longitude`          | Longitude of the destination                                               | `number` |
| `localNames`         | List of local names or slang for the destination                           | `array`  |
| `country`            | Country of the destination                                                 | `string` |
| `distanceKm`         | Distance from the destination location                                     | `number` |
| `destiComments`         | Comments about the destination                                    | `array` |

[top](#table-of-contents)

### Payment
List of payment options for the service

| Field                | Description          | Type     |
|----------------------|-----------------------------------------------------------------------------|----------|
| `paymentId`          | Unique identifier for the payment                                          | `string` |
| `rideId`             | Unique identifier of the associated ride                                   | `string` |
| `paymentOptions`     | Available payment options (e.g., credit card, PayPal, cash)                | `array`  |
| `dealIds`            | List of deal IDs applied to the payment, passenger-specific deals, location, time or distance based promotions                                    | `array`  |
| `status`             | Status of the payment (e.g., pending, completed, failed)                   | `enum`   |

[top](#table-of-contents)

### Language
Information about language preferences

| Field                | Description                                                                 | Type     |
|----------------------|-----------------------------------------------------------------------------|----------|
| `languageCode`       | Language code (ISO 639-1)                                                  | `string` |
| `name`               | Name of the language                                                       | `string` |
| `nativeName`         | Native name of the language                                                | `string` |

[top](#table-of-contents)

### Groups and Companies
Information about user groups and associated companies

| Field                | Description                                                                 | Type     |
|----------------------|-----------------------------------------------------------------------------|----------|
| `groupId`            | Unique identifier for the group                                            | `string` |
| `name`               | Name of the group                                                          | `string` |
| `type`               | Type of the group (e.g., public, private, hidden)                          | `enum`   |
| `dealIds`            | List of deal IDs available to group members                                | `array`  |

| Field                | Description                                                                 | Type     |
|----------------------|-----------------------------------------------------------------------------|----------|
| `companyId`          | Unique identifier for the company                                          | `string` |
| `name`               | Name of the company                                                        | `string` |
| `dealIds`            | List of deal IDs available to employees of the company                     | `array`  |

[top](#table-of-contents)

### API
Information about the API endpoints and their functionality

| Endpoint             | Method    | Description                                                                 | Type     |
|----------------------|-----------|-----------------------------------------------------------------------------|----------|
| `API@Integration`         | `Text`    | Integration with third-party APIs                                     |
| `API@Endpoints`     | `Text`    | List of available endpoints                                                 |
| `API@Authentication`  | `Text`  | Authentication methods    
| `/v1/users`          | `GET`     | Retrieve a list of users (paginated, filterable, sortable)                 |          |
| `/v1/users`          | `POST`    | Create a new user                                                          |          |
| `/v1/users/{userId}` | `GET`     | Retrieve a specific user by ID                                             |          |
| `/v1/users/{userId}` | `PUT`     | Update a specific user by ID                                               |          |
| `/v1/users/{userId}` | `DELETE`  | Delete a specific user by ID                                               |          |
| `/v1/drivers`        | `GET`     | Retrieve a list of drivers (paginated, filterable, sortable)               |          |
| `/v1/drivers`        | `POST`    | Create a new driver                                                        |          |
| `/v1/drivers/{driverId}` | `GET`     | Retrieve a specific driver by ID                                       |          |
| `/v1/drivers/{driverId}` | `PUT`     | Update a specific driver by ID                                         |          |
| `/v1/drivers/{driverId}` | `DELETE`  | Delete a specific driver by ID                                         |          |
| `/v1/cars`           | `GET`     | Retrieve a list of cars (paginated, filterable, sortable)                  |          |
| `/v1/cars`           | `POST`    | Create a new car                                                           |          |
| `/v1/cars/{carId}`   | `GET`     | Retrieve a specific car by ID                                              |          |
| `/v1/cars/{carId}`   | `PUT`     | Update a specific car by ID                                                |          |
| `/v1/cars/{carId}`   | `DELETE`  | Delete a specific car by ID                                                |          |
| `/v1/rides`          | `GET`     | Retrieve a list of rides (paginated, filterable, sortable)                |          |
| `/v1/rides`          | `POST`    | Create a new ride                                                         |          |
| `/v1/rides/{rideId}` | `GET`     | Retrieve a specific ride by ID                                            |          |
| `/v1/rides/{rideId}` | `PUT`     | Update a specific ride by ID                                              |          |
| `/v1/rides/{rideId}` | `DELETE`  | Delete a specific ride by ID                                              |          |
| `/v1/waypoints`      | `GET`     | Retrieve a list of waypoints (paginated, filterable, sortable)            |          |
| `/v1/waypoints`      | `POST`    | Create a new waypoint                                                     |          |
| `/v1/waypoints/{waypointId}` | `GET`     | Retrieve a specific waypoint by ID                                |          |
| `/v1/waypoints/{waypointId}` | `PUT`     | Update a specific waypoint by ID                                    |          |
| `/v1/waypoints/{waypointId}` | `DELETE`  | Delete a specific waypoint by ID                                    |          |
| `/v1/destinations`   | `GET`     | Retrieve a list of destinations (paginated, filterable, sortable)         |          |
| `/v1/destinations`   | `POST`    | Create a new destination                                                  |          |
| `/v1/destinations/{destinationId}` | `GET`     | Retrieve a specific destination by ID                        |          |
| `/v1/destinations/{destinationId}` | `PUT`     | Update a specific destination by ID                            |          |
| `/v1/destinations/{destinationId}` | `DELETE`  | Delete a specific destination by ID                            |          |
| `/v1/payments`       | `GET`     | Retrieve a list of payments (paginated, filterable, sortable)             |          |
| `/v1/payments`       | `POST`    | Create a new payment                                                      |          |
| `/v1/payments/{paymentId}` | `GET`     | Retrieve a specific payment by ID                                    |          |
| `/v1/payments/{paymentId}` | `PUT`     | Update a specific payment by ID                                        |          |
| `/v1/payments/{paymentId}` | `DELETE`  | Delete a specific payment by ID                                        |          |

Note: All endpoints should implement proper authentication, authorization, and security measures. Error handling and documentation should be provided for each endpoint. Pagination, filtering, and sorting should be supported where applicable.

[top](#table-of-contents)

This concludes the updated version of the Open CarPool Standard (v0.7) 
The standard now includes normalized data structures, enhanced data integrity, improved object relationships, accessibility and privacy considerations, and API design improvements.

MIT License 2024 Norwegian Carpooling Embassy

                                                      

