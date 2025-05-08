 # Airbnb Clone 
## Overview

This project is a backend web application developed as a clone of Airbnb, designed to manage users, property listings, bookings, payments, and reviews. Built with Django, Django REST Framework, PostgreSQL, GraphQL, Celery, Redis, and Docker with CI/CD pipelines for smooth development and deployment workflows. it replicates core Airbnb features with a focus on performance, scalability, and reliability.


### 👥 Team Roles
* **__Backend Developer__**: Responsible for implementing API endpoints, database schemas, and business logic.
* **__Database Administrator__**: Manages database design, indexing, and optimizations.
* **__DevOps Engineer__**: Handles deployment, monitoring, and scaling of the backend services.
* **__QA Engineer__**: Ensures the backend functionalities are thoroughly tested and meet quality standards.


### 🛠️ Technology Stack
* **__Django__**: A high-level Python web framework used for building the RESTful API.
* **__Django REST Framework__**: Provides tools for creating and managing RESTful APIs.
* **__PostgreSQL__**: A powerful relational database used for data storage.
* **__GraphQL__**: Allows for flexible and efficient querying of data.
* **__Celery__**: For handling asynchronous tasks such as sending notifications or processing payments.
* **__Redis__**: Used for caching and session management.
* **__Docker__**: Containerization tool for consistent development and deployment environments.
* **__CI/CD Pipelines__**: Automated pipelines for testing and deploying code changes.

### Database Design 

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









