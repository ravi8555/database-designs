# 🏥 Clinic Management System - Database Design

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


---

## 📊 ER Diagram

### Eraser DSL Format
The ER diagram is written in **Eraser DSL syntax** for use with Eraser's diagram-as-code feature.

```eraser
entity-relationship-diagram

Patient [icon: user, color: blue] {
  patient_id int pk
  first_name varchar
  last_name varchar
  email varchar unique
  phone varchar
  date_of_birth date
  gender enum:MALE,FEMALE,OTHER
  blood_group varchar
  address text
  created_at date
}

Doctor [icon: user-md, color: green] {
  doctor_id int pk
  first_name varchar
  last_name varchar
  email varchar unique
  phone varchar
  qualification varchar
  experience_years int
  consultation_fee decimal
  joining_date date
}

Specialty [icon: tags, color: purple] {
  specialty_id int pk
  specialty_name varchar unique
  description text
}

DoctorSpecialty [icon: user-md, color: green] {
  doctor_id int pk fk
  specialty_id int pk fk
}

Appointment [icon: calendar-check, color: yellow] {
  appointment_id int pk
  patient_id int fk
  doctor_id int fk
  appointment_date date
  appointment_time time
  status enum:SCHEDULED,CONFIRMED,CANCELLED,COMPLETED,NO_SHOW
  booking_date timestamp
  notes varchar
}

Consultation [icon: stethoscope, color: teal] {
  consultation_id int pk
  appointment_id int fk unique
  patient_id int fk
  doctor_id int fk
  consultation_date date
  consultation_time time
  symptoms text
  diagnosis text
  prescription text
  advice text
  follow_up_required boolean
  follow_up_date date
}

PrescribedTest [icon: flask, color: red] {
  prescribed_test_id int pk
  consultation_id int fk
  test_name varchar
  test_category varchar
  urgency enum:NORMAL,URGENT
  instructions text
  prescribed_date date
}

DiagnosticTest [icon: microscope, color: orange] {
  test_id int pk
  prescribed_test_id int fk
  test_name varchar
  lab_name varchar
  sample_required boolean
  sample_type enum:BLOOD,URINE,XRAY,ECG,OTHER
  test_date date
  status enum:PENDING,IN_PROGRESS,COMPLETED
}

Report [icon: file-alt, color: purple] {
  report_id int pk
  test_id int fk
  patient_id int fk
  consultation_id int fk
  report_date date
  report_data text
  file_url varchar
  summary text
  status enum:GENERATED,APPROVED,SENT_TO_PATIENT
}

Payment [icon: credit-card, color: yellow] {
  payment_id int pk
  consultation_id int fk
  appointment_id int fk
  patient_id int fk
  amount decimal
  payment_method enum:CASH,CARD,UPI,INSURANCE
  payment_status enum:PENDING,COMPLETED,FAILED,REFUNDED
  payment_date timestamp
  transaction_id varchar unique
  receipt_url varchar
}

// Relationships
Patient patient_id -- Appointment patient_id
Doctor doctor_id -- Appointment doctor_id
Patient patient_id -- Consultation patient_id
Doctor doctor_id -- Consultation doctor_id
Appointment appointment_id -- Consultation appointment_id
Doctor doctor_id -- DoctorSpecialty doctor_id
Specialty specialty_id -- DoctorSpecialty specialty_id
Consultation consultation_id -- PrescribedTest consultation_id
PrescribedTest prescribed_test_id -- DiagnosticTest prescribed_test_id
Patient patient_id -- Report patient_id
Consultation consultation_id -- Report consultation_id
DiagnosticTest test_id -- Report test_id
Patient patient_id -- Payment patient_id
Consultation consultation_id -- Payment consultation_id
Appointment appointment_id -- Payment appointment_id

## 🤝 Contribution

Feel free to fork this repo and improve the design.

---

## 📧 Contact

**Ravindra Dhadave**
📧 [ravi8555@gmail.com](mailto:ravi8555@gmail.com)

---

## ⭐ If you like this project

Give it a ⭐ on GitHub!
