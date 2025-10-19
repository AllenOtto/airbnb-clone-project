# AirBNB Clone Project

The Airbnb Clone Project is a comprehensive, real-world application designed to simulate the development of a robust booking platform like Airbnb. It involves a deep dive into full-stack development, focusing on backend systems, database design, API development, and application security.

## Project Goals

By completing this project, learners will:

- Master collaborative team workflows using GitHub.
- Deepen their understanding of backend architecture and database design principles
- Implement advanced security measures for API development.
- Gain proficiency in designing and managing CI/CD pipelines for efficient deployment
- Strengthen their ability to document and plan complex software projects effectively
- Develop an understanding of integrating technologies like Django, MySQL, and GraphQL in a unified ecosystem

### Tech Stack

To complete this project, the student must:

- Have a GitHub account to create and manage repositories.
- Be familiar with Markdown syntax for README.md file creation.
- Possess prior experience with backend frameworks like Django and database systems such as MySQL.
- Understand software development lifecycle practices, including security, CI/CD, and database design.
- Be comfortable with modern tools such as Docker, GitHub Actions, or similar CI/CD platforms.

### Team Roles

1. ** Business Analyst (BA) **

Description: Bridges the gap between business needs and technical implementation

** Responsibilities **

- Understands the client’s business processes and workflows
- Translates abstract business ideas into clear, actionable software requirements

2. ** Product Owner (PO) **

The visionary and primary decision-maker for the product

** Responsibilities **

- Defines and communicates the product vision and strategy
- Manages the product backlog (prioritizing features based on value)

3. ** Project Manager (PM) **

Oversees delivery, timelines, budget, and team coordination

** Responsibilities **

- Ensures the product (or phase) is delivered on time and within budget
- Plans work, assigns tasks, and tracks progress

4. UI/UX Designer

Shapes how users interact with and experience the product

** Responsibilities **

- UX Designer: Conducts user research, creates personas, designs user journeys, wireframes, and prototypes
- UI Designer: Crafts visually appealing, intuitive, and responsive interfaces
- Together, they ensure the product is usable, engaging, and goal-oriented

### Technology Stack

1. ** Github **

GitHub is a cloud-based platform for hosting and managing Git repositories. It enables developers to:

- Collaborate via pull requests, code reviews, and issue tracking
- Integrate with CI/CD tools (like GitHub Actions) for automated workflows

2. ** Django **

Django is a high-level Python-based backend web framework that follows the "batteries-included" philosophy. Its role includes:

- Rapidly building secure, scalable web applications with built-in features (ORM, authentication, admin panel)
- Structuring backend logic, handling HTTP requests, and connecting to databases
- Enforcing best practices like MVC (Model-View-Template) architecture

3. ** MySQL **

MySQL is a widely used relational database management system (RDBMS). In development projects, it:

- Stores structured application data (e.g., users, transactions, settings) in tables with defined schemas
- Supports complex queries, transactions, and data integrity through SQL
- Integrates with backend frameworks (like Django) via ORMs to persist and retrieve data reliably

4. ** Docker **

Docker is a containerization platform that packages applications and their dependencies into isolated, portable containers. Its role includes:

- Ensuring consistent environments across development, testing, and production ("it works on my machine" problem solved)
- Simplifying deployment and scaling of microservices or monolithic apps
- Enabling reproducible builds and easy integration with CI/CD pipelines

5. ** Github Actions **

GitHub Actions is a CI/CD (Continuous Integration/Continuous Delivery) service built into GitHub. It allows teams to:   

- Automate workflows such as testing, building, and deploying code whenever changes are pushed
- Run test suites on multiple OS/runtime configurations.
- Publish packages or deploy to cloud platforms automatically

6. ** PostgreSQL **

PostgreSQL is an advanced, open-source relational database system known for its reliability, extensibility, and compliance with SQL standards. In development projects, it:

- Stores structured and semi-structured data (including JSON)
- Supports complex queries, transactions, and ACID compliance

7. ** GraphQL **

GraphQL is a query language and runtime for APIs that allows clients to request exactly the data they need—nothing more, nothing less. Its role in development includes:

- Replacing or complementing REST APIs with more flexible, efficient data fetching
- Reducing over-fetching and under-fetching of data
- Enabling frontend teams to iterate faster without waiting for backend changes

### Database Design

1. ** User **

Represents anyone using the platform—both guests and hosts.

Important Fields:   

- id (primary key)  
- email (unique, for login)  
- first_name, last_name  
- phone_number  
- user_type 

Relationships:   

- A User can be a host who owns multiple Properties.  
- A User (as a guest) can create multiple Bookings.  
- A User can write multiple Reviews (as a guest for properties, or as a host for guests).

2. ** Property **

Represents a bookable listing (e.g. apartment) owned by a host.
Important Fields:   

- id (primary key)  
- title (e.g., “Cozy Downtown Loft”)  
- description  
- location (city, country, or geocoordinates)  
- price_per_night  
- host_id (foreign key → User.id)
     

Relationships:   

- A Property belongs to one User (the host).  
- A Property can have multiple Bookings.  
- A Property can receive multiple Reviews from guests.  
- Property may be associated with multiple Payments (via bookings)

** 3. Booking **

Represents a reservation made by a guest for a property over a date range.
Important Fields:   

- id (primary key)  
- property_id (foreign key → Property.id)  
- guest_id (foreign key → User.id)  
- check_in_date  
- check_out_date  
- total_price  
- status (e.g., “confirmed”, “cancelled”, “completed”)
     

Relationships:   

- A Booking belongs to one Property and one Guest (User).  
- A Booking triggers one or more Payments.  
- A completed Booking may lead to a Review from the guest.

** 4. Review **

Represents feedback from a guest about a property (and optionally, from a host about a guest).
Important Fields:   

- id (primary key)  
- property_id (foreign key → Property.id)  
- reviewer_id (foreign key → User.id)  
- rating (e.g., 1–5 stars)  
- comment  
- created_at
     

Relationships:   

- A Review is about one Property and written by one User (guest).  
- A Property can have many Reviews.  
- Host reviews of guests can be modeled similarly with a reviewee_id

5. Payment

Represents a financial transaction for a booking.
Important Fields:   

- id (primary key)  
- booking_id (foreign key → Booking.id)  
- payer_id (foreign key → User.id)  
- amount  
- payment_method (e.g., “credit_card”, “mobile_money”)  
- status (e.g., “pending”, “completed”, “failed”)  
- transaction_id (from payment gateway)
     

Relationships:   

- A Payment is linked to one Booking and one User (the payer).  
- A Booking typically has one primary Payment, though partial or split payments could be supported.  
- Payments are tied to the financial lifecycle of a booking.
     