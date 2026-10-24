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
