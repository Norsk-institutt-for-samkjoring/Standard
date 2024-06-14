# The Open Carpool standard

We are trying to make reference/guide standard for carpooling

The standard will remain open for all to use, improve, and implement.

Feel free to help out!

[HERE IS THE LATEST ](https://github.com/Norsk-institutt-for-samkjoring/Standard/blob/main/OpenCarPoolingStandard.md "OpenCarPoolingstandard")


![AI think its like this.](samkjore2.png)

### Example 
#Ride from the 
~~version 0.8~~ Version 9

## Ride

### Information about the ride

| Field           	| Description                                     	| Type	|
|---------------------|-----------------------------------------------------|---------|
| rideId          	| Unique identifier for the ride                  	| string  |
| driverId        	| Unique identifier of the driver                 	| string  |
| vehicleId       	| Unique identifier of the vehicle                	| string  |
| passengerIds    	| List of passenger IDs                           	| array   |
| state           	| Current state of the ride (e.g., requested, accepted, started, ended) | enum	|
| startTime       	| Start time of the ride (ISO 8601 format)        	| string  |
| endTime         	| End time of the ride (ISO 8601 format)          	| string  |
| waypointIds     	| List of waypoint IDs for the ride               	| array   |
| destinationId   	| Destination ID                                  	| string  |
| tripstatus      	| A way to pause trip temporarily but not end the trip | string  |
| paymentId       	| Payment ID for the ride                         	| string  |
| estimatedDuration   | Estimated duration of the ride in seconds       	| number  |
| estimatedDistance   | Estimated distance of the ride in kilometers    	| number  |
| dealIds         	| List of deal IDs used for the current ride      	| array   |
| comments        	| Comments about the ride                         	| array   |
| pickupRange     	| Acceptable range for pickup location (in kilometers) | number  |
| pickupNegotiation   | Suggested and negotiation for pickup location   	| number  |
| pickupTimeRange 	| Acceptable time range for pickup (in minutes)   	| object  |
| appIds          	| List of app IDs used by the driver and passengers for the ride | array   |
| isPublic        	| Indicates if the ride is public, private, or hidden | boolean |
| requestDate     	| Date when the ride was requested (ISO 8601 format)  | string  |
| rideDate        	| Date of the ride (ISO 8601 format)              	| string  |
| customFields    	| Custom fields for extending ride information    	| object  |
| qrCode          	| QR code for joining the ride, including timestamp when started | string  |
| rideurl         	| Deep link for the ride                          	| string  |
| riderate        	| A way for users to rate the ride after completion   | string  |
| ridematchfinfo  	| How the match or ride started (e.g., in vehicle, random, planned, matched) | string  |


### Inspiration and similar: 
* https://github.com/TOMP-WG/TOMP-API
* https://github.com/openmobilityfoundation/mobility-data-specification/tree/main#about
* https://github.com/mitfahrverband/mitfahr-api
* https://github.com/mfdz/amarillo
* https://github.com/mitanand

### Todo
- [x] Find license ([MIT](https://github.com/Norsk-institutt-for-samkjoring/Standard/blob/main/LICENSE))
- [ ] Create all possible tags
- [x] Connect with APIs
- [ ] get feedback

### Contributors
* Norwegian carpool embassy / Norsk institutt for samkjøring -> with help from AI's and feedback from others




Layout could be like this:

```
Open CarPool Standard (v0.9)
│
├── README
│
├── User
│   ├── userId
│   ├── name
│   ├── email
│   ├── phone
│   ├── pictureUrl
│   ├── language
│   ├── locale
│   ├── accessibilityNeeds
│   ├── paymentOptions
│   ├── groups
│   ├── companies
│   ├── rating
│   ├── rides
│   ├── deals
│   ├── defaultApp
│   └── customFields
│
├── Driver
│   ├── driverId
│   ├── userId
│   ├── licenseVerified
│   ├── customFields
│   └── rating
│
├── Vehicle
│   ├── vehicleId
│   ├── driverId
│   ├── color
│   ├── type
│   ├── engine
│   ├── vehiclepos
│   ├── insurance
│   ├── capacity
│   ├── reservedCapacity
│   ├── vehiclePicture
│   ├── plateId
│   ├── amenities
│   ├── vehiclespeedlimit
│   ├── autopilot
│   ├── laneAssistance
│   ├── advancedFeatures
│   └── customFields
│
├── Passenger
│   ├── passengerId
│   ├── userId
│   ├── luggage
│   ├── passengerposs
│   └── customFields
│
├── Ride
│   ├── rideId
│   ├── driverId
│   ├── vehicleId
│   ├── passengerIds
│   ├── state
│   ├── startTime
│   ├── endTime
│   ├── waypointIds
│   ├── destinationId
│   ├── tripstatus
│   ├── paymentId
│   ├── estimatedDuration
│   ├── estimatedDistance
│   ├── dealIds
│   ├── comments
│   ├── pickupRange
│   ├── pickupNegotiation
│   ├── pickupTimeRange
│   ├── appIds
│   ├── isPublic
│   ├── requestDate
│   ├── rideDate
│   ├── customFields
│   ├── qrCode
│   ├── rideurl
│   ├── riderate
│   └── ridematchfinfo
│
├── Waypoint
│   ├── waypointId
│   ├── name
│   ├── latitude
│   ├── longitude
│   ├── openForNegotiation
│   ├── via waypoint
│   ├── localNames
│   ├── country
│   ├── pickupComments
│   └── customFields
│
├── Destination
│   ├── destinationId
│   ├── destinationNegotiation
│   ├── name
│   ├── latitude
│   ├── longitude
│   ├── localNames
│   ├── country
│   ├── distanceKm
│   ├── destinationComments
│   └── customFields
│
├── Payment
│   ├── paymentId
│   ├── rideId
│   ├── paymentOptions
│   ├── dealIds
│   ├── status
│   └── customFields
│
├── Language
│   ├── languageCode
│   ├── name
│   └── nativeName
│
├── Groups_and_Companies
│   ├── groupId
│   ├── name
│   ├── type
│   ├── dealIds
│   └── customFields
│
├── API
│   ├── Endpoint
│   │   ├── /v1/deals
│   │   ├── /v1/promotions
│   │   ├── /v1/discounts
│   │   ├── /v1/authentication
│   │   ├── /v1/user-preferences
│   │   └── /v1/settings
│   ├── Authentication
│   │   ├── /v1/login
│   │   └── /v1/logout
│   ├── README
│   └── Versioning
│
└── LICENSE

```



```
class Ride:
    def __init__(self, ride_id, driver_id, vehicle_id, passenger_ids, state, start_time, end_time, waypoint_ids, destination_id, trip_status, payment_id, estimated_duration, estimated_distance, deal_ids, comments, pickup_range, pickup_negotiation, pickup_time_range, app_ids, is_public, request_date, ride_date, custom_fields=None, qr_code=None, ride_url=None, ride_rate=None, ride_match_info=None):
        self.ride_id = ride_id
        self.driver_id = driver_id
        self.vehicle_id = vehicle_id
        self.passenger_ids = passenger_ids
        self.state = state
        self.start_time = start_time
        self.end_time = end_time
        self.waypoint_ids = waypoint_ids
        self.destination_id = destination_id
        self.trip_status = trip_status
        self.payment_id = payment_id
        self.estimated_duration = estimated_duration
        self.estimated_distance = estimated_distance
        self.deal_ids = deal_ids
        self.comments = comments
        self.pickup_range = pickup_range
        self.pickup_negotiation = pickup_negotiation
        self.pickup_time_range = pickup_time_range
        self.app_ids = app_ids
        self.is_public = is_public
        self.request_date = request_date
        self.ride_date = ride_date
        self.custom_fields = custom_fields
        self.qr_code = qr_code
        self.ride_url = ride_url
        self.ride_rate = ride_rate
        self.ride_match_info = ride_match_info

# Example usage:
ride = Ride(
    ride_id="123456",
    driver_id="789012",
    vehicle_id="345678",
    passenger_ids=["passenger1", "passenger2"],
    state="requested",
    start_time="2024-04-01T08:00:00Z",
    end_time="2024-04-01T10:00:00Z",
    waypoint_ids=["waypoint1", "waypoint2"],
    destination_id="789",
    trip_status="",
    payment_id="123",
    estimated_duration=7200,
    estimated_distance=50,
    deal_ids=["deal1", "deal2"],
    comments=["Comment 1", "Comment 2"],
    pickup_range=5.0,
    pickup_negotiation=0,  # Adjust as needed
    pickup_time_range={"start": "2024-04-01T07:45:00Z", "end": "2024-04-01T08:15:00Z"},
    app_ids=["app1", "app2"],
    is_public=True,
    request_date="2024-03-31T12:00:00Z",
    ride_date="2024-06-06T08:00:00Z"
)


```## Code Components

- User
- Driver
- Vehicle
- Passenger
- Ride
- Waypoint
- Destination
- Payment
- Language
- Groups and Companies
- API
- Internationalization
- Extensions
- Security and Privacy
- Real-time Updates
- Geospatial
- Analytics and Reporting
- Integration
- Developer Resources
- Versioning
- Certification and Compliance

Additionally, it provides API endpoints for managing users, drivers, vehicles, rides, waypoints, destinations, payments, languages, groups, and companies.

