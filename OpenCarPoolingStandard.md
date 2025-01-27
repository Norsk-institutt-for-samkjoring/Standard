# Open CarPool Standard

**Version: 1.0 **

**Work in progress, feel free to add items for it to be included in the 1.1 release**

This document contains specifications for carpooling.

## Table of Contents

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

## User

### Information about the users

| Field          	| Description                                    	| Type	|
|--------------------|----------------------------------------------------|---------|
| userId         	| Unique identifier for the user                 	| string  |
| name           	| Name of the user                               	| string  |
| email          	| Email address of the user                      	| string  |
| phone          	| Phone number(s) of the user                    	| string  |
| pictureUrl     	| URL to the user's profile picture (protected)  	| string  |
| language       	| User's preferred language (ISO 639-1)          	| string  |
| locale         	| User's locale for formatting dates, times, and currencies | string  |
| accessibilityNeeds | User's accessibility needs (e.g., wheelchair access, guide dog, deaf) | array   |
| paymentOptions 	| User's preferred payment options (e.g., credit card, PayPal) | array   |
| groups         	| List of group IDs the user belongs to          	| array   |
| companies      	| List of company IDs the user is associated with	| array   |
| rating         	| User's rating                                  	| number  |
| backgroundCheck         	| Indicates if a background check has been completed, and what type/date                                 	| object  |
| rides          	| Number of rides taken by the user              	| number  |
| deals          	| List of active deal IDs for the user           	| array   |
| defaultApp     	| User's default carpooling app/agency           	| string  |
| customFields   	| Custom fields for extending user information, like Carbon Tracking, distance covered   	| object  |
| realTimeSharing 	| Real-time sharing of ride information with trusted contacts             	| boolean |
| emergencyContacts  | List of emergency contacts to notify during a ride (e.g., name, phone number) | array  |


[top](#table-of-contents)

## Driver

### Information about the driver

| Field       	| Description                             	| Type	|
|-----------------|---------------------------------------------|---------|
| driverId    	| Unique identifier for the driver        	| string  |
| userId      	| Unique identifier of the user associated with the driver | string  |
| licenseVerified | Indicates if the driver's license has been verified | boolean |
| customFields	| Custom fields for extending driver information | object  |

[top](#table-of-contents)

## Vehicle

### Information about the vehicle

| Field         	| Description                                     	| Type	|
|-------------------|-----------------------------------------------------|---------|
| vehicleId     	| Unique identifier for the vehicle               	| string  |
| driverId      	| Unique identifier of the driver associated with the vehicle | string  |
| color         	| Color of the vehicle                             	| string  |
| type          	| Type of vehicle (e.g., sedan, SUV, electric, hybrid, bike, boat, helicopter, bus, flatbed) | enum	|
| engine        	| Type of propulsion (e.g., gasoline, electric, hybrid, human) | enum	|
| sustainabilityScore | A score representing the sustainability of the vehicle | number |
| vehiclepos    	| Vehicle or driver's position for dynamic matching, or shown on map (like Waze) | string  |
| insurance     	| Insurance information for the vehicle           	| object  |
| capacity      	| Total capacity of the vehicle, including the driver | number  |
| reservedCapacity  | Number of seats reserved for the driver (should be 1 for non-autonomous vehicles) | number  |
| vehiclePicture	| URL to a picture of the vehicle                 	| string  |
| plateId       	| License plate number or other means of verification | string  |
| amenities     	| List of amenities available in the vehicle (e.g., air conditioning, Wi-Fi, child seat, phone charger, animal cage, non-animal, accessibility attributes, sunshade/sunroof, retractable roof) | array   |
| vehiclespeedlimit | Maximum speed limit for the vehicle (if different from normal, like for A-traktor) | number  |
| autopilot          	| Indicates if the vehicle is equipped with an autopilot system, and what level   | object|
| laneAssistance     	| Indicates if the vehicle has lane assistance capabilities   	| boolean|
| advancedFeatures   	| List of advanced features available in the vehicle (e.g., adaptive cruise control, emergency braking, parking assistance) | array  |
| customFields  	| Custom fields for extending vehicle information 	| object  |

[top](#table-of-contents)

## Passenger

### Information about the passenger

| Field      	| Description                                           	| Type	|
|----------------|-----------------------------------------------------------|---------|
| passengerId	| Unique identifier for the passenger                   	| string  |
| userId     	| Unique identifier of the user associated with the passenger | string  |
| luggage    	| Information about the passenger's luggage (e.g., number of bags, size) | object  |
| passengerposs  | Passenger's position for dynamic matching, or shown on map (like Waze), could be time-coded and toggled on/off | string  |
| customFields   | Custom fields for extending passenger information     	| object  |

[top](#table-of-contents)

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
| sustainabilityScore | A score representing the sustainability of the ride (e.g., based on vehicle type and distance) | number |


[top](#table-of-contents)

## Waypoint

### Information about the waypoint

| Field        	| Description                                        	| Type	|
|------------------|--------------------------------------------------------|---------|
| waypointId   	| Unique identifier for the waypoint                 	| string  |
| name         	| Name of the waypoint                               	| string  |
| latitude     	| Latitude of the waypoint                           	| number  |
| longitude    	| Longitude of the waypoint                          	| number  |
| openForNegotiation | If the waypoint is open for negotiation           	| boolean |
| viawaypoint 	| Allowing passenger or driver to set via points     	| object  |
| localNames   	| List of local names or slang for the waypoint      	| array   |
| country      	| Country of the waypoint                            	| string  |
| pickupComments   | Comments about the waypoint                        	| array   |
| customFields 	| Custom fields for extending waypoint information   	| object  |

[top](#table-of-contents)

## Destination

### Information about the destination

| Field            	| Description                                   	| Type	|
|----------------------|---------------------------------------------------|---------|
| destinationId    	| Unique identifier for the destination         	| string  |
| destinationNegotiation | Suggested and negotiation for destination location | number  |
| name             	| Name of the destination                       	| string  |
| latitude         	| Latitude of the destination                   	| number  |
| longitude        	| Longitude of the destination                  	| number  |
| localNames       	| List of local names or slang for the destination  | array   |
| country          	| Country of the destination                    	| string  |
| distanceKm       	| Distance from the destination location        	| number  |
| destinationComments  | Comments about the destination                	| array   |
| customFields     	| Custom fields for extending destination information | object  |

[top](#table-of-contents)

## Payment

### List of payment options for the service

| Field      	| Description                                         	| Type	|
|----------------|---------------------------------------------------------|---------|
| paymentId  	| Unique identifier for the payment                   	| string  |
| rideId     	| Unique identifier of the associated ride            	| string  |
| paymentOptions | Available payment options (e.g., credit card, PayPal, cash) | array   |
| dealIds    	| List of deal IDs applied to the payment,
 including passenger-specific deals, location, time or distance-based promotions | array   |
| status     	| Status of the payment (e.g., pending, completed, failed) | enum	|
| customFields   | Custom fields for extending payment information, which could also be used for compensation, tips, payment for additional services | object  |

[top](#table-of-contents)

## Language

### Information about language preferences

| Field    	| Description                      	| Type	|
|--------------|--------------------------------------|---------|
| languageCode | Language code (ISO 639-1)        	| string  |
| name     	| Name of the language             	| string  |
| nativeName   | Native name of the language      	| string  |

[top](#table-of-contents)

## Groups and Companies

### Information about user groups and associated companies

| Field      	| Description                           	| Type	|
|----------------|-------------------------------------------|---------|
| groupId    	| Unique identifier for the group       	| string  |
| name       	| Name of the group                     	| string  |
| type       	| Type of the group (e.g., public, private, hidden) | enum	|
| dealIds    	| List of deal IDs available to group members | array   |
| customFields   | Custom fields for extending group information | object  |
| socialFeatures  	| Social features for matching users with similar interests or destinations   | object |


| Field      	| Description                           	| Type	|
|----------------|-------------------------------------------|---------|
| companyId  	| Unique identifier for the company     	| string  |
| name       	| Name of the company                   	| string  |
| dealIds    	| List of deal IDs available to employees of the company | array   |
| customFields   | Custom fields for extending company information | object  |

[top](#table-of-contents)


## API Example

### Information about the API endpoints and their functionality

| Endpoint                      	| Method | Description                                                                               	|
|-----------------------------------|--------|-----------------------------------------------------------------------------------------------|
| /v1/users                     	| GET	| Retrieve a list of users (paginated, filterable, sortable)                                 	|
| /v1/users                     	| POST   | Create a new user                                                                         	|
| /v1/users/{userId}            	| GET	| Retrieve a specific user by ID                                                            	|
| /v1/users/{userId}            	| PUT	| Update a specific user by ID                                                              	|
| /v1/users/{userId}            	| DELETE | Delete a specific user by ID                                                              	|
| /v1/drivers                   	| GET	| Retrieve a list of drivers (paginated, filterable, sortable)                              	|
| /v1/drivers                   	| POST   | Create a new driver                                                                       	|
| /v1/drivers/{driverId}        	| GET	| Retrieve a specific driver by ID                                                          	|
| /v1/drivers/{driverId}        	| PUT	| Update a specific driver by ID                                                            	|
| /v1/drivers/{driverId}        	| DELETE | Delete a specific driver by ID                                                            	|
| /v1/vehicles                  	| GET	| Retrieve a list of vehicles (paginated, filterable, sortable)                             	|
| /v1/vehicles                  	| POST   | Create a new vehicle                                                                      	|
| /v1/vehicles/{vehicleId}      	| GET	| Retrieve a specific vehicle by ID                                                         	|
| /v1/vehicles/{vehicleId}      	| PUT	| Update a specific vehicle by ID                                                           	|
| /v1/vehicles/{vehicleId}      	| DELETE | Delete a specific vehicle by ID                                                           	|
| /v1/rides                     	| GET	| Retrieve a list of rides (paginated, filterable, sortable)                                	|
| /v1/rides                     	| POST   | Create a new ride                                                                         	|
| /v1/rides/{rideId}            	| GET	| Retrieve a specific ride by ID                                                            	|
| /v1/rides/{rideId}            	| PUT	| Update a specific ride by ID                                                              	|
| /v1/rides/{rideId}            	| DELETE | Delete a specific ride by ID                                                              	|
| /v1/waypoints                 	| GET	| Retrieve a list of waypoints (paginated, filterable, sortable)                            	|
| /v1/waypoints                 	| POST   | Create a new waypoint                                                                     	|
| /v1/waypoints/{waypointId}    	| GET	| Retrieve a specific waypoint by ID                                                        	|
| /v1/waypoints/{waypointId}    	| PUT	| Update a specific waypoint by ID                                                          	|
| /v1/waypoints/{waypointId}    	| DELETE | Delete a specific waypoint by ID                                                          	|
| /v1/destinations              	| GET	| Retrieve a list of destinations (paginated, filterable, sortable)                         	|
| /v1/destinations              	| POST   | Create a new destination                                                                  	|
| /v1/destinations/{destinationId}  | GET	| Retrieve a specific destination by ID                                                     	|
| /v1/destinations/{destinationId}  | PUT	| Update a specific destination by ID                                                       	|
| /v1/destinations/{destinationId}  | DELETE | Delete a specific destination by ID                                                       	|
| /v1/users/{userId}/sharing     	| GET    | Get real-time sharing settings for a user                    |
| /v1/users/{userId}/sharing     	| PUT    | Update real-time sharing settings                            |
| /v1/sustainability/vehicles    	| GET    | Get sustainability scores for vehicles                        |
| /v1/sustainability/rides       	| GET    | Get sustainability metrics for rides                          |
| /v1/social/matches            	| GET    | Get potential carpool matches based on social preferences      |
| /v1/social/interests          	| PUT    | Update user's social matching preferences                      |
| /v1/payments                  	| GET	| Retrieve a list of payments (paginated, filterable, sortable)                             	|
| /v1/payments                  	| POST   | Create a new payment                                                                      	|
| /v1/payments/{paymentId}      	| GET	| Retrieve a specific payment by ID                                                         	|
| /v1/payments/{paymentId}      	| PUT	| Update a specific payment by ID                                                           	|
| /v1/payments/{paymentId}      	| DELETE | Delete a specific payment by ID                                                           	|
| /v1/vehicles/{vehicleId}/autonomous  | GET    |  Get autonomous driving capabilities and certification (e.g., level of autonomy, certification status)      |
| /v1/vehicles/{vehicleId}/safety 	| GET    | Get vehicle safety certifications and features (e.g., crash test ratings, advanced safety systems)             |
| /v1/background-checks         	| POST   | Initiate a background check for a user                        |
| /v1/background-checks/{checkId}	| GET    | Get status and results of a background check                 |
| /v1/PTA/{gtfs}                	| GET	| Return GTFS Feed for current region                                                       	|
| /v1/PTA/{gtfs-RT}             	| GET	| Return GTFS-RT Feed for this region                                                       	|
| /v1/PTA/{list}                	| GET	| Return closest PTA offers (stop or vehicle)                                               	|
| /v1/Negotiation/              	| GET	| Suggestion, negotiation, and acceptance of new pickup, waypoint, and drop-off location for passenger |
| /v1/rides/{rideId}/status     	| PATCH  | Update the status of a specific ride (e.g., start, end, pause, resume)                    	|
| /v1/users/{userId}/trips      	| GET	| Retrieve a number of trips for a specific user |
| /v1/analytics/rides           	| GET	| Retrieve analytics data about rides (e.g., total rides, average ride duration, popular routes) |
| /v1/notifications             	| GET	| Retrieve a list of notifications for a user                                               	|
| /v1/notifications             	| POST   | Create a new notification for a user                                                      	|
| /v1/notifications/{notificationId} | GET   | Retrieve a specific notification by ID                                                    	|
| /v1/notifications/{notificationId} | DELETE | Delete a specific notification by ID                                                      	|
| /v1/integrations/map          	| POST   | Integrate with a mapping service to provide accurate routing information                  	|
| /v1/integrations/public-transport | POST   | Integrate with public transport systems to combine carpooling with other transportation modes  |
| /v1/deals                		 | GET    | Retrieve a list of deals (paginated, filterable, sortable)                           		 |
| /v1/deals                		 | POST   | Create a new deal                                                                    		 |
| /v1/deals/{dealId}       		 | GET    | Retrieve a specific deal by ID                                                       		 |
| /v1/deals/{dealId}       		 | PUT    | Update a specific deal by ID                                                         		 |
| /v1/deals/{dealId}       		 | DELETE | Delete a specific deal by ID                                                         		 |
| /v1/promotions           		 | GET    | Retrieve a list of promotions (paginated, filterable, sortable)                      		 |
| /v1/promotions           		 | POST   | Create a new promotion                                                               		 |
| /v1/promotions/{promotionId} 	 | GET    | Retrieve a specific promotion by ID                                                  		 |
| /v1/promotions/{promotionId} 	 | PUT    | Update a specific promotion by ID                                                    		 |
| /v1/promotions/{promotionId} 	 | DELETE | Delete a specific promotion by ID                                                    		 |
| /v1/discounts            		 | GET    | Retrieve a list of discounts (paginated, filterable, sortable)                       		 |
| /v1/discounts            		 | POST   | Create a new discount                                                                		 |
| /v1/discounts/{discountId}   	 | GET    | Retrieve a specific discount by ID                                                   		 |
| /v1/discounts/{discountId}   	 | PUT    | Update a specific discount by ID                                                     		 |
| /v1/discounts/{discountId}   	 | DELETE | Delete a specific discount by ID                                                     		 |
| /v1/webhooks               	| POST   | Register a webhook for real-time updates                                	|

### User Authentication and Authorization

| Endpoint                 		 | Method | Description                                                                          		 |
|-----------------------------------|--------|-----------------------------------------------------------------------------------------------|
| /v1/auth/login           		 | POST   | Authenticate a user and generate a token                                             		 |
| /v1/auth/logout          		 | POST   | Log out a user and invalidate their token                                            		 |
| /v1/auth/refresh         		 | POST   | Refresh a user's token                                                               		 |
| /v1/auth/register        		 | POST   | Register a new user                                                                  		 |

### User Preferences and Settings

| Endpoint                 		 | Method | Description                                                                          		 |
|-----------------------------------|--------|-----------------------------------------------------------------------------------------------|
| /v1/user/preferences     		 | GET    | Retrieve the preferences and settings for the current user                           		 |
| /v1/user/preferences     		 | PUT    | Update the preferences and settings for the current user                             		 |
| /v1/user/preferences     		 | DELETE | Reset the preferences and settings for the current user                              		 |


[top](#table-of-contents)



## Notes

### Security and Privacy

- Strong authentication and authorization mechanisms (e.g., OAuth 2.0 or JWT) should be required to ensure secure access to the API.
- Encryption for sensitive data transmission and storage (e.g., HTTPS for API communication and encryption at rest for stored data) should be used.
- Adherence to privacy regulations like GDPR and CCPA, with clear guidelines for handling user data and obtaining user consent, is mandatory.

### Real-time Updates

- Support for real-time updates and notifications (e.g., WebSocket or server-sent events) to enable live tracking of rides, driver locations, and status changes.
- Push notifications for important events, such as ride requests, acceptances, and cancellations, should be provided.

### Geospatial

- APIs for geocoding, reverse geocoding, and distance calculations based on user locations and destinations should be available.

### Analytics and Reporting

- Endpoints and data structures for capturing and analyzing usage metrics (e.g., ride counts, popular routes, user demographics) should be included.
- APIs for generating reports and dashboards to help developers and businesses gain insights into their carpooling services should be provided.

### Integration

- Integration points with popular mapping and navigation services (e.g., Google Maps, OpenStreetMap) to provide accurate and up-to-date routing information should be offered.
- Integration with public transport systems to allow users to combine carpooling with other modes of transportation should be supported. Public transport companies should be able to make API requests to obtain match results for specific trips, including path, time, and additional information.

### General Requirements

- All endpoints should implement proper authentication, authorization, and security measures.
- Error handling and documentation should be provided for each endpoint.
- Pagination, filtering, and sorting should be supported where applicable.

[top](#table-of-contents)

### Changes

This document contains the updated version of the Open CarPool Standard (v1.0). The standard now includes several enhancements to support a wider range of mobility solutions and improve user experience. Key updates and additions include:

- **Social Features**: Added social features for matching users with similar interests or destinations.
- **Autonomous Level**: Included autonomous driving level in the `autopilot` field.
- **Sustainability Score**: Added a sustainability score for vehicles and rides.
- **Webhooks**: Added support for webhooks to enable real-time updates.
- **Background Check**: Added a field to indicate if a background check has been completed, including type and date.
- **Real-time Sharing**: Added real-time sharing of ride information with trusted contacts.
- **Emergency Contacts**: Added a field for emergency contacts to notify during a ride.

---

MIT License 2025 Norwegian Carpooling Embassy

[top](#table-of-contents)

---
