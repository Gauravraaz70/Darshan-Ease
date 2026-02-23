🏗 DarshanEase – Technical Architecture

📌 Overview

DarshanEase follows a microservices-based architecture where each component performs a specific responsibility.
The system is divided into Frontend, Backend Services, and Database Layer to ensure scalability, security, and modularity.

🖥 1️⃣ User Interface (Frontend Layer)

Web-based interface for devotees.

Allows users to:

Explore darshan timings

Select preferred slots

Make bookings

View e-tickets

Communicates with backend through API Gateway.

👉 This layer ensures a smooth and user-friendly experience.

🌐 2️⃣ Web Server

Hosts the user interface.

Serves web pages to users.

Handles HTTP requests and responses.

Connects frontend with backend services.

🚪 3️⃣ API Gateway

Acts as a single entry point for all client requests.

Routes requests to appropriate backend services.

Provides:

Security

Load balancing

Request logging

Centralized control

👉 Improves system security and maintainability.

🔐 4️⃣ Authentication Service

Handles login and registration.

Generates secure authentication tokens (JWT).

Implements role-based access control:

Devotee

Organizer

Admin

Ensures secure access to protected services.

🗄 5️⃣ Database Layer

Stores persistent data such as:

User information

Darshan slots

Bookings

Payments

Tickets

Temple details

👉 Ensures reliable data storage and retrieval.

⚙ 6️⃣ Core Backend Services
🕉 Darshan Service

Manages darshan timings.

Maintains slot availability.

Updates special darshan schedules.

📅 Booking Service

Creates new bookings.

Updates or cancels bookings.

Maintains booking records.

🏛 Temple Service

Manages temple details.

Stores location and amenities.

Maintains access information.

🪑 Seat Service

Handles seat allocation.

Checks seat availability.

Prevents overbooking.

🎟 Ticket Service

Generates electronic tickets.

Creates digital booking records.

Supports QR code for verification.

🔄 System Flow (How It Works)

User interacts with User Interface.

Request goes to API Gateway.

API Gateway validates via Authentication Service.

Request is routed to:

Darshan Service

Booking Service

Temple Service

Seat Service

Ticket Service

Data is stored/retrieved from Database.

Summary:- “DarshanEase follows a microservices-based architecture. The system consists of a frontend interface hosted on a web server, connected to backend services through an API Gateway.
Authentication Service ensures secure access, while specialized services such as Darshan Service, Booking Service, Temple Service, Seat Service, and Ticket Service handle their respective functionalities.
All persistent data is stored in a centralized database.”

Response is sent back to user.


Task 2.

![image alt](https://github.com/Gauravraaz70/Darshan-Ease/blob/1385eb3f3ae5d5a32bb77ab3b7cfd4508d98f5f0/Er%20Diagram.png)


📌 Overview of the ER Diagram

The ER Diagram represents the database structure of the DarshanEase Temple Booking System.

It contains 4 main entities:

User

Booking

DarshanSlot

Temple

These entities are connected using primary keys (PK) and foreign keys (FK) to maintain relationships and data integrity.

🧩 1️⃣ User Entity
🔹 Attributes:

UserID (PK) → Unique identifier for each user

Name

Email

Phone

Address

🔹 Purpose:

Stores details of devotees who register and book darshan slots.

🔹 Relationship:

One User can make multiple Bookings

This is a One-to-Many (1:M) relationship.

User (1) -------- (M) Booking
🧩 2️⃣ Temple Entity
🔹 Attributes:

TempleID (PK) → Unique identifier for each temple

TempleName

Location

DarshanStartTime

DarshanEndTime

🔹 Purpose:

Stores general information about temples and their darshan timings.

🔹 Relationship:

One Temple can have multiple DarshanSlots

This is a One-to-Many (1:M) relationship.

Temple (1) -------- (M) DarshanSlot
🧩 3️⃣ DarshanSlot Entity
🔹 Attributes:

SlotID (PK) → Unique slot identifier

TempleID (FK) → References Temple

Date

StartTime

EndTime

AvailableSeats

Price

🔹 Purpose:

Represents individual bookable darshan time slots for a temple.

🔹 Relationships:

Each slot belongs to one Temple

One slot can have multiple Bookings

DarshanSlot (1) -------- (M) Booking
🧩 4️⃣ Booking Entity
🔹 Attributes:

BookingID (PK) → Unique booking identifier

UserID (FK) → References User

SlotID (FK) → References DarshanSlot

BookingDate

TotalAmount

🔹 Purpose:

Stores booking transactions made by users for specific darshan slots.

🔹 Relationships:

Each booking belongs to:

One User

One DarshanSlot

🔗 Complete Relationship Flow

The complete system flow is:

User → Booking → DarshanSlot → Temple

Meaning:

A User makes a Booking

A Booking is for a DarshanSlot

A DarshanSlot belongs to a Temple

🎯 Cardinality Summary
Relationship	Type
User → Booking	1 : M
Temple → DarshanSlot	1 : M
DarshanSlot → Booking	1 : M

There are no many-to-many relationships, which makes the schema simple and normalized.

