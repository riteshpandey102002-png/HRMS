# HRMS Lite

A lightweight Human Resource Management System for managing employee records and tracking daily attendance.

## Tech Stack

| Layer      | Technology                     |
| ---------- | ------------------------------ |
| Frontend   | React 19, Vite, Tailwind CSS 4 |
| Backend    | Python, FastAPI                |
| Database   | MongoDB (Motor async driver)   |
| Icons      | Lucide React                   |

## Features

### Core
- **Employee Management** - Add, view, and delete employees with validation (unique ID, email format, duplicate handling)
- **Attendance Tracking** - Mark daily attendance (Present/Absent) per employee with duplicate prevention

### Bonus
- **Dashboard** - Summary cards showing total employees, today's attendance breakdown
- **Date Filter** - Filter attendance records by date
- **Employee Filter** - Filter attendance by employee
- **Present Days Count** - Display total present days per employee

## Project Structure

```
HRMS-Lite/
├── backend/
│   ├── app/
│   │   ├── main.py           # FastAPI app entry point
│   │   ├── database.py       # MongoDB connection
│   │   ├── models/           # Pydantic models
│   │   └── routes/           # API endpoints
│   ├── requirements.txt
│   └── .env
├── frontend/
│   ├── src/
│   │   ├── api/              # Axios HTTP client
│   │   ├── components/       # Reusable UI components
│   │   └── pages/            # Page components
│   └── package.json
└── README.md
```

## Prerequisites

- **Node.js** >= 18
- **Python** >= 3.10
- **MongoDB** running locally on port 27017

## Steps to Run Locally

### 1. Clone the repository

```bash
git clone <repo-url>
cd HRMS-Lite
```

### 2. Start MongoDB

Make sure MongoDB is running locally:

```bash
mongod
```

### 3. Backend Setup

```bash
cd backend
python -m venv venv
source venv/bin/activate    # On Windows: venv\Scripts\activate
pip install -r requirements.txt
uvicorn app.main:app --reload --port 8000
```

The API will be available at `https://www.hrms-backend.theritesh.in`. Visit `https://www.hrms-backend.theritesh.in/docs` for Swagger UI.

### 4. Frontend Setup

```bash
cd frontend
npm install
npm run dev
```

The app will be available at `http://localhost:5173`.

## API Endpoints

| Method | Endpoint                          | Description                     |
| ------ | --------------------------------- | ------------------------------- |
| GET    | `/api/employees`                  | List all employees              |
| POST   | `/api/employees`                  | Create a new employee           |
| GET    | `/api/employees/{employee_id}`    | Get employee by ID              |
| DELETE | `/api/employees/{employee_id}`    | Delete employee and attendance  |
| GET    | `/api/attendance`                 | List attendance (filterable)    |
| POST   | `/api/attendance`                 | Mark attendance                 |
| GET    | `/api/attendance/employee/{id}`   | Get attendance for an employee  |
| GET    | `/api/attendance/summary/today`   | Today's attendance summary      |

## Assumptions & Limitations

- Single admin user; no authentication required
- Leave management, payroll, and advanced HR features are out of scope
- MongoDB must be running before starting the backend
- Attendance can only be marked once per employee per date
# HRMS
