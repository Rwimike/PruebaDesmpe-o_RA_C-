# 🏥 San Vicente Hospital — Medical Appointment Management System

## 👨‍💻 Developer Information
- **Name:** Miguel Ángel (Migue)
- **Clan:** Be a CoderNN  
- **Email:** migue.coder@example.com  
- **ID Document:** 123456789  

---

## 📖 Project Overview

**San Vicente Hospital** is a web-based medical appointment management system built with **ASP.NET Core MVC** and **Entity Framework Core (EF Core)** using a **PostgreSQL** database.  
It allows administrators to manage patients, doctors, and appointments while automatically sending **email confirmations** using SMTP.  

The project follows good software architecture practices and uses **Bootstrap** for styling and **SweetAlert** for user-friendly notifications.

---

## ⚙️ Tech Stack

| Layer | Technology |
|-------|-------------|
| Backend | ASP.NET Core MVC (.NET 8) |
| Database | PostgreSQL |
| ORM | Entity Framework Core |
| Frontend | Bootstrap 5 + SweetAlert |
| Email Service | SMTP (configurable via `.env`) |
| Environment | Docker (optional) |

---

## 🧰 Prerequisites

Before running this project, make sure you have the following installed:

- [.NET SDK 8.0+](https://dotnet.microsoft.com/en-us/download)
- [PostgreSQL 15+](https://www.postgresql.org/download/)
- [Docker Desktop](https://www.docker.com/products/docker-desktop) *(optional but recommended)*
- [Git](https://git-scm.com/downloads)
- An SMTP account (e.g., Gmail) with [App Passwords enabled](https://myaccount.google.com/apppasswords)

---

## 🧩 Project Structure

```

SanVicente/
│
├── Controllers/
│   ├── AppointmentController.cs
│   ├── DoctorController.cs
│   └── PatientController.cs
│
├── Data/
│   └── PostgresDbContext.cs
│
├── Models/
│   ├── Appointment.cs
│   ├── Doctor.cs
│   ├── EmailHistory.cs
│   └── Patient.cs
│
├── Services/
│   └── EmailService.cs
│
├── Views/
│   ├── Shared/
│   │   └── _Layout.cshtml
│   ├── Appointment/
│   │   ├── Index.cshtml
│   │   ├── Create.cshtml
│   │   └── History.cshtml
│   ├── Doctor/
│   │   ├── Index.cshtml
│   │   ├── Create.cshtml
│   │   └── Edit.cshtml
│   └── Patient/
│       ├── Index.cshtml
│       ├── Create.cshtml
│       └── Edit.cshtml
│
├── .env
├── appsettings.json
├── Program.cs
└── README.md

````

---

## 🪄 Environment Configuration

You should **never** hardcode credentials in your source code.  
Instead, create a `.env` file in the project root with the following values:

```env
# PostgreSQL connection
CONNECTION_STRING=Host=localhost;Port=5432;Database=SanVicenteDB;Username=postgres;Password=your_password;

# SMTP configuration
SMTP_SERVER=smtp.gmail.com
SMTP_PORT=587
SMTP_USERNAME=your_email@gmail.com
SMTP_PASSWORD=your_app_password
````

> ⚠️ For Gmail accounts, you must create an [App Password](https://myaccount.google.com/apppasswords)
> after enabling **2-Step Verification** in your Google Account.

---

## 🚀 How to Run the Project

### 1. Clone the repository

```bash
git clone https://github.com/yourusername/SanVicente.git
cd SanVicente
```

### 2. Configure environment variables

Create a `.env` file in the project root using the example above.

### 3. Install dependencies

```bash
dotnet restore
```

### 4. Apply database migrations

```bash
dotnet ef database update
```

*(Make sure your PostgreSQL server is running.)*

### 5. Run the project

```bash
dotnet run
```

The app will start at:
👉 [http://localhost:5000](http://localhost:5000)
or
👉 [https://localhost:7000](https://localhost:7000)

---

## 🧪 Docker Setup (Optional)

If you prefer running PostgreSQL in Docker:

```bash
docker run --name postgres-sv \
-e POSTGRES_USER=postgres \
-e POSTGRES_PASSWORD=your_password \
-e POSTGRES_DB=SanVicenteDB \
-p 5432:5432 \
-d postgres
```

Then, update your `.env` connection string accordingly.

example for a docker ps on bash 'docker run --name some-postgres -p 5432:5432 -e POSTGRES_PASSWORD=password -d postgres'

---

## 📬 Email Sending

When an appointment is successfully created:

* The system automatically sends a confirmation email to the patient.
* All sent or failed emails are stored in the `EmailHistories` table for auditing.

---

## 🧭 Application Features

### 👨‍⚕️ Doctors

* Create, edit, or deactivate doctors.
* Filter by specialization.
* Toggle between **Active** and **Inactive** doctors.

### 🧍‍♂️ Patients

* Register new patients with validation rules.
* Edit or view patient information.
* Email format and duplicate document validation.

### 📅 Appointments

* Schedule new appointments.
* Validate conflicts and working hours.
* Cancel or mark appointments as completed.
* Send email confirmation.
* View appointment history.

---

## 💡 Usual Errors

| Problem                          | Solution                                                    |
| -------------------------------- | ----------------------------------------------------------- |
| `timestamp with time zone` error | Convert `DateHour` to UTC before saving.                    |
| Email not sending                | Check `.env` SMTP credentials or enable "Less secure apps". |
| Database connection failed       | Verify PostgreSQL is running and credentials match.         |

---

## 📚 License

This project is licensed under the **MIT License** — feel free to use and modify it.

Would you like me to also include a **ready-to-copy `.env.example`** file and a **sample Dockerfile + docker-compose.yml** for a full containerized setup? That would make your README even more professional and runnable in one command.
```
