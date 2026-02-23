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


Task 2.

![image alt]https://github.com/Gauravraaz70/Darshan-Ease/blob/1385eb3f3ae5d5a32bb77ab3b7cfd4508d98f5f0/Er%20Diagram.png

Summary:- “DarshanEase follows a microservices-based architecture. The system consists of a frontend interface hosted on a web server, connected to backend services through an API Gateway.
Authentication Service ensures secure access, while specialized services such as Darshan Service, Booking Service, Temple Service, Seat Service, and Ticket Service handle their respective functionalities.
All persistent data is stored in a centralized database.”

Response is sent back to user.
