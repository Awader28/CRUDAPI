# Avion API Documentation

## Base URL

`/upi`

## Endpoints

### 1. Create a New Flight

- **URL:** `/upi/avion`
- **Method:** `POST`
- **Description:** Creates a new flight.
- **Request Body:**
  ```json
  {
    "forigin": "String",
    "flayover": "String",
    "fdestination": "String",
    "fdistance": "Double",
    "ffuel": "Double",
    "fcraft": "String",
    "fintime": "String",
    "fouttime": "String"
  }
  ```
- **Response:**
  - **Status Code:** `200 OK`
  - **Body:** `"Flight Job Created"`

### 2. Get All Flights

- **URL:** `/upi/avion/all`
- **Method:** `GET`
- **Description:** Retrieves all flights.
- **Response:**
  - **Status Code:** `200 OK` if flights are found, `404 Not Found` if no flights are found.
  - **Body:**
    ```json
    [
      {
        "id": "Long",
        "forigin": "String",
        "flayover": "String",
        "fdestination": "String",
        "fdistance": "Double",
        "ffuel": "Double",
        "fcraft": "String",
        "fintime": "String",
        "fouttime": "String"
      }
    ]
    ```

### 3. Get Flights by Destination

- **URL:** `/upi/avion/destination`
- **Method:** `GET`
- **Description:** Retrieves flights by destination.
- **Query Parameter:** `fdestination` (String) - The destination to search for flights.
- **Response:**
  - **Status Code:** `200 OK` if flights are found, `404 Not Found` if no flights are found.
  - **Body:**
    ```json
    [
      {
        "id": "Long",
        "forigin": "String",
        "flayover": "String",
        "fdestination": "String",
        "fdistance": "Double",
        "ffuel": "Double",
        "fcraft": "String",
        "fintime": "String",
        "fouttime": "String"
      }
    ]
    ```

### 4. Update a Flight

- **URL:** `/upi/avion/{fid}`
- **Method:** `PUT`
- **Description:** Updates an existing flight by ID.
- **Path Parameter:** `fid` (Long) - The ID of the flight to update.
- **Request Body:**
  ```json
  {
    "forigin": "String",
    "flayover": "String",
    "fdestination": "String",
    "fdistance": "Double",
    "ffuel": "Double",
    "fcraft": "String",
    "fintime": "String",
    "fouttime": "String"
  }
  ```
- **Response:**
  - **Status Code:** `200 OK` if the flight is successfully updated, `404 Not Found` if the flight is not found.
  - **Body:** `"Flight updated successfully"` or `"Flight not found"`

### 5. Delete a Flight

- **URL:** `/upi/avion/{fid}`
- **Method:** `DELETE`
- **Description:** Deletes a flight by ID.
- **Path Parameter:** `fid` (Long) - The ID of the flight to delete.
- **Response:**
  - **Status Code:** `200 OK` if the flight is successfully deleted, `404 Not Found` if the flight is not found.
  - **Body:** `"Flight deleted successfully"` or `"Flight not found"`

## Example Requests

### Create a New Flight
```bash
curl -X POST "http://localhost:8080/upi/avion" -H "Content-Type: application/json" -d '{
  "forigin": "New York",
  "flayover": "London",
  "fdestination": "Paris",
  "fdistance": 5837.0,
  "ffuel": 2500.0,
  "fcraft": "Boeing 747",
  "fintime": "10:00",
  "fouttime": "14:00"
}'
```

### Get All Flights
```bash
curl -X GET "http://localhost:8080/upi/avion/all"
```

### Get Flights by Destination
```bash
curl -X GET "http://localhost:8080/upi/avion/destination?fdestination=Paris"
```

### Update a Flight
```bash
curl -X PUT "http://localhost:8080/upi/avion/1" -H "Content-Type: application/json" -d '{
  "forigin": "Los Angeles",
  "flayover": "Chicago",
  "fdestination": "Tokyo",
  "fdistance": 8700.0,
  "ffuel": 3000.0,
  "fcraft": "Airbus A380",
  "fintime": "15:00",
  "fouttime": "20:00"
}'
```

### Delete a Flight
```bash
curl -X DELETE "http://localhost:8080/upi/avion/1"
