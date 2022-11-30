# Open CarPool Standard


## User
- #Traveler
- #IdUser
- #Name
- #mail
- #phone
- #picturelink

## Driver
- #driver@IdUser
- #driver@Name
- #driver@mail
- #driver@phone
- #driver@carId
- #driver@travpicturelink
- #any security here? hashed, verfified, Driving License confirmed? 

### Car
- #car@color
- #car@type
- #car@type@engine
- #car@insurance
- #car@capacity
- #car@capacity@reserved
- #car@plateID - or other means of verification


## Passenger
- #Passenger@IdUser
- #Passenger@Name
- #Passenger@mail
- #passenge@phone
- #Passenger@travpicturelink
- #any security here? hashed, verfified,?


## From
- #fromAreaId
- #fromAreaLocLatitude
- #fromAreaName
- #fromAreaDistkm -How far away from target


## Destination
- #DestinationAreaId
- #DestinationAreaLocaLatitude
- #DestinationAreaName
- #DestinationAreaDistkm -how far away from target accepted (in km)


## payment
- #paydeal - for deals (company/subscriptions etc)
- #paydealTime - for Time limited
- #paydealLoc - Locations based offer
- #paydealDist
- #paydealPassengerIdlookup
