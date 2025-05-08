 # Airbnb Clone 
## Overview

This project is a backend web application developed as a clone of Airbnb, designed to manage users, property listings, bookings, payments, and reviews. Built with Django, Django REST Framework, PostgreSQL, GraphQL, Celery, Redis, and Docker with CI/CD pipelines for smooth development and deployment workflows. it replicates core Airbnb features with a focus on performance, scalability, and reliability.

---
### 👥 Team Roles
* **__Backend Developer__**: Responsible for implementing API endpoints, database schemas, and business logic.
* **__Database Administrator__**: Manages database design, indexing, and optimizations.
* **__DevOps Engineer__**: Handles deployment, monitoring, and scaling of the backend services.
* **__QA Engineer__**: Ensures the backend functionalities are thoroughly tested and meet quality standards.
---

### 🛠️ Technology Stack
* **__Django__**: A high-level Python web framework used for building the RESTful API.
* **__Django REST Framework__**: Provides tools for creating and managing RESTful APIs.
* **__PostgreSQL__**: A powerful relational database used for data storage.
* **__GraphQL__**: Allows for flexible and efficient querying of data.
* **__Celery__**: For handling asynchronous tasks such as sending notifications or processing payments.
* **__Redis__**: Used for caching and session management.
* **__Docker__**: Containerization tool for consistent development and deployment environments.
* **__CI/CD Pipelines__**: Automated pipelines for testing and deploying code changes.
---
### 🗂️ Database Design 

The database is structured to reflect the core functionality of an Airbnb-like platform. Below are the key entities and their essential fields, along with the relationships between them.

#### 🧑 Users
- `id`: Unique identifier
- `username`: Unique username for login
- `email`: User's email address
- `password`: Hashed password
- `is_host`: Boolean to determine if the user can list properties

**Relationships**:
- A user can list multiple properties.
- A user can make multiple bookings.
- A user can leave multiple reviews.

---
#### 🏠 Properties
- `id`: Unique identifier
- `title`: Title of the property listing
- `description`: Detailed description
- `location`: Address or city
- `price_per_night`: Cost of staying per night

**Relationships**:
- Each property belongs to a host (user).
- A property can have multiple bookings.
- A property can have multiple reviews.

---

#### 📅 Bookings
- `id`: Unique identifier
- `user_id`: The user who made the booking
- `property_id`: The property being booked
- `start_date`: Check-in date
- `end_date`: Check-out date

**Relationships**:
- Each booking is made by a user.
- Each booking is for one property.

---

#### ✍️ Reviews
- `id`: Unique identifier
- `user_id`: Reviewer (user)
- `property_id`: The property being reviewed
- `rating`: Numeric rating (e.g., 1–5)
- `comment`: Textual feedback

**Relationships**:
- Each review is written by a user.
- Each review is for one property.

---

#### 💳 Payments
- `id`: Unique identifier
- `booking_id`: Associated booking
- `amount`: Total payment amount
- `payment_status`: Status (e.g., pending, completed)
- `payment_date`: Timestamp of payment

**Relationships**:
- Each payment is linked to a booking.
---
### Feature Breakdown
#### 👤 User Management
Handles user registration, login, and profile updates. Differentiates between guests and hosts, ensuring secure access and personalized functionality for each role.
___
#### 🏠 Property Management
Allows hosts to create, update, and manage property listings. Each property includes detailed information such as title, description, location, and price per night.
___
#### 📆 Booking System
Enables users to book available properties for specific dates. It also prevents overlapping bookings and provides a clear record of past and upcoming reservations.
___
#### 💳 Payment Processing
Processes payments securely for confirmed bookings. Integrates with a payment gateway and records transaction details and payment status.
___
#### ⭐ Review System
Allows guests to leave ratings and reviews for properties after their stay. Helps maintain trust and quality by giving feedback to hosts and aiding future guests in decision-making.
___
#### ⚙️ Asynchronous Task Handling
Uses Celery and Redis to manage background tasks like sending notifications and processing payments, improving app responsiveness and reliability.
___
#### 🚀 Deployment & DevOps
Leverages Docker for containerized development and production environments. CI/CD pipelines automate testing and deployment, ensuring smooth and consistent updates.

---
### API Security
Security is a critical component of this Airbnb Clone backend to protect sensitive user data, ensure safe transactions, and maintain trust in the platform. The following key measures will be implemented:

#### 🔑 Authentication
Token-based authentication (such as JWT or DRF’s TokenAuth) will be used to verify user identity. This ensures that only legitimate users can access protected resources and perform actions.

#### 🛡️ Authorization
Role-based access control (RBAC) will restrict actions based on user roles (e.g., guest vs. host). This prevents unauthorized access to data or features, such as preventing guests from editing property listings.

#### 📈 Rate Limiting
Rate limiting will be applied to prevent abuse of the API through excessive requests. This helps defend against brute-force attacks and protects server resources.

#### 🔒 Data Protection
Sensitive information such as passwords will be hashed, and payment data will be handled securely via third-party services. This ensures user credentials and financial data are protected from breaches.

#### 📬 Input Validation & Error Handling
All user input will be validated to prevent common vulnerabilities like SQL injection and XSS. Proper error handling will also prevent sensitive information from being exposed in responses.

---
### CI/CD Pipeline
CI/CD (Continuous Integration and Continuous Deployment) pipelines automate the process of testing, building, and deploying code. They help maintain code quality, catch bugs early, and ensure that new features or fixes are delivered quickly and reliably.

For this project, CI/CD pipelines are used to automatically run tests, build Docker containers, and deploy updates to the production environment. This ensures a smooth development workflow and reduces the chances of human error during deployment.

**Tools Used:**
- **GitHub Actions**: Automates testing and deployment workflows.
- **Docker**: Ensures consistent environments across development, testing, and production.

