# Deliverable D1: Design Models and Design Rationale

## 1. Introduction
The **Fitness Management System** is a comprehensive solution designed to automate fitness center operations, including membership management, course scheduling, personal trainer bookings, and facility reservations. This document details the architectural design for the **v1.0 release**, focusing on system integrity, security, and adherence to professional construction standards.

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