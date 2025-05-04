# Airbnb Clone Project

## Project Overview
The Airbnb Clone Project is a backend system designed to simulate the functionality of Airbnb. It handles user registration, property listings, bookings, payments, and reviews. This real-world application emphasizes clean architecture, API design, database management, and collaborative development practices.

## Project Goals
- Implement secure user management and authentication
- Develop property listing and booking features
- Integrate payment and review systems
- Ensure performance through caching and database indexing
- Use modern DevOps practices including CI/CD pipelines

## Tech Stack
- **Framework**: Django
- **API**: Django REST Framework & GraphQL
- **Database**: PostgreSQL (or MySQL)
- **Caching**: Redis
- **Async Tasks**: Celery
- **Containerization**: Docker
- **CI/CD**: GitHub Actions


## 👥 Team Roles
### Backend Developer
Designs and implements the backend logic, APIs, and integrations. Ensures secure, scalable, and maintainable backend services.
### Database Administrator (DBA)
Designs, optimizes, and maintains the project’s relational database schema. Responsible for performance tuning and data integrity.
### DevOps Engineer
Sets up and manages CI/CD pipelines, containerization, and cloud deployments. Ensures system reliability and scalability.
### QA Engineer
Tests backend functionalities, identifies bugs, and ensures quality through automated and manual testing strategies.
### Technical Writer (Optional)
Documents APIs, system architecture, workflows, and user guides. Ensures clarity and accessibility of technical documentation.

## Technology Stack
This project uses a modern and scalable technology stack to deliver a high-performance backend application.
- **Django**: A high-level Python web framework used to build the core backend logic and structure the application using the MVC (Model-View-Controller) pattern.
- **Django REST Framework (DRF)**: A powerful toolkit for building RESTful APIs with Django. It simplifies the process of serialization, authentication, and CRUD operations.
- **GraphQL**: A flexible query language that allows clients to request exactly the data they need. Used alongside REST APIs to support more dynamic data retrieval.
- **PostgreSQL**: A robust, open-source relational database used to store structured data such as users, properties, bookings, and reviews.
- **MySQL**: An alternative RDBMS option, mentioned for flexibility in deployment environments. Can be used interchangeably with PostgreSQL if preferred.
- **Redis**: An in-memory data store used for caching and session management, improving performance by reducing database load.
- **Celery**: A task queue system used to manage background tasks such as sending confirmation emails or processing payments asynchronously.
- **Docker**: A containerization platform used to package the application and its dependencies for consistent deployment across development, staging, and production environments.
- **GitHub Actions**: A CI/CD automation tool used to run tests, lint code, and deploy the application automatically on code pushes or pull requests.

## Database Design

The database is designed using a relational model to ensure data integrity and enable complex relationships between entities. Below are the core entities and their attributes:

### Users
Represents both guests and hosts on the platform.
- `id`: Unique identifier
- `name`: Full name of the user
- `email`: Email address (unique)
- `password_hash`: Securely stored password
- `is_host`: Boolean indicating whether the user is a host

### Properties
Represents accommodations listed by hosts.
- `id`: Unique identifier
- `title`: Title of the property listing
- `description`: Detailed description of the property
- `location`: Address or geographic location
- `host_id`: Foreign key referencing the User who owns the property

### Bookings
Represents a reservation made by a user for a property.
- `id`: Unique identifier
- `user_id`: Foreign key referencing the guest (User)
- `property_id`: Foreign key referencing the booked property
- `check_in`: Date of check-in
- `check_out`: Date of check-out

### Payments
Represents payment transactions for bookings.
- `id`: Unique identifier
- `booking_id`: Foreign key referencing the related booking
- `amount`: Total amount paid
- `payment_method`: e.g., credit card, PayPal
- `payment_status`: e.g., paid, pending, failed

### Reviews
Represents user feedback for properties after a stay.
- `id`: Unique identifier
- `user_id`: Foreign key referencing the reviewer (User)
- `property_id`: Foreign key referencing the reviewed property
- `rating`: Numeric rating (e.g., 1–5)
- `comment`: Text review

### Entity Relationships
- A **User** can create multiple **Properties** (if they are a host).
- A **User** can make multiple **Bookings**.
- Each **Booking** is linked to one **Property** and one **User**.
- Each **Booking** has one **Payment**.
- A **User** can leave multiple **Reviews**, each tied to a specific **Property**.

## Feature Breakdown

### User Management
This feature allows users to register, authenticate, and manage their profiles. It ensures secure login and password management, enabling both guests and hosts to interact with the platform effectively. The authentication system is built with security best practices to safeguard user data.

### Property Management
Hosts can create, update, retrieve, and delete property listings. This feature enables them to add important details such as location, description, and pricing, providing a seamless experience for hosts to showcase their properties. Guests can easily browse available properties.

### Booking System
The booking system allows users to make, update, and manage bookings for properties. It tracks essential details such as check-in and check-out dates, ensuring users can reserve their stays seamlessly. It also ensures availability and prevents double-booking by integrating with the property database.

### Payment Processing
This feature handles transactions for bookings, including payment collection and status updates. It integrates with a payment gateway to securely process credit card or alternative payments. Payments are linked directly to bookings, and the system can manage various payment statuses (e.g., pending, successful).

### Review System
Guests can leave reviews and ratings for properties after their stay. This feature helps build trust within the platform, as potential guests can evaluate the property based on previous users' experiences. Reviews include both numerical ratings and detailed comments.

### Database Optimizations
The database is optimized for high performance and scalability. Caching and indexing strategies are implemented to speed up data retrieval, ensuring the platform can handle large volumes of users, properties, and bookings without slowdowns.
