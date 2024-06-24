# Project Title: MuleSoft COVID Case Management API

## Introduction
This project is a MuleSoft application designed to manage COVID case data. It provides endpoints to create, update, and retrieve COVID case information. The project is built using MuleSoft, leveraging various connectors and modules such as HTTP, Database, and DataWeave.

## Table of Contents
1. [Getting Started](#getting-started)
2. [Prerequisites](#prerequisites)
3. [Installation](#installation)
4. [Configuration](#configuration)
5. [Deployment](#deployment)
6. [Usage](#usage)
7. [Endpoints](#endpoints)
8. [Logging](#logging)
9. [Error Handling](#error-handling)
10. [Contributing](#contributing)
11. [License](#license)

## Getting Started
This section will help you get started with the MuleSoft COVID Case Management API.

## Prerequisites
- MuleSoft Anypoint Studio
- MySQL Database
- Java 8 or higher

## Installation
1. Clone the repository:
   ```bash
   git clone https://github.com/your-repo/mulesoft-covid-case-management.git
   ```
2. Open the project in Anypoint Studio.

## Configuration
1. Configure the MySQL database connection in `src/main/resources/mule-app.properties`:
   ```properties
   db.host=localhost
   db.port=3306
   db.user=root
   db.password=yourPassword
   db.name=mulesoft_tutorial
   ```
2. Set up the HTTP listener configuration in `src/main/mule/config.xml`:
   ```xml
   <http:listener-config name="HTTP_Listener_config" doc:name="HTTP Listener config" basePath="/learnmulesoft">
       <http:listener-connection host="0.0.0.0" port="6061" />
   </http:listener-config>
   ```

## Deployment
Deploy the application to CloudHub:
1. Right-click the project in Anypoint Studio.
2. Select `Anypoint Platform` -> `Deploy to CloudHub`.
3. Follow the deployment wizard to complete the process.

## Usage
The API exposes three main endpoints for managing COVID cases.

## Endpoints
1. **Create COVID Case (POST /v1/cases)**
   - Description: Registers a new COVID case.
   - Request: JSON payload with case details.
   - Response: JSON with the created case ID.
   
2. **Update COVID Case (PUT /v1/cases)**
   - Description: Updates an existing COVID case.
   - Request: JSON payload with updated case details.
   - Response: JSON with the updated case ID.
   
3. **Retrieve COVID Case (GET /v1/cases/{nationalID})**
   - Description: Retrieves details of a COVID case by national ID.
   - Request: Path parameter with national ID.
   - Response: JSON with case details.

### Example Requests
#### Create COVID Case
```bash
curl -X POST http://localhost:6061/learnmulesoft/v1/cases -H "Content-Type: application/json" -d '{
  "source": "UHIS",
  "case_type": "Confirmed",
  "first_name": "John",
  "last_name": "Doe",
  "phone": "1234567890",
  "email": "john.doe@example.com",
  "date_of_birth": "1980-01-01",
  "national_id": "AB123456",
  "national_id_type": "Passport",
  "street_address": "123 Main St",
  "city": "Anytown",
  "state": "AN",
  "postal": "12345",
  "country": "USA",
  "create_date": "2024-06-24",
  "update_date": "2024-06-24",
  "create_by": "UHIS",
  "update_by": "UHIS"
}'
```

#### Update COVID Case
```bash
curl -X PUT http://localhost:6061/learnmulesoft/v1/cases -H "Content-Type: application/json" -d '{
  "covidCase": {
    "caseID": "123",
    "source": "UHIS",
    "caseType": "Confirmed",
    "firstName": "John",
    "lastName": "Doe",
    "phone": "1234567890",
    "email": "john.doe@example.com",
    "dateOfBirth": "1980-01-01",
    "nationalID": "AB123456",
    "nationalIDType": "Passport",
    "address": {
      "streetAddress": "123 Main St",
      "city": "Anytown",
      "state": "AN",
      "postal": "12345",
      "country": "USA"
    }
  }
}'
```

#### Retrieve COVID Case
```bash
curl -X GET http://localhost:6061/learnmulesoft/v1/cases/AB123456
```

## Logging
The application logs significant events and errors:
- Start and end of each flow
- Transaction and correlation IDs
- Payload data

## Error Handling
The application includes error handling for various scenarios:
- Resource not found (404)
- Internal server errors (500)

## Contributing
We welcome contributions to this project. Please submit pull requests or raise issues for any improvements or bugs.

## License
This project is licensed under the MIT License - see the LICENSE file for details.
