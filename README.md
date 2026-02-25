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


Task 3 

🌸 DARSHAN EASE – System Features
1️⃣ Devotee Module (User Side)
🔐 1. Devotee Registration & Authentication

Users can create an account with name, email, phone, password.

Secure login using JWT authentication.

Password encryption using bcrypt.

Forgot password & email verification (optional enhancement).

🏛 2. Darshan Listings
4

Displays:

Temple Name

Location

Darshan Date

Start Time & End Time

Available Slots

Filters:

By Date

By Temple

By Availability

🛕 3. Temple Selection

Shows detailed temple information:

Location (City, State)

Description

Special Darshan types (VIP, General, Festival)

Example temples you can use for demo:

Tirupati Balaji Temple

Kashi Vishwanath Temple

Vaishno Devi Temple

⏳ 4. Slot Selection

Devotee selects:

Date

Time slot

Number of devotees

System checks:

Real-time availability

Maximum slot capacity

🎟 5. Ticket Booking

Booking includes:

Booking ID (Auto Generated)

Temple ID

Slot ID

Number of devotees

Total Amount

Status:

Confirmed

Cancelled

Pending

💳 6. Donation Integration

Integrate payment gateway:

Razorpay / Stripe (for demo)

Payment for:

Ticket amount

Optional donation

Secure transaction handling.

📧 7. Booking Confirmation

After successful payment:

Confirmation Page

Email with:

Booking ID

Temple Name

Date & Time

QR Code (Optional)

📜 8. Booking History

Users can:

View past bookings

View upcoming bookings

Cancel booking (before cutoff time)

Download ticket (PDF)

2️⃣ Organizer Module (Temple Side)
🖥 Organizer Dashboard
4

Organizer can:

Add temple details

Create darshan slots

Set slot capacity

Monitor bookings

Issue manual tickets (if required)

🗂 Darshan Slot Management

Organizer can:

Create slots (Date + Start Time + End Time)

Update capacity

Close slot

View booked count

3️⃣ Admin Module (System Level)
🛠 Admin Dashboard

Admin controls:

Users

Organizers

Temples

Slots

Bookings

Admin has full CRUD access.

📊 Reporting & Analytics

Total bookings per temple

Popular darshan timings

Daily / Monthly revenue

Devotee demographics

Cancellation ratio

Charts:

Bar Graph → Temple Popularity

Line Chart → Booking Trends

Pie Chart → Slot Distribution

4️⃣ System-Level Features
🔄 Real-Time Slot Availability

When booking happens:

Slot capacity decreases

When cancellation:

Slot capacity increases

Use:

MongoDB transactions

or Optimistic locking

🌐 Integration with External APIs

Temple information APIs

Payment Gateway API

Email Service (SendGrid / NodeMailer)

SMS API (Optional)

🔷 Complete Feature Categorization (For Viva)
Layer	Features
Frontend	Temple listing, slot selection, booking UI
Backend	Authentication, slot management, booking logic
Database	Users, Temples, Slots, Bookings, Payments
Security	JWT, Password Hashing
Payment	Razorpay/Stripe
Admin Control	Dashboard, reports, management

Task 4


🌸 DARSHAN EASE – Roles and Responsibilities

The DarshanEase system consists of three main roles:

Devotee (User)

Organizer (Temple Manager)

Admin (System Administrator)

👤 1️⃣ Devotee (User Role)
4
🔹 Responsibilities
🔐 Registration

Create an account using:

Name

Email

Password

Authenticate securely using login credentials.

👤 Profile Management

Update:

Name

Email

Password

Manage personal information securely.

🛕 Darshan Booking

View available temples.

Check darshan slots (date & time).

Select preferred slot.

Enter number of devotees.

Complete ticket booking.

Receive electronic ticket.

⭐ Feedback & Rating

Provide:

Ratings for temple experience.

Comments or suggestions.

🚪 Logout

Securely logout from the DarshanEase system.

🏛 2️⃣ Organizer (Temple Role)
4
🔹 Responsibilities
👤 Profile Management

Update personal details:

Email

Name

Password

⏳ Darshan Slot Management

Create darshan slots.

Set:

Date

Start time

End time

Slot capacity

Mark special slots (VIP / Festival).

Update availability.

Close or cancel slots if needed.

🎟 Booking Management

View all bookings.

Monitor slot capacity.

Assign slots manually (if required).

Modify bookings if necessary.

🔔 Notification Handling

Receive notifications for:

New bookings

Cancellations

Slot updates

🚪 Logout

Logout securely from the system.

🛠 3️⃣ Admin (System Administrator Role)
4
🔹 Responsibilities
⚙ System Management

Full control over:

Users

Organizers

Temples

Slots

Bookings

Maintain system security.

Manage configurations.

👥 Devotee Management

Create, update, delete devotee accounts.

Monitor user activities.

Manage ratings and feedback.

🏛 Temple Organizer Management

Create, update, delete organizer accounts.

Assign organizers to temples.

🗓 Facility & Slot Management

Schedule darshan slots.

Allocate resources.

Manage temple capacity.

Handle maintenance-related slot closures.

🎉 Events Management

Create temple events.

Update event details.

Delete events if necessary.

📊 Reporting & Analytics

View:

Booking statistics

Popular temples

Revenue reports

Daily / Monthly activity trends

🚪 Logout

Securely logout from DarshanEase.

🔷 Role Hierarchy Summary
Role	Access Level	Control Scope
Devotee	Limited	Personal bookings & profile
Organizer	Medium	Temple & slot management
Admin	Full	Complete system control

