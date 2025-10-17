# airbnb-clone-project
Overview

  The Airbnb Clone Project is a full-stack web application built using Django, Django REST Framework, PostgreSQL, GraphQL, Celery, Redis, Docker, and CI/CD Pipelines. It replicates core core Airbnb features and focuses on backend development, database design, API creation, and security.

Technology Stack
  1. Django	- Web framework for building applications in Python
  2. Django REST Framework - Provides tools for creating and managing RESTful APIs.
  3. PostgreSQL	- Database for storing data
  4. GraphQL	- Efficient query language for APIs
  5. Celery	- Runs background tasks asynchronously
  6. Redis	- Fast cache and message broker
  7. Docker	- Runs apps in isolated containers
  8. CI/CD Pipelines	- Automate testing and deployment

Team Roles
  1. Backend Developer - Builds and maintains server-side logic, APIs, and integrations.
  2. Database Administrator - Design, manages and optimizes the database for performance and           reliability. 
  3. DevOps Engineer - Responsible for handling the project's deployment, monitoring, and scaling of backend services.
  4. QA Engineer -  Ensures that backend functionalities are thoroughly tested and meet quality standards.


Database Design
  Key Entities
  A. Users
    a. Fields:
      •	id – Unique identifier for each user.
      •	username – The user’s chosen display name.
      •	email – Used for login and communication.
      •	password – Encrypted password for authentication.
      •	is_host – Boolean indicating whether the user can list properties.
    b. Relationships:
      •	A User can list multiple Properties.
      •	A User can make multiple Bookings.
      •	A User can leave multiple Reviews.
  
  B. Properties
    a. Fields:
      •	id – Unique identifier for each property.
      •	host_id – References the user who owns the property.
      •	title – Name or short description of the property.
      •	location – Address or city where the property is located.
      •	price_per_night – Cost of renting the property per night.
    b. Relationships:
      •	A Property belongs to one User (the host).
      •	A Property can have multiple Bookings.
      •	A Property can receive multiple Reviews.
    
  C. Bookings
    a. Fields:
      •	id – Unique identifier for each booking.
      •	user_id – References the user who made the booking.
      •	property_id – References the property being booked.
      •	check_in – Date the booking starts.
      •	check_out – Date the booking ends.
      •	status – Indicates booking status (e.g., confirmed, canceled).
    b. Relationships:
      •	A Booking belongs to one User and one Property.
      •	A Booking can have one Payment.

  D. Payments
    a. Fields
      •	id – Unique identifier for each payment.
      •	booking_id – References the associated booking.
      •	amount – Total amount paid.
      •	payment_method – Type of payment (e.g., credit card, PayPal).
      •	status – Indicates whether the payment was successful or pending.
    b. Relationships:
          •	A Payment belongs to one Booking.
      •	A Booking can have one Payment.
  
   E. Reviews
    a. Fields:
      • id – Unique identifier for each review.
      •. user_id – References the reviewer.
      •. property_id – References the reviewed property.
      •.	rating – Numeric rating (e.g., 1–5).
      •. comment – Textual feedback from the user.
    b. Relationships:
      •	A Review belongs to one User and one Property.
      •	A Property can have multiple Reviews.
  
Feature Breakdown
  1. User Management
     Handles user registration, authentication, and profile management for guests and hosts. It ensures secure access and role-based functionality across the platform.
     
  2. Property Management
     Allows hosts to create, update, and delete property listings. This feature maintains accurate details such as descriptions, prices, and locations for easy discovery by users.
   
  3. Booking System
     Enables users to reserve properties based on availability. It manages booking dates, check-in/check-out details, and prevents overlapping reservations.
   
  4. Payment Processing
     Supports secure transactions between guests and hosts. It verifies payments, records transaction data, and ensures financial reliability in the booking process.

  5. Review System
     Lets users share feedback and rate properties after their stay. This builds trust, helps hosts improve, and enhances user experience.

  6. Data Optimization
    Enhances performance through caching, indexing, and optimized database queries. It ensures faster response times and efficient data management.


API Security
  1.	Authentication
    •  Uses secure methods (e.g., JWT or OAuth2) to verify user identity before granting access to APIs.
    •  mportance: Prevents unauthorized users from accessing sensitive features such as bookings, payments, or user profiles.
  3.	Authorization
      •  Controls what authenticated users can do (e.g., hosts can add properties, guests can make bookings).
    	•  Importance: Ensures that users can only perform actions they are permitted to, protecting both user and system integrity.
  4.	Rate Limiting
      •  Restricts the number of API requests a user or client can make in a given time frame.
      •  Importance: Prevents abuse, such as denial-of-service (DoS) attacks, and ensures fair resource usage.
  5.	Data Encryption
      •  Uses HTTPS (SSL/TLS) and database encryption to protect sensitive data during transmission and storage.
    	•  Importance: Keeps user credentials, payment details, and personal information safe from interception.
  7.	Input Validation & Sanitization
      •  Validates incoming data and removes malicious inputs before processing.
      •  Importance: Protects the system from common web vulnerabilities such as SQL injection and cross-site scripting (XSS).
  8.	Secure Payment Handling
       •	Ensures payment transactions are processed through trusted gateways with encrypted connections.
       •  Importance: Protects financial data and maintains user trust during payment processing.
  
  
    
      
