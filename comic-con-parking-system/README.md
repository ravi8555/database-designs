# 🅿️ Comic-Con Parking System – ER Design

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

## 🎯 Business Requirements Supported

The database design answers key operational questions:
- ✅ What vehicles entered the parking facility?
- ✅ What type of vehicle entered (bike, car, SUV, EV)?
- ✅ Which parking spot was assigned to which vehicle?
- ✅ Which zone or level does that parking spot belong to?
- ✅ Was the parking spot reserved for exhibitors, VIP guests, staff, or EV charging?
- ✅ When did the vehicle enter and exit the facility?
- ✅ What ticket was issued for the parking session?
- ✅ Can one vehicle visit the venue multiple times across different days?
- ✅ Can one parking spot be reused across multiple parking sessions?
- ✅ How is parking availability tracked in real-time?
- ✅ How are parking charges calculated based on vehicle type and access category?
- ✅ How is payment recorded for each parking session?
- ✅ Can special access categories (cosplayers with props, exhibitors, VIP guests, staff) be represented?
- ✅ Can the system track which vehicles are currently parked inside the venue?

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
