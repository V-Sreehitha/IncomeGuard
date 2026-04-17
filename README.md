# Income Guard

## Disruption-Based Insurance for Gig Workers

---

## 1. Project Overview

**Project Name:** Income Guard

Income Guard is a disruption-based insurance system designed to protect gig workers (delivery agents, drivers, etc.) from income loss caused by unexpected disruptions such as:

* Rain
* Heat
* Pollution (AQI)
* Floods
* Social disruptions (strikes, curfews)

**Core Idea:**
When a disruption occurs and prevents a worker from working, the system automatically detects the event, processes a claim, and issues a payout.

---

## 2. System Architecture

The system is divided into three main layers:

### Frontend (React)

* User Dashboard
* Claims Page
* Admin Panel
* Analytics UI

### Backend (Node.js / Express)

* Business Logic
* Claim Processing
* Fraud Detection
* Admin Approval System

### ML Microservice (Python)

* Risk Scoring
* Claim Prediction

---

## 3. Core Workflow

### Step 1: User Registration & Profile

Users provide:

* City
* Pincode
* Daily earnings
* Thresholds:

  * Rain (mm)
  * Heat (°C)
  * AQI
  * Flood level

All data is stored in the database under the User model.

---

### Step 2: Data Collection

The system gathers:

* Weather data (rain, temperature, etc.)
* Environmental data
* Social trigger data (manual/mock inputs)

---

### Step 3: Trigger Detection Engine

A cron job runs every hour to compare real-time data with user thresholds.

**Example:**

* Rain = 25 mm
* User threshold = 10 mm

If exceeded, the trigger is activated.

---

### Step 4: Claim Creation

When a disruption is detected:

* A claim is created with **status = pending**
* Includes:

  * Risk score
  * Fraud score
  * Trigger type
  * User data

---

## 4. ML Risk Scoring

The ML model generates a **risk score (0 to 1)** based on:

* Past claims
* Claim frequency
* User behavior

This score is used for premium calculation and fraud detection.

---

## 5. Premium Calculation

Weekly premium is proportional to risk score:

* Low risk → ₹100
* High risk → ₹300

---

## 6. Fraud Detection System

Fraud is detected using rule-based checks:

* Repeated claims
* Location mismatch
* Invalid triggers
* High claim frequency

Outputs a **fraud score (0 to 1)**.

---

## 7. Admin Approval System

### Workflow:

1. Claim created (pending)
2. Sent to admin
3. Admin reviews:

   * Risk score
   * Fraud score
   * Trigger type
   * Claim reason

### Admin Actions:

* Approve
* Reject

---

## 8. Payout System

Payouts are processed only after admin approval.

**Formula:**

`Payout = Avg Daily Income × Disruption Severity`

---

## 9. Dashboard System

### Worker Dashboard

* Risk score
* Weekly premium
* Wallet balance
* Claim status
* Active triggers

### Admin Dashboard

* Total claims
* Loss ratio
* Pending approvals
* Fraud analysis
* Region-wise data

---

## 10. Analytics Engine

Provides insights such as:

* Claims trends
* Loss ratio
* City-wise predictions
* Future disruption risks

---

## 11. Automation Engine

Handles periodic tasks:

* Trigger detection
* Claim creation
* Risk scoring
* Fraud scoring

---

## 12. Multi-Factor Disruption Model

### Environmental Factors

* Rain
* Heat
* Pollution
* Flood

### Social Factors

* Curfew
* Strikes
* Zone closures

---

## 13. Test Cases

### Case 1: Rain exceeds threshold

Claim → Pending → Approved → Payout

### Case 2: High heat

Claim → Fraud check → Admin decision

### Case 3: Duplicate claim

Fraud score increases → Rejected

### Case 4: No disruption

No claim created

---

## 14. Security & Validation

* Prevents duplicate claims
* Validates trigger sources
* Ensures admin approval
* Integrates fraud detection layer

---

## 15. Final System Flow

This section explains the complete working of the system in a clear and structured manner:

### Step 1: User Onboarding

* User registers or logs into the system
* Enters profile details:

  * City & Pincode
  * Daily Income
  * Disruption Thresholds (Rain, Heat, AQI, Flood, etc.)

---

### Step 2: Data Collection

* System continuously collects external data:

  * Weather data (Rain, Temperature)
  * Environmental data (AQI)
  * Social events (Strikes, Curfews - simulated/manual)

---

### Step 3: Disruption Detection

* System compares real-time data with user-defined thresholds

**If no threshold is exceeded:**

* No disruption detected
* No claim is created
* Process ends

**If any threshold is exceeded:**

* Disruption is detected
* (Rain / Heat / AQI / Social)

---

### Step 4: Claim Creation

* A claim is automatically created
* Status is set to: **Pending**
* Claim includes:

  * Trigger type
  * User data

---

### Step 5: ML & Fraud Analysis

* Claim data is sent to ML model
* System calculates:

  * **Risk Score (0–1)**
  * **Fraud Score (0–1)**

---

### Step 6: Fraud Check

**If Fraud Score > 0.7:**

* Claim is marked as **Suspicious**
* Sent to admin with high priority

**If Fraud Score ≤ 0.7:**

* Claim is sent to admin for normal review

---

### Step 7: Admin Decision

Admin reviews:

* Risk score
* Fraud score
* Trigger type
* Claim reason

**Admin can:**

* Approve
* Reject

---

### Step 8: Final Outcome

**If Rejected:**

* Claim is closed
* Dashboard is updated
* No payout issued

**If Approved:**

* Payout is calculated:

`Payout = Avg Daily Income × Disruption Severity`

* Wallet balance is updated
* Dashboard reflects updated status

---

### Final Summary Flow

User → Data Collection → Disruption Check → Claim Creation → ML + Fraud Analysis → Admin Review → Payout / Rejection

---


## 17. Database

All application data is stored and managed using MongoDB.

Includes:

* User actions
* Trigger events
* Approval records
* Analytics data

Ensures persistent storage and enables analytics to be available across sessions and future logins.

---

## 18. Installation & Setup Guide

Follow these steps to run the project locally:

### Prerequisites

Ensure the following are installed:

* Node.js (v18+)
* npm (comes with Node.js)
* Python (3.9+)
* pip (Python package manager)
* MongoDB (local or MongoDB Atlas)
* Git

---

## Project Structure

* `client` → Frontend (React)
* `server` → Backend (Node.js / Express)
* `ml-service` → ML Microservice (Python)

---

## Run the Project

### 1. Backend (Server)

```bash
cd server
npm install
npm run dev
```

---

### 2. Frontend (Client)

```bash
cd client
npm install
npm run dev
```

---

### 3. ML Microservice

```bash
cd ml-service
pip install -r requirements.txt
python app.py
```

---

## System Flow Order

The services should be started and interact in the following order:

**Frontend → Backend → ML Service → Database (MongoDB)**

---

## 19. Requirements

### Backend Dependencies

* Express.js
* Mongoose
* dotenv
* node-cron

### Frontend Dependencies

* React
* Axios
* Chart libraries (for analytics)

### ML Service Dependencies

* Flask / FastAPI
* scikit-learn
* pandas
* numpy

---
## 📊 Pitch Deck Access

## 🎥 Project Demo Video

## 🌐 Live Deployment
