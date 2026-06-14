# Rivalry Tracker

**Category:** Web Development  
**Tech Stack:** MERN (MongoDB, Express.js, React, Node.js)


---

## 1. Project Overview

Rivalry Tracker is a web app that lets small groups of friends, siblings, or roommates track ongoing head-to-head gaming rivalries across multiple games. Users create a "Rivalry" with another person, add the games they play together, log match results, and view an automatically calculated scorecard, win streaks, and match history.

**Tagline:** *"Track every win. Settle every score."*

---

## 2. User Roles

- **Registered User**  the only role for this MVP. Users can create/join rivalries, manage games, log matches, and view stats. No admin role is required.

---

## 3. Core Modules & Features

### 3.1 Authentication
- Register (name, email, password)
- Login / Logout
- Passwords hashed (bcrypt); sessions handled via JWT

### 3.2 Rivalry Management
- Create a new Rivalry (name, optional description)
- Invite a member via email or shareable invite code
- View list of all Rivalries the user belongs to (Dashboard)

### 3.3 Game Management
- Add games to a Rivalry (e.g., FIFA, Chess, Mario Kart)
- Edit / remove games from a Rivalry
- Each game's win count is tracked independently per Rivalry

### 3.4 Match Logging
- Log a match: select game, select winner, date, optional note
- Edit or delete a match (only by users in that rivalry)

### 3.5 Scoreboard & Stats
- Overall scorecard per Rivalry (total wins per member)
- Per-game win breakdown table
- Current win streak per member (auto-calculated from match history)
- Head-to-head summary

### 3.6 Match History
- Chronological feed of logged matches (game, winner, date, note)

### 3.7 User Profile
- Name, email, list of rivalries joined, basic overall stats (total matches logged, win rate, longest streak)

---

## 4. Pages

| Page | Description | Reference Mockup |
|---|---|---|
| Landing | Intro + Login/Register CTA | 
| Login / Register | Auth forms | `reference_image/login.png` |
| Dashboard | List of user's rivalries with mini scoreboards | `reference_image/dashboard.png` |
| Create Rivalry | Form to create a new rivalry + invite members | `reference_image/create_rivalry.png` |
| Rivalry Detail | Full scoreboard, per-game breakdown, win streaks, match history, "Log Match" button | `reference_image/reference_image.png` |
| Log Match (Modal) | Form to log a new match result | `reference_image/log_match.png` |
| Profile | User info, rivalries list, overall stats | `reference_image/profile.png` |

All reference mockups are included in this submission and use the brand color palette defined in `assets.pdf`.

---

## 5. Database Schema (High-Level)

```
User
  - _id
  - name
  - email
  - passwordHash

Rivalry
  - _id
  - name
  - description
  - members: [userId]

Game
  - _id
  - rivalryId
  - name

Match
  - _id
  - rivalryId
  - gameId
  - winnerId
  - date
  - note
```

---

## 6. Expected API Endpoints

```
POST   /api/auth/register
POST   /api/auth/login

GET    /api/rivalries            (list rivalries for logged-in user)
POST   /api/rivalries            (create rivalry)
POST   /api/rivalries/:id/invite (invite member)

GET    /api/rivalries/:id        (rivalry detail incl. scoreboard)
POST   /api/rivalries/:id/games  (add game)
DELETE /api/games/:id             (remove game)

POST   /api/matches              (log match)
PUT    /api/matches/:id          (edit match)
DELETE /api/matches/:id          (delete match)

GET    /api/users/me              (profile + stats)
```

---

## 7. Design Guidelines

- **Colors:** Charcoal Navy (#1F2A3C), Rivalry Red (#E63946), Victory Gold (#FFC857), Off White (#F5F5F5), Slate Grey (#3A3A3A)  see `assets.pdf`
- **Typography:** Headings  Poppins (Bold); Body  Inter or Roboto
- **Icons:** Use a free icon set (Lucide / Feather Icons) for trophy, flame (streak), controller, add, calendar, profile, edit/delete
- The interface must work on desktop and mobile without overlapping text, clipped content, or unusable controls.


---

## 8. Deliverables

- Full source code (frontend + backend) in a public GitHub repository
- Basic README with setup/run instructions
- Deployed live demo link (e.g., Vercel/Render + MongoDB Atlas)

---

## 9. Out of Scope

- Mobile app
- Real-time notifications
- Social media login (OAuth)
- Image/avatar uploads
- Admin dashboard
- Payment/subscription features

