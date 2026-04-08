# 🏥 Clinic Appointment and Diagnostics Platform - Database Design
Design Link https://github.com/ravi8555/database-designs/blob/Ravindra-Dhadave/clinic-management-system/assets/clinic-management-system%E2%80%93ER_Diagram.png

## 📋 Overview

This repository contains the **Entity-Relationship (ER) diagram** design for a modern clinic management system. The design focuses on digitizing clinic operations including patient management, doctor scheduling, appointments, consultations, diagnostic tests, reports, and payment tracking.

The system is designed to be **scalable**, **practical**, and **focused** on clinic-level operations (not a full hospital management system).

---

## 🎯 Business Requirements Supported

The database design answers key business questions:

- ✅ Who are the doctors and what are their specialties?
- ✅ Which patient booked which appointment?
- ✅ What was the appointment status?
- ✅ Did the appointment result in a consultation?
- ✅ Were any diagnostic tests prescribed?
- ✅ What reports were generated?
- ✅ Can one patient have many visits?
- ✅ Can one doctor attend many patients?
- ✅ Can one consultation lead to multiple tests?
- ✅ How are payments connected to visits or appointments?

---

## 🗂️ Entities & Relationships

### Core Entities

| Entity | Description |
|--------|-------------|
| **Patient** | Stores patient demographics and medical history |
| **Doctor** | Stores doctor information and qualifications |
| **Specialty** | Medical specialties (Cardiology, Dermatology, etc.) |
| **Appointment** | Booking/scheduling information |
| **Consultation** | Actual doctor-patient visit after appointment |
| **PrescribedTest** | Tests prescribed by doctor during consultation |
| **DiagnosticTest** | Lab tests performed based on prescription |
| **Report** | Diagnostic reports generated from tests |
| **Payment** | Financial transactions for consultations/tests |

### Key Relationships
Patient → Appointment (1:N)

Doctor → Appointment (1:N)

Appointment → Consultation (1:0/1)

Consultation → Tests (M:N via Consultation_Test)

Consultation_Test → Report (1:1)

Appointment → Payment (1:1 or 1:N)



## 🤝 Contribution

Feel free to fork this repo and improve the design.

---

## 📧 Contact

**Ravindra Dhadave**
📧 [ravi8555@gmail.com](mailto:ravi8555@gmail.com)

---

## ⭐ If you like this project

Give it a ⭐ on GitHub!
