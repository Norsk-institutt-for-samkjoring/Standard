# The Open Carpool standard

We are trying to make reference/guide standard for carpooling

The standard will remain open for all to use, improve, and implement.

Feel free to help out!



### Example 
#Ride from the 
~~standard version 0.6~~ [Version 8 WIP](https://github.com/Norsk-institutt-for-samkjoring/Standard/blob/main/OpenCarPoolingStandard.md "OpenCarPoolingstandard")

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
| `customFields`       | Custom fields for extending ride information                               | `object` |



### Inspiration and similar: 
* https://github.com/TOMP-WG/TOMP-API
* https://github.com/openmobilityfoundation/mobility-data-specification/tree/main#about
* https://github.com/mitfahrverband/mitfahr-api
* https://github.com/mfdz/amarillo

### Todo
- [x] Find license ([MIT](https://github.com/Norsk-institutt-for-samkjoring/Standard/blob/main/LICENSE))
- [ ] Create all possible tags
- [x] Connect with APIs
- [ ] get feedback

### Contributors
* Norwegian carpool embassy / Norsk institutt for samkjøring -> with help from AI's

Layout could be like this:
```
Open CarPool Standard (v0.6)
│
├── README
├── User
│   ├── userId
│   ├── name
│   ├── phone
│   ├── email
│   ├── pictureUrl
│   ├── language
│   ├── paymentOptions
│   ├── groups
│   ├── companies
│   ├── rating
│   ├── deals
│   ├── defaultApp
│   └── README
│
├── Driver
│   ├── driverId
│   ├── userId
│   ├── name
│   ├── email
│   ├── phone
│   ├── carId
│   ├── pictureUrl
│   ├── licenseVerified
│   ├── rating
│   └── README
│
├── Car
│   ├── carId
│   ├── color
│   ├── type
│   ├── engine
│   ├── insurance
│   ├── capacity
│   ├── reservedCapacity
│   ├── plateId
│   ├── amenities
│   └── README
│
├── Passenger
│   ├── passengerId
│   ├── userId
│   ├── name
│   ├── email
│   ├── phone
│   ├── pictureUrl
│   ├── luggage
│   └── README
│
├── Ride
│   ├── rideId
│   ├── driverId
│   ├── carId
│   ├── passengers
│   ├── state
│   ├── startTime
│   ├── endTime
│   ├── waypoints
│   ├── destination
│   ├── payment
│   ├── estimatedDuration
│   ├── estimatedDistance
│   ├── dealsUsed
│   ├── comments
│   ├── pickupRange
│   ├── pickupTimeRange
│   ├── apps
│   ├── isPublic
│   ├── requestDate
│   └── rideDate
│
├── Waypoint
│   ├── waypointId
│   ├── name
│   ├── latitude
│   ├── longitude
│   ├── localNames
│   ├── slangNames
│   ├── fuzzyPickup
│   ├── pickupTime
│   ├── country
│   └── pickupComments
│
├── Destination
│   ├── destinationId
│   ├── name
│   ├── latitude
│   ├── longitude
│   ├── localNames
│   ├── slangNames
│   ├── country
│   ├── distanceKm
│   └── destiComments
│
├── Payment
│   ├── paymentOptions
│   ├── deals
│   ├── dealTime
│   ├── dealLocation
│   ├── dealDistance
│   └── passengerIdLookup
│
├── Language
│   ├── preference
│   ├── name
│   └── nativeName
│
├── Groups_and_Companies
│   ├── companyId
│   ├── name
│   ├── deals
│   ├── groupId
│   ├── type
│   └── README
│
├── API
│   ├── API@Integration
│   ├── API@Endpoints
│   ├── API@Authentication
│   ├── users
│   ├── drivers
│   ├── cars
│   ├── rides
│   ├── waypoints
│   ├── destinations
│   ├── payments
│   └── README
│
└── LICENSE

```



```
class Ride:
    def __init__(self, ride_id, driver_id, car_id, passengers, state, start_time, end_time, waypoints, destination, payment, estimated_duration, estimated_distance, deals_used, comments, pickup_range, pickup_time_range, apps, is_public, request_date, ride_date):
        self.ride_id = ride_id
        self.driver_id = driver_id
        self.car_id = car_id
        self.passengers = passengers
        self.state = state
        self.start_time = start_time
        self.end_time = end_time
        self.waypoints = waypoints
        self.destination = destination
        self.payment = payment
        self.estimated_duration = estimated_duration
        self.estimated_distance = estimated_distance
        self.deals_used = deals_used
        self.comments = comments
        self.pickup_range = pickup_range
        self.pickup_time_range = pickup_time_range
        self.apps = apps
        self.is_public = is_public
        self.request_date = request_date
        self.ride_date = ride_date

# Example usage:
ride = Ride(
    ride_id="123456",
    driver_id="789012",
    car_id="345678",
    passengers=["passenger1", "passenger2"],
    state="requested",
    start_time="2024-04-01T08:00:00Z",
    end_time="2024-04-01T10:00:00Z",
    waypoints=["waypoint1", "waypoint2"],
    destination={"destinationId": "789", "name": "Destination Name", "latitude": 123.456, "longitude": -78.901, "country": "Country Name", "distanceKm": 10.5},
    payment={"paymentId": "123", "amount": 25.0, "currency": "USD"},
    estimated_duration=7200,
    estimated_distance=50,
    deals_used=["deal1", "deal2"],
    comments=["Comment 1", "Comment 2"],
    pickup_range=5.0,
    pickup_time_range={"start": "2024-04-01T07:45:00Z", "end": "2024-04-01T08:15:00Z"},
    apps=["app1", "app2"],
    is_public=True,
    request_date="2024-03-31T12:00:00Z",
    ride_date="2024-04-01T08:00:00Z"
)

```

## Code Components

This code file includes the following components:

### ride

Represents a single ridesharing trip, including details such as:
- Ride ID
- Start and end times
- Locations
- Estimated and actual duration and distance
- Driver and car information
- Passenger details
- Ride status
- Fare breakdown
- Comments

### car

Contains information about the car used for the ride, including:
- Car ID
- Make, model, year
- Color
- License plate
- Seating capacity
- Reserved capacity for the driver
- Available amenities
- Insurance details

### driver

Represents the driver of the ridesharing car, including:
- Driver ID
- User ID associated with the driver
- Name
- Contact details
- Profile picture URL
- License verification status
- Ratings

### passenger

Represents a passenger in the ridesharing car, including:
- Passenger ID
- User ID associated with the passenger
- Name
- Contact details
- Profile picture URL
- Luggage details
- Ratings

### payment

Contains payment information for the ride, including:
- Payment options
- Deals or promotions
- Time-limited deals
- Location-based deals
- Distance-based deals
- Passenger-specific deals

Additionally, it provides API endpoints for managing:
- Users
- Drivers
- Cars
- Rides
- Waypoints
- Destinations
- Payments
- Languages
- Groups and companies


Additionally, it provides API endpoints for managing users, drivers, cars, rides, waypoints, destinations, payments, languages, groups and companies.


