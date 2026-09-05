# ArthSetu — Autonomous AI Revenue Recovery OS

> **Recover missed revenue with intelligent, policy-aware automation.**

**ArthSetu** is an AI-powered Revenue Recovery Operating System designed to identify revenue leakage, diagnose payment failures, select the best recovery strategy, execute recovery actions safely, and provide complete auditability.

Built for the **Razorpay AI Buildathon 2026 — Track 03: AI Revenue Recovery**.

---

## 🚀 Overview

Revenue can be lost due to:

* Failed payments
* Temporary banking failures
* Subscription payment failures
* Checkout abandonment
* Overdue invoices
* Repeated unsuccessful payment attempts

ArthSetu addresses these problems through an end-to-end intelligent recovery pipeline:

```text
Revenue Event
     ↓
Risk Detection
     ↓
AI Diagnosis
     ↓
Recovery Strategy
     ↓
Deterministic Policy Engine
     ↓
Action Execution
     ↓
Audit Trail
     ↓
Revenue Measurement
```

The core philosophy is:

> **AI Decides → Policy Controls → System Executes → Metrics Prove**

---

## ✨ Key Features

### 🤖 AI-Powered Revenue Recovery

ArthSetu uses multiple specialized agents:

* **Risk Detector Agent** — Identifies revenue-risk events.
* **Diagnosis Agent** — Determines failure category, severity, recoverability, and confidence.
* **Recovery Strategist Agent** — Compares possible recovery actions using expected utility.
* **Hinglish Communicator Agent** — Generates personalized Hindi-English customer communication.
* **Orchestrator** — Coordinates the complete recovery workflow.

### 🛡️ Deterministic Policy Engine

AI recommendations cannot directly execute financial actions.

Every action must pass through a deterministic policy layer containing rules such as:

* Retry limits
* Risk thresholds
* Duplicate-event protection
* Suspicious-pattern detection
* Customer opt-out protection
* High-value case approval
* API failure handling
* Human escalation

Rules are identified as:

```text
RULE-001 → RULE-010
```

---

### 💳 Payment Gateway Integration

The system supports:

* Razorpay Test Mode
* Mock Payment Adapter
* Controlled failure injection
* Payment-link fallback
* Retry execution

This makes the system suitable for both demonstrations and controlled evaluation.

---

### 👤 Human-in-the-Loop Governance

High-value or high-risk recovery actions can be routed to human operators.

RBAC roles include:

| Role      | Capabilities                     |
| --------- | -------------------------------- |
| `ADMIN`   | Full system control              |
| `MANAGER` | Approvals, strategies, analytics |
| `ANALYST` | Case analysis and simulations    |
| `VIEWER`  | Read-only access                 |

---

### 🔐 Cryptographic Audit Trail

Every important system event is recorded with:

* Timestamp
* Correlation ID
* Actor
* Input snapshot
* Output snapshot
* Rule ID
* Execution status

Audit events use a **SHA-256 hash chain** to provide tamper-evident history.

---

## 🧠 Recovery Strategy

ArthSetu evaluates multiple recovery options:

```text
IMMEDIATE_RETRY
DELAYED_RETRY
PAYMENT_LINK
HUMAN_ESCALATION
```

The strategy engine uses an expected-utility approach:

```text
Utility =
P(Recovery) × Revenue Amount − Action Cost
```

The highest-value safe strategy is selected, subject to deterministic policy rules.

---

## 🏗️ System Architecture

```text
                         ┌─────────────────────┐
                         │   Revenue Event     │
                         └──────────┬──────────┘
                                    ↓
                         ┌─────────────────────┐
                         │   Risk Detector     │
                         └──────────┬──────────┘
                                    ↓
                         ┌─────────────────────┐
                         │   Diagnosis Agent   │
                         └──────────┬──────────┘
                                    ↓
                         ┌─────────────────────┐
                         │ Recovery Strategist │
                         └──────────┬──────────┘
                                    ↓
                         ┌─────────────────────┐
                         │ Deterministic Policy│
                         │       Engine        │
                         └──────────┬──────────┘
                                    ↓
                         ┌─────────────────────┐
                         │   Action Executor   │
                         └──────────┬──────────┘
                                    ↓
                  ┌─────────────────┴─────────────────┐
                  ↓                                   ↓
        ┌───────────────────┐               ┌──────────────────┐
        │ Razorpay Test     │               │ Mock Payment     │
        │ Adapter           │               │ Adapter          │
        └───────────────────┘               └──────────────────┘
                                    ↓
                         ┌─────────────────────┐
                         │   Audit & Metrics   │
                         └─────────────────────┘
```

---

## 📁 Project Structure

```text
ArthSetu/
│
├── agents/
│   ├── diagnosis_agent.py
│   ├── Hinglish_communicator.py
│   ├── orchestrator.py
│   ├── risk_detector.py
│   └── strategist.py
│
├── backend/
│   ├── app/
│   │   ├── adapters/
│   │   ├── core/
│   │   ├── models/
│   │   ├── schemas/
│   │   └── main.py
│   └── requirements.txt
│
├── evaluation/
│   ├── baseline_model.py
│   ├── dataset_generator.py
│   └── evaluator.py
│
├── frontend/
│   ├── app/
│   ├── components/
│   ├── package.json
│   └── ...
│
├── policy_engine/
│   ├── engine.py
│   └── rules.py
│
├── tests/
│   └── test_api_system.py
│
├── API.md
├── ARCHITECTURE.md
├── DATABASE.md
├── DEMO.md
├── EVALUATION.md
├── FAILURES.md
├── SECURITY.md
├── RUN_AND_SETUP.md
├── docker-compose.yml
├── .env.example
└── README.md
```

---

## 🛠️ Tech Stack

### Backend

* Python
* FastAPI
* Pydantic
* SQLAlchemy
* Uvicorn
* PyTest

### Frontend

* Next.js 14
* React 18
* TypeScript
* Tailwind CSS
* Recharts
* Lucide React

### Database

* SQLite for local/demo usage
* PostgreSQL supported for deployment

### Payment

* Razorpay Test Mode
* Mock Payment Adapter

### Security

* JWT authentication
* Role-Based Access Control
* SHA-256 password hashing
* Cryptographic audit hash chain

---

# ⚡ Quick Start

## 1. Clone the Repository

```bash
git clone https://github.com/YOUR_USERNAME/arthsetu.git
cd arthsetu
```

---

## 2. Create Python Environment

### Windows

```powershell
python -m venv .venv
.venv\Scripts\activate
```

### macOS / Linux

```bash
python3 -m venv .venv
source .venv/bin/activate
```

---

## 3. Install Backend Dependencies

```bash
pip install -r backend/requirements.txt
```

---

## 4. Configure Environment Variables

Create a `.env` file from the example:

```bash
cp .env.example .env
```

For Windows PowerShell:

```powershell
Copy-Item .env.example .env
```

Example configuration:

```env
MODE=DEMO_MODE
DATABASE_URL=sqlite:///./arthsetu.db
API_KEY=replace_with_a_secure_random_key
RAZORPAY_KEY_ID=rzp_test_your_key_id
RAZORPAY_KEY_SECRET=your_test_secret
```

> **Never commit `.env` or real payment credentials to GitHub.**

---

# 🗄️ Database Setup

Seed the demo database:

```powershell
$env:PYTHONPATH="."
python -c "import backend.app.core.seed as s; s.seed_database()"
```

For macOS/Linux:

```bash
PYTHONPATH=. python -c "import backend.app.core.seed as s; s.seed_database()"
```

---

# 🔧 Start Backend

Run the FastAPI server:

```bash
python -m uvicorn backend.app.main:app --reload --port 8000
```

Backend will be available at:

```text
http://127.0.0.1:8000
```

Health check:

```text
http://127.0.0.1:8000/health
```

FastAPI documentation:

```text
http://127.0.0.1:8000/docs
```

---

# 🎨 Start Frontend

Open another terminal:

```bash
cd frontend
npm install
npm run dev
```

Open:

```text
http://localhost:3000
```

---

# 🔑 Demo Accounts

The application includes seeded demo users:

| Role    | Email                | Password       |
| ------- | -------------------- | -------------- |
| ADMIN   | `admin@artsetu.ai`   | `ArtSetu2026!` |
| MANAGER | `manager@artsetu.ai` | `ArtSetu2026!` |
| ANALYST | `analyst@artsetu.ai` | `ArtSetu2026!` |
| VIEWER  | `viewer@artsetu.ai`  | `ArtSetu2026!` |

> These credentials are intended for local/demo environments only. Change or remove them before production deployment.

---

# 🧪 Run Tests

Run the complete test suite:

```bash
python -m pytest tests/
```

The tests cover areas including:

* Authentication
* RBAC
* Policy rules
* API endpoints
* Recovery workflows
* Audit integrity

---

# 📊 Evaluation

ArthSetu includes a synthetic batch evaluation framework.

### Dataset

The evaluation contains:

```text
10,000 synthetic revenue-risk events
```

Event distribution:

| Event Type            | Percentage |
| --------------------- | ---------: |
| Payment Failures      |        65% |
| Subscription Failures |        20% |
| Checkout Abandonment  |        10% |
| Overdue Invoices      |         5% |

### Data Split

```text
60% Training
20% Validation
20% Held-Out Test
```

### Benchmark

| Metric                     |     Result |
| -------------------------- | ---------: |
| Revenue at Risk            |    ₹34.38M |
| Baseline Recovered Revenue |    ₹15.99M |
| ArthSetu Recovered Revenue |    ₹19.32M |
| Incremental Revenue        |     ₹3.33M |
| Recovery Uplift            | **20.82%** |
| F1 Score                   | **0.8604** |
| ArthSetu Policy Violations |      **0** |
| Baseline Policy Violations |        626 |

The evaluation demonstrates the potential benefit of combining AI-driven diagnosis and strategy selection with deterministic financial safety controls.

---

# 🔄 Example Recovery Workflow

A failed payment enters the system:

```json
{
  "payment_id": "pay_demo",
  "amount": 8499,
  "retry_count": 0,
  "failure_reason": "bank_timeout"
}
```

ArthSetu processes the event:

```text
1. Detect revenue risk
        ↓
2. Diagnose failure
        ↓
3. Calculate recoverability
        ↓
4. Generate recovery strategies
        ↓
5. Select optimal strategy
        ↓
6. Validate against policy rules
        ↓
7. Execute recovery
        ↓
8. Record audit event
        ↓
9. Measure recovered revenue
```

If automated recovery is unsafe or fails, the system can trigger:

```text
Payment Link
      OR
Human Escalation
```

---

# 💰 Revenue Recovery Philosophy

Traditional payment systems often follow:

```text
Payment Failed
      ↓
Retry
      ↓
Retry
      ↓
Retry
```

ArthSetu instead follows:

```text
Payment Failed
      ↓
Why did it fail?
      ↓
Can it be recovered?
      ↓
What is the best action?
      ↓
Is the action allowed?
      ↓
Execute safely
      ↓
Measure the outcome
```

This reduces unnecessary retries while improving recovery decisions.

---

# 🛡️ Safety & Governance

ArthSetu is designed around financial safety principles:

### Deterministic Policy Enforcement

AI cannot override policy rules.

### Bounded Automation

Repeated failures and unsafe conditions can stop automation.

### Human Escalation

High-risk/high-value cases can require manager approval.

### Duplicate Protection

Duplicate events can be detected before action execution.

### Customer Opt-Out

Customer preferences can prevent automated recovery communication.

### Auditability

Every major state transition is recorded for investigation and compliance.

---

# 🌐 API

Major API groups include:

```text
/api/v1/auth
/api/v1/dashboard
/api/v1/recovery
/api/v1/strategies
/api/v1/simulations
/api/v1/policy
/api/v1/approvals
/api/v1/audit
/api/v1/analytics
/api/v1/notifications
```

See [`API.md`](./API.md) for the complete API specification.

---

# 🎬 Demo

The recommended demonstration flow is:

```text
Landing Page
     ↓
Login
     ↓
Executive Dashboard
     ↓
Recovery Queue
     ↓
Open Failed Payment
     ↓
AI Diagnosis
     ↓
Strategy Simulator
     ↓
Policy Validation
     ↓
Execute Recovery
     ↓
Audit Trail
     ↓
Evaluation Dashboard
```

See [`DEMO.md`](./DEMO.md) for the complete 5-minute demonstration script.

---

# 📚 Documentation

| Document                                 | Description                              |
| ---------------------------------------- | ---------------------------------------- |
| [`ARCHITECTURE.md`](./ARCHITECTURE.md)   | System architecture and technical design |
| [`API.md`](./API.md)                     | REST API documentation                   |
| [`DATABASE.md`](./DATABASE.md)           | Database design                          |
| [`DEMO.md`](./DEMO.md)                   | Hackathon demo script                    |
| [`EVALUATION.md`](./EVALUATION.md)       | Evaluation methodology and results       |
| [`FAILURES.md`](./FAILURES.md)           | Failure scenarios and handling           |
| [`SECURITY.md`](./SECURITY.md)           | Security considerations                  |
| [`RUN_AND_SETUP.md`](./RUN_AND_SETUP.md) | Detailed setup guide                     |

---

# 🚧 Production Considerations

This repository contains a hackathon/demo implementation.

Before production deployment, consider:

* Secure secret management
* Production-grade authentication
* HTTPS/TLS
* Real payment gateway credentials management
* PostgreSQL deployment
* Rate limiting
* Monitoring and alerting
* Distributed job processing
* Comprehensive observability
* Formal financial compliance review
* Stronger test coverage
* Production-grade customer consent management

---

# 🔒 Security

Do not commit:

```text
.env
API keys
JWT secrets
Razorpay credentials
Production database credentials
Customer payment information
```

Use `.env.example` as the configuration template.

If you discover a security issue, please report it privately rather than publicly opening an issue containing sensitive information.

---

# 🧑‍💻 Development

Recommended workflow:

```bash
# Backend
python -m uvicorn backend.app.main:app --reload --port 8000

# Frontend
cd frontend
npm run dev

# Tests
python -m pytest tests/
```

---

# 🏆 Hackathon Highlights

ArthSetu demonstrates:

* Multi-agent AI architecture
* Revenue-risk detection
* Explainable failure diagnosis
* Utility-based strategy optimization
* Deterministic financial policy enforcement
* Human-in-the-loop approvals
* Razorpay Test Mode integration
* Payment-link fallback
* Cryptographic auditability
* Synthetic batch evaluation
* Revenue recovery measurement
* Modern enterprise dashboard

---

# 📌 Project Status

**Status:** Hackathon Prototype / Demo Ready

**Track:** Razorpay AI Buildathon 2026 — Track 03

**Focus:** AI Revenue Recovery

---

# 👥 Contributors

Add your team members here:

```text
Prem Mahadik — AI / Backend
Shivali Panchal — Frontend
Rushil Purohit — ML / Evaluation
```

---

# 📄 License

Add the appropriate license for your project, for example:

```text
MIT License
```

if you intend to release the repository under MIT.

---

## ⭐ If You Find This Project Interesting

Give the repository a ⭐ and feel free to explore the architecture, recovery agents, policy engine, and evaluation framework.

**ArthSetu — Turning revenue leakage into recoverable revenue.**
