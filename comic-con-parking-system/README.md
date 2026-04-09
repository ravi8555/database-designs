# 🅿️ ## Comic-Con Parking System – ER Design

## 📌 Overview

This project represents the **database design (ER Model)** for a large-scale event parking system such as Comic-Con India.

The system manages:

* Vehicle entry & exit
* Parking spot allocation
* Zone-based parking structure
* Reserved parking categories (VIP, Staff, Exhibitor, EV, Cosplayer)
* Parking sessions & tickets
* Payment tracking
* Real-time parking availability

The design ensures **efficient space utilization, scalability, and structured tracking of parking operations**.

---

## 🎯 Objectives

This system is designed to answer:

* What vehicles entered the parking facility?
* What type of vehicle is it?
* Which parking spot and category was assigned?
* Which zone does the spot belong to?
* When did the vehicle enter and exit?
* What ticket was generated?
* What is the payment status?
* Can a vehicle enter multiple times?
* Can a parking spot be reused?
* What is the current parking availability?

---

## 🧩 Entities Description

### 🚗 Vehicle

Stores vehicle details:

* `vehicle_id` (PK)
* `vehicle_number` (unique)
* `vehicle_type_id` (FK)
* `is_vip`
* `created_at`

---

### 🏷️ Vehicle Type

Defines vehicle categories:

* Car, Bike, SUV, EV, Cab

---

### 🅿️ Parking Spot

Represents individual parking slots:

* Linked to zone and category
* Tracks availability status

---

### 📂 Spot Category

Defines parking types:

* General, VIP, Staff, Exhibitor, Cosplayer, EV Charging
* Includes hourly pricing

---

### 🗺️ Parking Zone

Represents different parking areas:

* Zone name
* Logical grouping of parking spots

---

### ⏱️ Parking Session

Core entity tracking:

* Vehicle entry & exit
* Assigned category
* Ticket & payment linkage
* Session status (Active, Completed, Cancelled)

---

### 🎫 Parking Ticket

Generated at entry:

* Linked to session
* Contains QR code for tracking

---

### 💳 Payment

Handles billing:

* Linked to vehicle & session
* Stores transaction details
* Tracks payment status

---

### 📊 Current Parking Status

Tracks real-time availability:

* Total spots
* Occupied spots
* Available spots
* Updated per zone

---

## 🔗 Relationships

* **Vehicle → VehicleType** (Many-to-One)
* **ParkingSpot → ParkingZone** (Many-to-One)
* **ParkingSpot → SpotCategory** (Many-to-One)
* **Vehicle → ParkingSession** (One-to-Many)
* **ParkingSession → ParkingTicket** (One-to-One)
* **ParkingSession → Payment** (One-to-One / One-to-Many)
* **ParkingZone → CurrentParkingStatus** (One-to-One)



## 🧑‍💻 Author

**Ravindra Dhadave**

---

## 📄 License

This project is intended for educational and system design purposes.
