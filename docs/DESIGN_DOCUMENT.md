# Zakat & Savings Tracker
## System Analysis and Design Document

**Project Name:** Zakat & Savings Tracker

**Project Type:** Mobile Application

**Mobile Technology:** Flutter and Dart

**Backend:** REST API

**Database:** Relational Database

**Group Members:**
- Ebaa Ali
- Luksa Harunah Talha
- Ntarambirwa Fidele

**Course:** Mobile App Development Capstone

**Lecturer:** Dr. Matsiko
---

## 1. Problem Statement

Managing personal assets, savings goals, and zakat payment records can be difficult when financial information is stored in different places or recorded manually. This can make it harder for users to monitor their savings progress, maintain organised records, and review previous zakat payments.

The Zakat & Savings Tracker is a mobile application designed to help users manage their financial information in one place. Users will be able to create an account, securely log in, record their assets, set savings goals, estimate their zakat based on the information and calculation settings provided, and record zakat payments.

The application will use Flutter and Dart for the mobile interface, a REST API for communication with the backend, and a relational database to store information. Each user will only be able to access their own financial records.

The goal is to provide a convenient and organised way to track savings and financial records. Zakat calculations will be estimates and will not replace guidance from a qualified religious authority.

## 2. Users and Goals

### 2.1 Target Users

The application is designed for individuals who want to organise their financial records, track savings goals, and keep records of their zakat payments.

### 2.2 User Goals

Users should be able to:

1. Register an account and log in securely.
2. Add, view, update, and delete their asset records.
3. Create and manage savings goals.
4. Track progress towards their savings targets.
5. View an estimated zakat amount based on their recorded information and calculation settings.
6. Record and review zakat payments.
7. Access their financial records securely and privately.

## 3. System Requirements

### 3.1 Functional Requirements

The system shall:

1. Allow users to register an account using their name, email, and password.
2. Allow registered users to log in securely.
3. Allow users to log out of their accounts.
4. Allow users to add new asset records.
5. Allow users to view their recorded assets.
6. Allow users to update existing asset records.
7. Allow users to delete asset records.
8. Allow users to create and manage savings goals.
9. Allow users to view an estimated zakat amount based on their financial information and calculation settings.
10. Allow users to record and view zakat payments.
11. Ensure that users can access only their own financial records.
12. Validate user input and display appropriate error messages.

### 3.2 Non-Functional Requirements

1. **Security:** The system shall protect user accounts by hashing passwords and securing access to private records.
2. **Usability:** The system shall provide a clear and simple interface that users can navigate easily.
3. **Reliability:** The system shall display appropriate error messages when requests fail or the backend is unavailable.
4. **Performance:** The system shall respond to normal user requests within a reasonable time under typical usage conditions.

5. ## 4. User Stories

1. As a user, I want to register an account so that I can use the application.
2. As a registered user, I want to log in securely so that my financial records remain private.
3. As a user, I want to add asset records so that I can track my assets.
4. As a user, I want to view my assets so that I can review my financial information.
5. As a user, I want to update asset records so that I can correct or change information.
6. As a user, I want to delete asset records so that I can remove information I no longer need.
7. As a user, I want to create savings goals so that I can plan my savings.
8. As a user, I want to track my savings progress so that I can see how close I am to my targets.
9. As a user, I want to estimate my zakat based on my financial information so that I can plan my zakat obligations.
10. As a user, I want to record zakat payments so that I can keep a history of payments.
11. As a user, I want to view my previous zakat payments so that I can review my records.
12. As a user, I want to log out so that my account is not left open on a shared device.

## 5. Database Design (ERD)

The database will contain four main entities: users, assets, savings_goals, and zakat_payments. Each user can have multiple asset records, multiple savings goals, and multiple zakat payment records.

### 5.1 Entity 1: users

- user_id: INTEGER, Primary Key, auto-increment
- name: VARCHAR(100), NOT NULL
- email: VARCHAR(150), UNIQUE, NOT NULL
- password_hash: VARCHAR(255), NOT NULL
- created_at: DATETIME, NOT NULL

### 5.2 Entity 2: assets

- asset_id: INTEGER, Primary Key, auto-increment
- user_id: INTEGER, Foreign Key references users(user_id)
- asset_name: VARCHAR(100), NOT NULL
- asset_type: VARCHAR(50), NOT NULL
- amount: DECIMAL(12,2), NOT NULL
- record_date: DATE, NOT NULL

### 5.3 Entity 3: savings_goals

- goal_id: INTEGER, Primary Key, auto-increment
- user_id: INTEGER, Foreign Key references users(user_id)
- goal_name: VARCHAR(100), NOT NULL
- target_amount: DECIMAL(12,2), NOT NULL
- current_amount: DECIMAL(12,2), NOT NULL, default 0
- target_date: DATE, nullable

### 5.4 Entity 4: zakat_payments

- payment_id: INTEGER, Primary Key, auto-increment
- user_id: INTEGER, Foreign Key references users(user_id)
- amount: DECIMAL(12,2), NOT NULL
- payment_date: DATE, NOT NULL
- notes: VARCHAR(255), nullable

### 5.5 Relationships and Cardinality

1. One user can have many assets (1:N).
2. One user can have many savings goals (1:N).
3. One user can have many zakat payment records (1:N).

Each asset, savings goal, and zakat payment record belongs to one user through the user_id foreign key.

### 5.6 Normalisation

The database is designed to follow Third Normal Form (3NF). Each table represents one main entity, each table has a primary key, and user information is stored separately from assets, savings goals, and zakat payments. This reduces unnecessary duplication and helps maintain data consistency.

## 6. Data Dictionary

The data dictionary describes the fields, data types, constraints, and meanings of the database tables.

### 6.1 Users Table

| Field | Data Type | Constraints | Description |
|---|---|---|---|
| user_id | INTEGER | Primary Key, Auto-increment | Unique user identifier |
| name | VARCHAR(100) | NOT NULL | User's full name |
| email | VARCHAR(150) | UNIQUE, NOT NULL | User's email address |
| password_hash | VARCHAR(255) | NOT NULL | Hashed password |
| created_at | DATETIME | NOT NULL | Account creation date and time |

### 6.2 Assets Table

| Field | Data Type | Constraints | Description |
|---|---|---|---|
| asset_id | INTEGER | Primary Key, Auto-increment | Unique asset identifier |
| user_id | INTEGER | Foreign Key, NOT NULL | Owner of the asset |
| asset_name | VARCHAR(100) | NOT NULL | Name or description of the asset |
| asset_type | VARCHAR(50) | NOT NULL | Category of the asset |
| amount | DECIMAL(12,2) | NOT NULL | Recorded asset value |
| record_date | DATE | NOT NULL | Date the asset was recorded |

### 6.3 Savings Goals Table

| Field | Data Type | Constraints | Description |
|---|---|---|---|
| goal_id | INTEGER | Primary Key, Auto-increment | Unique savings goal identifier |
| user_id | INTEGER | Foreign Key, NOT NULL | Owner of the goal |
| goal_name | VARCHAR(100) | NOT NULL | Name of the savings goal |
| target_amount | DECIMAL(12,2) | NOT NULL | Desired savings amount |
| current_amount | DECIMAL(12,2) | NOT NULL, DEFAULT 0 | Current saved amount |
| target_date | DATE | NULL allowed | Planned completion date |

### 6.4 Zakat Payments Table

| Field | Data Type | Constraints | Description |
|---|---|---|---|
| payment_id | INTEGER | Primary Key, Auto-increment | Unique payment identifier |
| user_id | INTEGER | Foreign Key, NOT NULL | User who recorded the payment |
| amount | DECIMAL(12,2) | NOT NULL | Amount of zakat paid |
| payment_date | DATE | NOT NULL | Date of payment |
| notes | VARCHAR(255) | NULL allowed | Optional payment notes |
