# The Open Carpool standard

We are trying to make reference/guide standard for carpooling

The standard will remain open for all to use, improve, and implement.

Feel free to help out:~~[OpenCarPoolStandard](OpenCarPoolStandard0.1.md)~~
                

### Inspiration and similar: 
* https://github.com/TOMP-WG/TOMP-API
* https://github.com/openmobilityfoundation/mobility-data-specification/tree/main#about

### Todo
- [x] Find license ([MIT](https://github.com/Norsk-institutt-for-samkjoring/Standard/blob/main/LICENSE))
- [ ] Create all possible tags
- [ ] Connect with APIs

### Contributors
* Norwegian carpool embassy / Norsk institutt for samkjøring -> with help from AI's

Layout could be like this:
```
ridesharing-standard/
├── README.md
├── ride.md
├── car.md
├── driver.md
├── passenger.md
├── payment.md
├── examples/
│   ├── ride_start.json
│   ├── ride_end.json
│   └── car_info.json
└── schemas/
	├── ride.json
	├── car.json
	├── driver.json
	├── passenger.json
	└── payment.json
```


Code from https://github.com/Norsk-institutt-for-samkjoring/Standard/blob/main/standard02.json
Work in progress for 0.3, feel free to help out..
```
{
  "ride": {
    "ride_id": "string",
    "start_time": "string",
    "end_time": "string",
    "start_location": {
      "latitude": "number",
      "longitude": "number"
    },
    "end_location": {
      "latitude": "number",
      "longitude": "number"
    },
    "estimated_duration": "number",
    "estimated_distance": "number",
    "actual_duration": "number",
    "actual_distance": "number",
    "driver_id": "string",
    "car_id": "string",
    "passengers": [
      {
        "passenger_id": "string",
        "seat_number": "number"
      }
    ],
    "status": "string",
    "fare": {
      "base_fare": "number",
      "distance_fare": "number",
      "time_fare": "number",
      "surge_multiplier": "number",
      "total_fare": "number"
    }
  },
  "car": {
    "car_id": "string",
    "make": "string",
    "model": "string",
    "year": "number",
    "color": "string",
    "license_plate": "string",
    "capacity": "number",
    "amenities": [
      "string"
    ]
  },
  "driver": {
    "driver_id": "string",
    "name": "string",
    "contact_details": {
      "phone": "string",
      "email": "string"
    },
    "profile_picture": "string",
    "license_number": "string",
    "background_check": "boolean",
    "ratings": {
      "average_rating": "number",
      "total_ratings": "number"
    },
    "reviews": [
      {
        "passenger_id": "string",
        "rating": "number",
        "comment": "string"
      }
    ]
  },
  "passenger": {
    "passenger_id": "string",
    "name": "string",
    "contact_details": {
      "phone": "string",
      "email": "string"
    },
    "preferences": {
      "car_type": "string",
      "chat_availability": "boolean"
    },
    "ratings": {
      "average_rating": "number",
      "total_ratings": "number"
    },
    "reviews": [
      {
        "driver_id": "string",
        "rating": "number",
        "comment": "string"
      }
    ]
  },
  "payment": {
    "payment_id": "string",
    "ride_id": "string",
    "passenger_id": "string",
    "payment_method": "string",
    "fare_breakdown": {
      "base_fare": "number",
      "distance_fare": "number",
      "time_fare": "number",
      "surge_multiplier": "number",
      "total_fare": "number"
    },
    "status": "string"
  }
}
```

This code file includes the following components:
```
ride: Represents a single ridesharing trip, including details such as ride ID, start and end times, locations, estimated and actual duration and distance, driver and car information, passenger details, ride status, and fare breakdown.
car: Contains information about the car used for the ride, including car ID, make, model, year, color, license plate, seating capacity, and available amenities.
driver: Represents the driver of the ridesharing car, including driver ID, name, contact details, profile picture, license number, background check status, ratings, and reviews.
passenger: Represents a passenger in the ridesharing car, including passenger ID, name, contact details, preferences (e.g., preferred car type, chat availability), ratings, and reviews.
payment: Contains payment information for the ride, including payment
```


