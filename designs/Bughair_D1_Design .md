# Fitness management system 
## Deliverable D1: Design Models and Design Rationale

## Introduction
The **Fitness Management System** is a comprehensive solution designed to automate fitness center operations, including membership management, course scheduling, personal trainer bookings, and facility reservations. This document details the architectural design for the **v1.0 release**, focusing on system integrity, security, and adherence to professional construction standards.

---

## Functional Requirements 

### 1. User Management 

1.1 Customer Account 

- The system shall allow a customer to register an account. 

- The system shall allow a customer to select membership type during registration. 

- The system shall allow a customer to log in and log out of the system. 

- The system shall allow a customer to reset their password. 

- The system shall allow a customer to update their profile information. 

- The system shall assign a unique member ID to each registered customer. 

  

1.2 Admin Account 

- The system shall allow an administrator to log in to the backend system. 

- The system shall restrict backend access to authorized administrators only. 

- The system shall allow an administrator to manage customer data. 

- The system shall log administrative activities for auditing purposes. 

  

### 2. Membership Management 

- The system shall support two membership types: Free Membership and Paid Membership. 

- The system shall support two paid membership plans: Monthly and Yearly. 

- The system shall automatically renew monthly memberships through recurring payment. 

- The system shall record membership start date and expiration date. 

- The system shall restrict system features based on membership type. 

- The system shall allow customers to renew or upgrade membership. 

  

### 3. Payment 

- The system shall support payment via Credit Card. 

- The system shall support payment via PayPal. 

- The system shall integrate with True Money Wallet for payment processing. 

- The system shall securely process all online payments. 

- The system shall record all payment transactions. 

  

### 4. Entrance and Attendance Tracking 

- The system shall record member entry time when a valid member ID is entered at the entrance keypad. 

- The system shall record member exit time when the member leaves the fitness. 

- The system shall maintain attendance logs for all members. 

- The system shall transmit entrance records to the backend system. 

- The system shall generate attendance reports for administrators. 

  

### 5. Course Management 

5.1 Course Administration 

- The system shall allow an administrator to create a course. 

- The system shall allow an administrator to specify course details, including: 

   - Course name 

   - Schedule 

   - Instructor 

   - Maximum number of attendees 

   - Course type 

   - Fitness level 

- The system shall allow an administrator to publish or unpublish a course. 

- The system shall allow an administrator to edit course information. 

- The system shall allow an administrator to delete a course. 

- The system shall require an administrator to provide a reason when canceling a course. 

  

5.2 Course Enrollment 

- The system shall allow a member to view available courses. 

- The system shall allow a member to enroll in a course. 

- The system shall prevent enrollment when the course reaches maximum capacity. 

- The system shall detect and prevent schedule conflicts for members. 

- The system shall record attendance for enrolled courses. 

- The system shall allow administrators to generate course attendance reports. 

  

### 6. Private Training Management 

- The system shall maintain a list of private trainers. 

- The system shall allow administrators to add, edit, and delete trainers. 

- The system shall store trainer expertise and availability schedule. 

- The system shall allow members to view trainer profiles. 

- The system shall allow members to filter trainers by expertise. 

- The system shall allow members to book private training sessions. 

- The system shall prevent booking time conflicts. 

- The system shall allow administrators to manage trainer schedules. 

  

### 7. Badminton Court Reservation 

- The system shall manage five badminton courts. 

- The system shall allow only members to reserve badminton courts. 

- The system shall allow members to view available courts and time slots. 

- The system shall prevent double booking of courts. 

- The system shall prevent booking time conflicts for members. 

- The system shall allow administrators to set maintenance periods for courts. 

- The system shall block reservations during maintenance periods. 

  

### 8. Content and Promotion Management 

- The system shall allow administrators to create promotional content. 

- The system shall allow administrators to publish and update content. 

- The system shall allow customers to view promotions. 

- The system shall allow customers to view general information about the fitness center. 

- The system shall allow customers to view event and course information. 

  

### 9. Usage Monitoring and Reporting 

- The system shall display the current number of members inside the fitness center. 

- The system shall identify peak and low-peak usage periods. 

- The system shall generate usage statistics reports. 

- The system shall provide a dashboard with data visualization for administrators. 

- The system shall allow administrators to generate financial and membership reports. 

  

## Non-Functional Requirements 

### 1. Security 

- The system shall encrypt user passwords. 

- The system shall use secure communication protocols (HTTPS). 

- The system shall implement role-based access control. 

- The system shall protect against common web vulnerabilities. 

- The system shall ensure secure integration with third-party payment providers. 

  

### 2. Availability 

- The system shall operate 24 hours per day, 7 days per week. 

- The system shall ensure high system uptime. 

- The system shall support real-time data updates. 

  

### 3. Performance 

- The system shall handle concurrent users without significant performance degradation. 

- The system shall process payments within an acceptable response time. 

- The system shall detect booking conflicts in real time. 

  

### 4. Usability 

- The system shall provide a user-friendly interface. 

- The system shall be accessible via web browser or mobile application. 

- The system shall support responsive design for mobile devices. 

  

### 5. Scalability 

- The system shall support future expansion of trainers and members. 

- The system shall allow additional branches to be integrated in the future. 

  

### 6. Reliability 

- The system shall ensure data consistency during transactions. 

- The system shall prevent duplicate payments. 

- The system shall prevent double booking of courses or courts. 

  

### 7. Assumptions 

- Each member shall have a unique identification number. 

- The fitness center shall have a stable internet connection. 

- Third-party payment providers shall provide integration APIs. 

- The entrance system shall be capable of transmitting member ID data to the software system. 

- The system shall initially support a single fitness branch. 

  

## Constraints 

- The backend system shall operate only on two machines within the fitness center. 

- Administrators shall not access the backend system outside the fitness center. 

- The system shall integrate with True Money Wallet. 

- The system shall operate continuously in a 24/7 environment. 

- The implementation priority shall be: 

   - First: Membership and Payment System 

   - Second: Course Management 

   - Third: Usage Monitoring 

---

## 1. C4 Context Diagram (Level 1)

<img width="1680" height="1799" alt="Context Diagram" src="https://github.com/user-attachments/assets/ecf93758-990c-4469-8e58-bdb910b9097d" />

### External Actors 

1.1 Customer

  The Customer is an external actor because the customer interacts with the system but is not part of the system itself. Customers use the Fitness Management System to register memberships, make payments, enroll in courses, reserve facilities, and access services. 

1.2 Administrator

  The Administrator (Fitness Staff) is an external actor because administrative users interact with the system to manage data but are not part of the system implementation. They access the backend interface to manage courses, trainers, courts, promotions, and reports. 

### External Systems 

2.1 Payment Gateway System

  The Payment Gateway System is considered external because it is a third-party service responsible for processing credit card and PayPal payments. The Fitness Management System does not control or implement the internal payment processing logic. Instead, it sends payment requests and receives transaction confirmations. 

2.2 TrueMoney Wallet API

  The TrueMoney Wallet API is an external system because it is a third-party digital wallet platform that provides payment services. The fitness system integrates with TrueMoney through APIs, but it does not manage wallet balances or authentication logic internally. 

2.3 Entrance Gate System

  The Entrance Gate System is considered external because it is a physical hardware-based access control system. It captures member identification (via keypad, QR code, or card reader) and transmits data to the Fitness Management System for validation and attendance recording. 
  
---

## 2. C4 Container Diagram (Level 2)
The system is decomposed into three primary containers to ensure a clear separation of concerns, supporting modular development and maintainability.

### 2.1 Container Descriptions and Responsibilities

* **Web Application (React.js)**:
    * **Responsibility**: Provides a unified interface for both **Customers** and **Administrators**.
        * **Customers**: Register accounts, manage profiles, select membership plans (Free/Monthly/Yearly), enroll in training courses, book private trainers, and **reserve badminton courts (Court 1-5)**.
        * **Administrators**: Manage customer and trainer data, publish promotions, schedule courses, and monitor facility usage statistics.
    * **Constraint Handling**: In compliance with **Constraint 2**, administrative backend features are restricted to the local fitness center network to ensure data security.

* **API Application (Node.js/Express)**:
    * **Responsibility**: The central hub for business logic and system integration.
        * **Logic**: Processes automated membership renewals, payment flows, and real-time conflict detection for course enrollments, trainer sessions, and **badminton court reservations**.
        * **Attendance Processing**: Receives and validates **Member ID** data transmitted from the **Entrance Gate System** to record entry and exit times.
        * **External Integration**: Facilitates secure communication with the **Payment Gateway** (Credit Card, PayPal), **TrueMoney Wallet API**, and the **Entrance Gate System**.

* **Database (MySQL)**:
    * **Responsibility**: The persistent data store for all system entities.
    * **Data Integrity**: Stores relational data for Users (with unique Member IDs), Memberships, Attendance logs, Training Courses, Trainers, and Badminton Court statuses. It ensures ACID properties to prevent double-booking of resources and maintain accurate financial records.

---

## 3. Design Rationale

### 3.1 Architectural Justification
* **Decoupled Architecture**: Separating the React frontend from the Node.js API allows for independent updates. This ensures that UI changes do not affect core business logic or database stability.
* **Centralized Security**: All business rules, such as verifying membership validity before allowing a court reservation, are centralized in the API layer.
* **Standardized Communication**: The system uses **HTTPS** and **JSON** for all internal container communications, following industry standards for security.

### 3.2 Support for Key Requirements
* **Membership & Payment**: Supports multiple tiers and diverse payment methods (Credit Card, PayPal, TrueMoney) with automated recurring billing for monthly plans.
* **Facility & Equipment Management**: Manages the **5 badminton courts**, tracking status (Available, Booked, Maintenance) and enforcing specific reservation rules.
* **Attendance Tracking**: Addresses the requirement for recording entry and exit by integrating with the **Entrance Keypad**, ensuring that every unique Member ID access is logged in the backend.
* **Trainer & Course Scheduling**: Allows members to book sessions while the API's conflict-checking engine prevents overlapping schedules.

---

## 4. Relation to Future Evolution
The v1.0 architecture provides a stable foundation for Phase 2. The modular container approach allows for the future addition of features, such as advanced analytics or expansion to multiple gym branches, without requiring a complete system redesign.
