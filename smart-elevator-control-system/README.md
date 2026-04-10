# 🏢 Elevator Management System ER Model

## 📌 Overview
This project represents the **database design (ER Model)** for a smart elevator infrastructure system used in large buildings such as:

- Corporate towers  
- Malls  
- Airports  
- Residential complexes  

The system is designed to handle high-volume elevator operations efficiently.

---

## ⚙️ System Capabilities

The system manages:

- Multiple buildings and floors  
- Elevator shafts and elevators  
- Floor-level requests  
- Ride assignments and logs  
- Elevator status tracking  
- Maintenance history  
- Real-time elevator snapshots  

This design ensures:

- ✅ Scalability  
- ✅ Real-time monitoring  
- ✅ Efficient elevator operations  

---

## 🎯 Key Questions Answered

The system is designed to answer:

- How many buildings and elevators exist?  
- Which floors belong to which building?  
- Which elevators serve which floors?  
- What requests are generated from floors?  
- Which elevator handled a request?  
- How many rides were completed?  
- What is the current elevator status?  
- Is an elevator under maintenance?  
- What is the real-time state of elevators?  

---

## 🔗 Entity Relationships

### 🏢 Building Relationships
- **Building → Floor** : `building_id`
- **Building → ElevatorShaft** : `building_id`
- **Building → Elevator** : `building_id`
- **Building → FloorRequest** : `building_id`

---

### 🛗 Elevator Structure
- **ElevatorShaft → Elevator** : `shaft_id`

---

### 🧱 Floor Relationships
- **Floor → ElevatorServedFloor** : `floor_id`
- **Floor → FloorRequest** : `floor_id`

---

### 🛗 Elevator Operations
- **Elevator → ElevatorStatus** : `elevator_id`
- **Elevator → RideLog** : `elevator_id`
- **Elevator → MaintenanceRecord** : `elevator_id`
- **Elevator → CurrentElevatorSnapshot** : `elevator_id`
- **Elevator → RideAssignment** : `elevator_id`

---

### 📲 Request & Ride Flow
- **FloorRequest → RideAssignment** : `request_id`
- **RideAssignment → RideLog** : `assignment_id`

---

## 💡 Design Highlights

- 🔹 Separation of **request, assignment, and ride execution**
- 🔹 Supports **multi-building and multi-elevator architecture**
- 🔹 Tracks both **real-time (snapshot)** and **historical data (logs)**
- 🔹 Maintains **maintenance history without overwriting data**
- 🔹 Enables **analytics on ride usage and elevator performance**

---

## 🧑‍💻 Author
**Ravindra Dhadave**

---

## 📄 License
This project is for educational and system design purposes.