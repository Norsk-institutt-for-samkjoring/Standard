# Open CarPool Standard



## User

 `user`      | Description                                            |
| ----------------- | ------------------------------------------------------ |
| `Traveler`           | Pedal or foot propulsion                               |
| `#IdUser` | Provides power only alongside human propulsion         |
| `Name`        | Contains throttle mode with a battery-powered motor    |
| ` #phone`      | Contains throttle mode with a gas engine-powered motor |
| ` #phone`      | Contains throttle mode with a gas engine-powered motor |
| ` #picturelink`      | Contains throttle mode with a gas engine-powered motor |

- #Traveler
- #IdUser
- #Name
- #mail
- #phone
- #picturelink

[Top][toc]


## Driver
- #driver@IdUser
- #driver@Name
- #driver@mail
- #driver@phone
- #driver@carId
- #driver@travpicturelink
- #any security here? hashed, verfified, Driving License confirmed? 

[Top][toc]

### Car
- #car@color
- #car@type
- #car@type@engine
- #car@insurance
- #car@capacity
- #car@capacity@reserved
- #car@plateID - or other means of verification

[Top][toc]

## Passenger
- #Passenger@IdUser
- #Passenger@Name
- #Passenger@mail
- #passenge@phone
- #Passenger@travpicturelink
- #any security here? hashed, verfified,?

[Top][toc]

## From
- #fromAreaId
- #fromAreaLocLatitude
- #fromAreaName
- #fromAreaDistkm -How far away from target

[Top][toc]

## Destination
- #DestinationAreaId
- #DestinationAreaLocaLatitude
- #DestinationAreaName
- #DestinationAreaDistkm -how far away from target accepted (in km)

[Top][toc]

## payment
- #paydeal - for deals (company/subscriptions etc)
- #paydealTime - for Time limited
- #paydealLoc - Locations based offer
- #paydealDist
- #paydealPassengerIdlookup

[Top][toc]
