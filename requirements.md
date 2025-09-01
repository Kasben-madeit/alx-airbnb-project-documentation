# Technical and Functional Requirements for ALX Airbnb Project

This document outlines the technical and functional requirements for the backend features of the ALX Airbnb Project.  
The features covered are:

- **User Authentication**  
- **Property Management**  
- **Booking System**

---

## 1. User Authentication

### Functional Requirements
- Users must be able to register with email, username, and password.  
- Users must be able to log in using their email and password.  
- Authentication must use JWT (JSON Web Tokens) for session management.  
- Passwords must be hashed before storage.  

### API Endpoints
- **POST** `/api/v1/auth/register`  
  - **Input:**  
    ```json
    { "username": "string", "email": "string", "password": "string" }
    ```
  - **Output:**  
    ```json
    { "id": "UUID", "username": "string", "email": "string", "token": "JWT" }
    ```

- **POST** `/api/v1/auth/login`  
  - **Input:**  
    ```json
    { "email": "string", "password": "string" }
    ```
  - **Output:**  
    ```json
    { "token": "JWT", "user": { "id": "UUID", "username": "string" } }
    ```

### Validation Rules
- Email must be unique and follow standard email format.  
- Password must be at least 8 characters, contain uppercase, lowercase, and a number.  
- Username must be between 3–20 characters and alphanumeric.  

### Performance Criteria
- Authentication requests must respond within **500ms** under normal load.  
- JWT tokens should expire after **24 hours**.  

---

## 2. Property Management

### Functional Requirements
- Hosts can create, update, delete, and list properties.  
- Each property must include title, description, location, price per night, and availability.  
- Properties must be associated with the host who created them.  

### API Endpoints
- **POST** `/api/v1/properties`  
  - **Input:**  
    ```json
    { "title": "string", "description": "string", "location": "string", "price_per_night": "float", "availability": "boolean" }
    ```
  - **Output:**  
    ```json
    { "id": "UUID", "title": "string", "host_id": "UUID" }
    ```

- **GET** `/api/v1/properties/{id}`  
  - **Output:**  
    ```json
    { "id": "UUID", "title": "string", "description": "string", "location": "string", "price_per_night": "float", "availability": "boolean" }
    ```

- **PUT** `/api/v1/properties/{id}`  
  - **Input:**  
    ```json
    { "title": "string", "description": "string", "price_per_night": "float", "availability": "boolean" }
    ```
  - **Output:**  
    ```json
    { "message": "Property updated successfully" }
    ```

- **DELETE** `/api/v1/properties/{id}`  
  - **Output:**  
    ```json
    { "message": "Property deleted successfully" }
    ```

### Validation Rules
- Price per night must be a positive number.  
- Location must not be empty.  
- Title must be between 5–100 characters.  

### Performance Criteria
- Property listing must support pagination for scalability.  
- Queries must return results within **1 second** for up to **1000 properties**.  

---

## 3. Booking System

### Functional Requirements
- Users must be able to book available properties.  
- A booking must include user ID, property ID, check-in date, check-out date, and total price.  
- The system must prevent double booking of properties.  

### API Endpoints
- **POST** `/api/v1/bookings`  
  - **Input:**  
    ```json
    { "property_id": "UUID", "check_in": "date", "check_out": "date" }
    ```
  - **Output:**  
    ```json
    { "id": "UUID", "property_id": "UUID", "user_id": "UUID", "total_price": "float" }
    ```

- **GET** `/api/v1/bookings/{id}`  
  - **Output:**  
    ```json
    { "id": "UUID", "property_id": "UUID", "user_id": "UUID", "check_in": "date", "check_out": "date", "total_price": "float" }
    ```

- **DELETE** `/api/v1/bookings/{id}`  
  - **Output:**  
    ```json
    { "message": "Booking canceled successfully" }
    ```

### Validation Rules
- Check-out date must be later than check-in date.  
- Booking cannot be made if property is not available.  
- Users cannot book their own property.  

### Performance Criteria
- Booking confirmation must complete within **1 second**.  
- The system must handle concurrent booking requests without race conditions.  

---
