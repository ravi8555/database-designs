# 🏋️‍♂️ Online Fitness Coaching Platform – ER Diagram

## 📌 Overview

This project represents the **database design (ER Diagram)** for an online fitness coaching platform.
The system enables fitness influencers/trainers to manage clients, sell coaching plans, schedule sessions, track progress, and handle subscriptions and payments.

This is **not a gym management system**, but a scalable **online coaching ecosystem**.

---

## 🎯 Features Covered

* 👤 User management (Client / Trainer / Admin)
* 🧑‍🏫 Trainer & Client profiles
* 📦 Coaching plans & programs
* 🔁 Subscription system
* 📅 Session scheduling (consultation/live)
* 📊 Progress tracking (weight, measurements)
* 📝 Weekly check-ins & trainer feedback
* 💳 Payment tracking

---

## 🧩 Entity Design

### 1. User

* Stores all users (clients, trainers, admins)
* Role-based system

### 2. TrainerProfile

* Additional details for trainers
* Linked to User

### 3. ClientProfile

* Stores client-specific fitness data

### 4. CoachingPlan

* Plans created by trainers
* Can be purchased by multiple clients

### 5. ClientPlanSubscription

* Core table connecting client ↔ plan
* Tracks start/end dates and status

### 6. Session

* Live classes or consultation calls

### 7. WeeklyCheckIn

* Client submits weekly updates

### 8. ProgressLog

* Tracks weight, body fat, etc.

### 9. BodyMeasurement

* Detailed body stats (chest, waist, etc.)

### 10. WorkoutPlan & DietPlan

* Structured plan content

### 11. TrainerFeedback

* Trainer feedback on check-ins

### 12. Payment

* Tracks payments for subscriptions

---

### Entity Relationship Diagram
erDiagram
    USER {
        int user_id PK
        string name
        string email
        string role
    }
    
    TRAINER {
        int trainer_id PK
        text bio
    }
    
    CLIENT {
        int client_id PK
        date date_of_birth
        float starting_weight_kg
    }
    
    COACHING_PLAN {
        int plan_id PK
        int trainer_id FK
        string plan_name
        decimal price
    }
    
    CLIENT_PLAN_SUBSCRIPTION {
        int subscription_id PK
        int client_id FK
        int plan_id FK
        date start_date
        date end_date
    }
    
    WEEKLY_CHECKIN {
        int checkin_id PK
        int client_id FK
        int subscription_id FK
        float weight_kg
        datetime submitted_at
    }
    
    TRAINER_FEEDBACK {
        int feedback_id PK
        int checkin_id FK
        int trainer_id FK
        text feedback_text
    }
    
    CONSULTATION {
        int consultation_id PK
        int client_id FK
        int trainer_id FK
        datetime scheduled_time
    }
    
    LIVE_SESSION {
        int session_id PK
        int trainer_id FK
        string session_name
        datetime session_datetime
    }
    
    PAYMENT {
        int payment_id PK
        int subscription_id FK
        int consultation_id FK
        decimal amount
        string status
    }

    USER ||--o| TRAINER : "is one"
    USER ||--o| CLIENT : "is one"
    TRAINER ||--o{ COACHING_PLAN : "creates"
    CLIENT ||--o{ CLIENT_PLAN_SUBSCRIPTION : "buys"
    COACHING_PLAN ||--o{ CLIENT_PLAN_SUBSCRIPTION : "has"
    CLIENT ||--o{ WEEKLY_CHECKIN : "submits"
    CLIENT_PLAN_SUBSCRIPTION ||--o{ WEEKLY_CHECKIN : "belongs to"
    WEEKLY_CHECKIN ||--|| TRAINER_FEEDBACK : "receives"
    CLIENT ||--o{ CONSULTATION : "books"
    TRAINER ||--o{ CONSULTATION : "conducts"
    TRAINER ||--o{ LIVE_SESSION : "hosts"
    CLIENT_PLAN_SUBSCRIPTION ||--o{ PAYMENT : "has"
    CONSULTATION ||--o| PAYMENT : "has"


## 🔗 Relationships

* A **User** can be a Trainer or Client
* A **Trainer** can create multiple Plans
* A **Client** can subscribe to multiple Plans
* A **Plan** can have multiple Clients
* A **Subscription** connects Client ↔ Plan
* A **Subscription** can have:

  * Payments
  * Sessions
  * Check-ins
  * Progress logs

---

## 🧠 Key Design Decisions

* ✅ **Subscription as central entity**
* ✅ Separation of **Session vs Check-in**
* ✅ Modular **progress tracking**
* ✅ Scalable many-to-many relationships
* ✅ Clean normalization (no redundant data)

---

## 🛠️ Tools Used

* ✏️ Eraser (for ER Diagram using code)
* 🧠 Conceptual database design principles

---

## 📂 Project Structure

```
/er-diagram
  ├── eraser-diagram.txt   # ER diagram code
  ├── README.md
```

---

## 🚀 How to Use

1. Open **Eraser**
2. Paste the ER diagram code
3. Visualize relationships automatically

---

## 📈 Future Improvements

* Add notifications system
* Add chat between trainer & client
* Add workout tracking logs
* Add API layer (Node.js / Express)
* Convert into MongoDB schema (MERN stack)

---

## 🤝 Contribution

Feel free to fork this repo and improve the design.

---

## 📧 Contact

**Ravindra Dhadave**
📧 [ravi8555@gmail.com](mailto:ravi8555@gmail.com)

---

## ⭐ If you like this project

Give it a ⭐ on GitHub!
