# CategoryService

## Overview
The **CategoryService** is a microservice responsible for managing categories used across various parts of the system, such as Banking, Expenses, and Budget services. It provides a centralized API for creating, updating, retrieving, and marking categories as inactive. The service is designed to be simple and efficient, leveraging Spring Boot and MongoDB.

---

## Features
- **CRUD Operations**:
  - Create, read, update, and delete (soft delete) categories.
- **Soft Delete Mechanism**:
  - Categories can be marked as inactive but remain visible for historical data in other services.
- **Scalability**:
  - Can be integrated with Kafka for event-driven synchronization across other microservices.

---

## Technologies Used
- **Spring Boot**:
  - Framework for building REST APIs.
- **MongoDB**:
  - NoSQL database for flexible and efficient data storage.
- **Docker**:
  - For containerization and easy deployment.
- **GitHub Actions**:
  - For CI/CD pipeline automation (future addition).

---

## API Endpoints

### Base URL
```
/api/v1/categories
```

### 1. Create a Category
- **Method**: `POST`
- **Endpoint**: `/`
- **Request Body**:
  ```json
  {
    "name": "Food"
  }
  ```
- **Response**:
  ```json
  {
    "id": "123abc",
    "name": "Food",
    "active": true
  }
  ```

### 2. Get All Categories
- **Method**: `GET`
- **Endpoint**: `/`
- **Response**:
  ```json
  [
    {
      "id": "123abc",
      "name": "Food",
      "active": true
    },
    {
      "id": "456def",
      "name": "Rent",
      "active": false
    }
  ]
  ```

### 3. Update a Category
- **Method**: `PUT`
- **Endpoint**: `/{id}`
- **Request Body**:
  ```json
  {
    "name": "Housing"
  }
  ```
- **Response**:
  ```json
  {
    "id": "123abc",
    "name": "Housing",
    "active": true
  }
  ```

### 4. Delete a Category (Soft Delete)
- **Method**: `DELETE`
- **Endpoint**: `/{id}`
- **Response**:
  ```json
  {
    "id": "123abc",
    "name": "Food",
    "active": false
  }
  ```

---

## Database Schema
### MongoDB Collection: `categories`
```json
{
  "id": "123abc",
  "name": "Food",
  "active": true
}
```

---

## Future Enhancements
1. **Integration with Kafka**:
   - Publish events for category creation, updates, and deletions.
2. **Authentication and Authorization**:
   - Secure the API endpoints with JWT.
3. **CI/CD Pipeline**:
   - Automate build, test, and deployment with GitHub Actions.
4. **Validation Rules**:
   - Ensure category names are unique and follow naming conventions.

---

## Running the Service
### Prerequisites
- Java 17+
- MongoDB (local or Dockerized)
- Maven

### Steps
1. Clone the repository:
   ```bash
   git clone https://github.com/your-repo/CategoryService.git
   ```
2. Navigate to the project directory:
   ```bash
   cd CategoryService
   ```
3. Start MongoDB:
   ```bash
   docker run -d -p 27017:27017 --name mongo mongo:latest
   ```
4. Run the application:
   ```bash
   ./mvnw spring-boot:run
   ```

---

## Contributing
1. Fork the repository.
2. Create a new branch for your feature or bug fix.
3. Commit your changes and open a pull request.

---

## License
This project is licensed under the MIT License.

