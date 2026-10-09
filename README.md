# HotelChain

Backend for a hotel and hostel management system, built as an Airbnb-style booking platform with **Java + Spring Boot**. Backend only — no frontend in this repo.

## The client

One owner, multiple properties:

| Property type | Count |
|---------------|-------|
| Hotels        | 3     |
| Hostels       | 5     |
| Cities        | 3     |

Hotels sell **rooms**; hostels sell **beds** (dorms) as well as private rooms. The system has to handle both under one booking flow.

## Tech stack

| Layer      | Choice                          |
|------------|---------------------------------|
| Language   | Java 21                         |
| Framework  | Spring Boot 4.1.1               |
| Web        | Spring Web MVC (REST APIs)      |
| Data       | Spring Data JPA (Hibernate)     |
| Build      | Maven (wrapper included)        |
| Database   | _To be decided_                 |

## Current status — Day 01

Boilerplate only: a Spring Initializr project with the **Spring Web** and **Spring Data JPA** dependencies. No entities, controllers, or database yet.

> **Note:** Spring Data JPA needs a database to start. Until a driver and datasource are added, the project compiles but `spring-boot:run` and the context test will fail. That is the next step.

## Planned modules

Nothing below is built yet — this is the layout we are working towards.

- **Property management** — hotels and hostels, their city, address, amenities, photos, active/inactive status
- **Room and bed management** — room types, dorm beds, capacity, base price
- **Inventory** — per-day availability and price for each room type
- **Search** — find properties by city, dates, and number of guests
- **Booking** — reserve, add guests, confirm, cancel
- **Guests and users** — sign-up, login, profiles, roles (guest / property manager / admin)
- **Payments** — payment for a booking, refunds on cancellation
- **Admin reports** — occupancy and revenue per property and per city

## Planned domain model

```
City 1 ──── * Property (HOTEL | HOSTEL)
Property 1 ──── * Room
Room 1 ──── * Inventory (one row per date)
User 1 ──── * Booking
Booking * ──── 1 Property
Booking * ──── 1 Room
Booking 1 ──── * Guest
Booking 1 ──── 1 Payment
```

## Planned package layout

```
src/main/java/com/hotelchain
├── HotelChainApplication.java   ← exists today
├── controller/                  REST endpoints
├── service/                     business logic
├── repository/                  Spring Data JPA repositories
├── entity/                      JPA entities
├── dto/                         request / response objects
├── exception/                   custom exceptions and global handler
└── config/                      application configuration
```

## Getting started

Requirements: JDK 21 or newer. Maven is not required — the wrapper downloads it.

```bash
git clone https://github.com/yaswanth211825/HotelChain.git
cd HotelChain
./mvnw clean compile
```

Running the app (`./mvnw spring-boot:run`) will work once a database is configured.

## Progress log

| Day    | What was done                                                    |
|--------|------------------------------------------------------------------|
| Day 01 | Spring Initializr boilerplate (Web MVC + Data JPA), README layout |
