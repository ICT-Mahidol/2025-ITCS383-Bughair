# 2025-ITCS383-Bughair
**Fitness Course Management System**  
ITCS383 Software Construction and Evolution — Phase 1  
Mahidol University ICT

---

## About

A web-based Fitness Management System consisting of multiple services: authentication & membership, course management, admin management, and payment. Built with Node.js/Express backends and HTML/JavaScript frontends.

---

## Repository Structure

```
2025-ITCS383-Bughair/
├── designs/                          # D1 — C4 diagrams and design rationale
├── implementations/
│   ├── Admin/                        # Admin management service
│   │   ├── backend/backend/          # Express.js backend
│   │   ├── front/                    # Admin frontend
│   │   ├── package.json
│   │   └── package-lock.json
│   │
│   ├── AuthMembership/               # Authentication & membership service
│   │   ├── backend-api_Module1/      # Express.js backend API
│   │   └── frontend/                 # Auth/membership frontend
│   │
│   ├── course-service/               # Course management service
│   │   ├── frontend/                 # Course frontend
│   │   ├── src/                      # Backend source code
│   │   ├── tests/                    # Jest unit tests
│   │   ├── .env.example              # Environment variable template
│   │   └── package.json
│   │
│   ├── payment-service/              # Payment service
│   │   ├── data/                     # Data files
│   │   ├── src/                      # Backend source code
│   │   └── fitness-payment-frontend.html
│   │
│   └── reservation-service/          # Reservation service
│
├── .github/workflows/                # GitHub Actions CI pipeline
├── Bughair_D3_AILog.md               # D3 — AI Usage Log
├── Bughair_D4_QualityReport.md       # D4 — Quality Evidence Report
├── sonar-project.properties          # SonarQube configuration
└── README.md
```

---

## Prerequisites

- [Node.js](https://nodejs.org/) v18 or higher
- npm (comes with Node.js)

Verify your installation:

```bash
node --version
npm --version
```

---

## Services

The system is composed of the following services. Each service runs independently.

---

### 1. AuthMembership Service

Handles user authentication, registration, and membership management.

**Setup & Run:**

```bash
cd implementations/AuthMembership/backend-api_Module1
npm install
node server.js
```

**Default URL:** `http://localhost:8080`

**Frontend:**  
Open `implementations/AuthMembership/frontend/` in your browser.

---

### 2. Course Service

Handles fitness course listings, enrollment, and schedule management.

**Setup:**

```bash
cd implementations/course-service
cp .env.example .env   # configure environment variables
npm install
```

**Run:**

```bash
npm start
```

**Frontend:**  
Open `implementations/course-service/frontend/` in your browser.

---

### 3. Admin Service

Handles administrative operations such as managing users and system settings.

**Setup & Run:**

```bash
cd implementations/Admin
npm install
node backend/backend/server.js
```

**Frontend:**  
Open `implementations/Admin/front/` in your browser.

---

### 4. Payment Service

Handles membership payment processing.

**Setup & Run:**

```bash
cd implementations/payment-service
npm install
node src/server.js
```

**Frontend:**  
Open `implementations/payment-service/fitness-payment-frontend.html` in your browser.

---

### 5. Reservation Service

Handles course slot reservations.

```bash
cd implementations/reservation-service
npm install
npm start
```

---

## Running Tests

Tests are located in the `course-service`:

```bash
cd implementations/course-service
npm test
```

Tests are written with [Jest](https://jestjs.io/) and [Supertest](https://github.com/ladjs/supertest), covering course listing, member enrollment/unenrollment, authentication, and admin authorisation.

---

## Environment Variables

The `course-service` uses a `.env` file. Copy the example file and fill in the values:

```bash
cp implementations/course-service/.env.example implementations/course-service/.env
```

Key variables:

| Variable | Description |
|----------|-------------|
| `PORT` | Port for the course service (default: `8080`) |
| `JWT_SECRET` | Secret key for JWT signing |

---

## CI/CD Pipeline

GitHub Actions automatically builds, tests, and analyses code on every push to `master`.

Pipeline steps:
1. Install dependencies (`npm install`)
2. Run unit tests (`npm test`)
3. Run SonarQube static analysis

See `.github/workflows/` for the workflow configuration.

---

## Code Quality

Static analysis is performed using [SonarQube Community](https://www.sonarsource.com/products/sonarqube/).

- Quality Gate: **Passed**
- See `Bughair_D4_QualityReport.md` for the full quality evidence report.

---

## Team

**Group:** Bughair  
**Course:** ITCS383 Software Construction and Evolution  
**Institution:** Faculty of ICT, Mahidol University  
