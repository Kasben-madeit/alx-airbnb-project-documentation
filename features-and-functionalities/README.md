# Airbnb Clone – Features and Functionalities

This document describes the core features and functionalities of the **Airbnb Clone Backend Application**.  
It serves as a **blueprint** for the system before development, ensuring clarity on what the backend should support.

---

## ✨ Core Features

### 1. User Management
- User registration and login with authentication (JWT-based).
- Roles: **Guest**, **Host**, and **Admin**.
- Profile management (name, email, phone, password).
- Secure password storage (bcrypt).

### 2. Property Management
- Hosts can list new properties.
- Edit and delete property listings.
- Properties contain: title, description, location, price, availability.
- Guests can search and filter properties (by location, price, rating).

### 3. Booking System
- Guests can book available properties.
- View and manage booking history.
- Booking statuses: **pending**, **confirmed**, **canceled**.
- Hosts can approve or reject bookings.

### 4. Payments
- Secure payment processing (Stripe, PayPal, etc.).
- Record transactions for each booking.
- Payment statuses: **completed**, **pending**, **refunded**.
- Support for cancellation refunds.

### 5. Reviews & Ratings
- Guests can leave reviews after stays.
- Ratings scale from **1 to 5**.
- Hosts can respond to reviews.
- Reviews are linked to verified bookings.

### 6. Messaging
- Direct messaging between Guests and Hosts.
- Inbox for each user.
- Timestamps for messages.

### 7. Admin Features
- Manage users (suspend, promote roles).
- Manage properties and bookings.
- Oversee payments and disputes.
- Generate platform-wide analytics.

---

## 🔧 Supporting Features
- API error handling and validation.
- Rate limiting and logging.
- Database indexing for performance optimization.
- Environment-based configuration (secure `.env`).

---

## 📊 Features Diagram

The diagram below illustrates the main modules of the Airbnb Clone backend:

📌 See the attached diagram: **`abnb.png`**

---

## ✅ Summary

This document provides the **high-level feature list** for the Airbnb Clone backend.  
It will serve as the foundation for future tasks such as **use case diagrams, user stories, data flow diagrams, and API specifications**.
