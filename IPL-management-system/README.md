# 🏏 Indian Premier League Management System – ER Model

## 📌 Overview

This project represents the **database design (ER Model)** for a professional cricket league system (similar to IPL).

It manages end-to-end operations including:

* Teams, Players, Owners, Sponsors
* Matches, Venues, Seasons
* Ball-by-ball gameplay tracking
* Player statistics and contracts
* Broadcasting and ticketing
* Auctions and awards

This design supports **high scalability, analytics, and real-time match tracking**.

---

## ⚙️ System Capabilities

The system manages:

* Multiple teams and players
* Player contracts and auctions
* Season-wise tournaments
* Match scheduling and results
* Ball-by-ball gameplay data
* Player performance statistics
* Sponsorship and broadcasting rights
* Ticket booking and attendance
* Awards and recognitions

---

## 🎯 Key Questions Answered

* Which players belong to which team?
* Which team owns which players in a season?
* Who won a match or season?
* What happened in each ball of a match?
* Which player performed best?
* What are team standings (points table)?
* Who are the sponsors and broadcast partners?
* How are tickets managed?
* Which awards were given?

---

## 🧩 Entities Overview

### 🏏 Team

* Stores team details such as name and home ground

### 👤 Player

* Stores player info including role and bio

### 👑 Owner

* Represents team owners

### 🤝 Sponsor & TeamSponsor

* Sponsors linked to teams with contract value

### 📡 BroadcastPartner & BroadcastRights

* Media partners and broadcasting rights per season

### 📅 Season

* Tournament-level data including winners

### 🏟️ Venue

* Match locations and infrastructure

### 🏏 Match

* Stores match details, teams, results, toss, stats

---

## 📊 Gameplay Tracking

### 🧱 Inning → Over → Ball → BallEvent

* Full hierarchical match tracking:

  * Inning → Overs → Balls → Events
* Supports:

  * Runs, wickets, extras, events

---

## 👨‍💼 Player Management

### 📄 PlayerContract

* Links players to teams per season

### 📈 PlayerStat

* Season-wise performance stats

---

## 🏆 Awards & Auctions

### 🏅 Award & PlayerAward

* Tracks awards given to players

### 🔨 PlayerAuction

* Auction details per season

---

## 🎟️ Ticketing

### 🎫 Ticket

* Match tickets with seat, price, and status

---

## 📊 Points Table

### 📋 PointsTable

* Tracks team rankings per season

---

## 👨‍⚖️ Match Officials

### 🧑‍⚖️ Umpire & MatchOfficial

* Officials assigned to matches

---

## 📡 Broadcasting

### 📺 BroadcastSchedule

* Match-wise broadcasting schedule

---

## 🔗 Relationships

### 🏏 Team Relationships

* Team → Owner (1:1)
* Team → PlayerContract (1:N)
* Team → TeamSponsor (1:N)
* Team → PointsTable (1:N)

---

### 👤 Player Relationships

* Player → PlayerContract (1:N)
* Player → PlayerStat (1:N)
* Player → PlayerAward (1:N)

---

### 📅 Season Relationships

* Season → PlayerContract (1:N)
* Season → PlayerStat (1:N)
* Season → PointsTable (1:N)
* Season → BroadcastRights (1:N)
* Season → PlayerAuction (1:1)

---

### 🏏 Match Relationships

* Match → Inning (1:N)
* Match → Ticket (1:N)
* Match → MatchOfficial (1:1)
* Match → BroadcastSchedule (1:N)

---

### 📊 Gameplay Relationships

* Inning → Over (1:N)
* Over → Ball (1:N)
* Ball → BallEvent (1:N)

---

### 📡 Broadcast Relationships

* BroadcastPartner → BroadcastRights (1:N)
* BroadcastPartner → BroadcastSchedule (1:N)

---

### 🏆 Award Relationships

* Award → PlayerAward (1:N)

---

## 💡 Key Design Decisions

### 1. Ball-by-Ball Granularity

* Full cricket tracking using:

  * Inning → Over → Ball → Event

---

### 2. Season-Based Modeling

* Contracts, stats, and points tied to seasons

---

### 3. Separation of Concerns

* Match, stats, contracts, and broadcasting are independent

---

### 4. Many-to-Many Handling

* Team ↔ Sponsor via `TeamSponsor`

---

### 5. Realistic Cricket Flow

* Toss, result, innings, overs, and ball events modeled accurately

---

## 🚀 How to Use

1. Import schema into ER tools (dbdiagram / drawsql)
2. Visualize relationships
3. Extend with APIs or analytics

---

## 📌 Future Enhancements

* Live match scoring system
* Fantasy league integration
* Player performance prediction
* AI-based analytics dashboard

---

## 🧑‍💻 Author

**Ravindra Dhadave**

---

## 📄 License

This project is for educational and system design purposes.
