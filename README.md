<div align="center">

# 🏥 Virtual Clinix
### *Pakistan's Modern Telemedicine Platform*

![React](https://img.shields.io/badge/React-19.x-61DAFB?style=for-the-badge&logo=react&logoColor=black)
![Vite](https://img.shields.io/badge/Vite-8.x-646CFF?style=for-the-badge&logo=vite&logoColor=white)
![Supabase](https://img.shields.io/badge/Supabase-Backend-3ECF8E?style=for-the-badge&logo=supabase&logoColor=white)
![Redux Toolkit](https://img.shields.io/badge/Redux_Toolkit-State_Mgmt-764ABC?style=for-the-badge&logo=redux&logoColor=white)
![TailwindCSS](https://img.shields.io/badge/Tailwind_CSS-4.x-06B6D4?style=for-the-badge&logo=tailwindcss&logoColor=white)

**A full-stack telemedicine web application featuring live video consultations, AI-assisted appointment scheduling, digital e-prescriptions, and secure role-based portals for Patients, Doctors, and Administrators.**

</div>

---

# 📋 Table of Contents

- [Features](#-features)
- [Tech Stack](#-tech-stack)
- [Architecture](#-architecture--database-schema)
- [Getting Started](#-getting-started)
- [Environment Variables](#-environment-variables)
- [Project Structure](#-project-structure)
- [Authentication & Security](#-authentication--security)
- [Git Workflow](#-git-branching-strategy)
- [Implementation Report](#-virtual-clinix-project-implementation-report)
- [Team](#-team)

---

# ✨ Features

## 👤 Patient Portal

- Secure Registration & Login
- Doctor Discovery & Filtering
- Online Appointment Booking
- Live Video Consultation (Jitsi Meet)
- Digital Prescriptions
- Profile Management

## 🩺 Doctor Portal

- Doctor Dashboard
- Patient Directory
- Live Consultation Room
- E-Prescription Writer
- Session Timer & Controls

## 🛡️ Admin Portal

- Doctor Verification Queue
- Analytics Dashboard
- User Management
- System Health Monitoring

---

# 🛠️ Tech Stack

| Category | Technology |
|---|---|
| Frontend | React 19 + Vite 8 |
| Styling | TailwindCSS 4 |
| State Management | Redux Toolkit |
| Routing | React Router DOM v7 |
| Backend | Supabase |
| Database | PostgreSQL |
| Validation | React Hook Form + Zod |
| Video Calls | Jitsi Meet API |
| Charts | Recharts |

---

# 🏗️ Architecture & Database Schema

```text
┌──────────────────────────────────────────────┐
│                 profiles                     │
│ id · full_name · role · created_at           │
└──────────────────┬───────────────────────────┘
                   │
        ┌──────────┴───────────┐
        │                      │

┌───────▼───────────┐   ┌──────▼──────────────┐
│   doctors_info    │   │    appointments     │
│ specialty · fee   │   │ patient_id          │
│ rating · city     │   │ doctor_id           │
│ verified          │   │ appointment_date    │
└───────────────────┘   └─────────────────────┘
```

---

# 🚀 Getting Started

## 1. Clone Repository

```bash
git clone https://github.com/YOUR_USERNAME/virtual-clinix.git
cd virtual-clinix
```

## 2. Install Dependencies

```bash
npm install
```

## 3. Setup Supabase

- Open Supabase Dashboard
- Go to SQL Editor
- Run `supabase/schema.sql`

## 4. Create Environment File

Create `.env.local`

```env
VITE_SUPABASE_URL=your_project_url
VITE_SUPABASE_ANON_KEY=your_anon_key
```

## 5. Run Development Server

```bash
npm run dev
```

Open:

```text
http://localhost:5173
```

---

# 📁 Project Structure

```text
virtual-clinix/
├── public/
├── src/
│   ├── components/
│   ├── pages/
│   ├── store/
│   ├── lib/
│   ├── App.jsx
│   └── main.jsx
├── supabase/
├── package.json
└── vite.config.js
```

---

# 🔐 Authentication & Security

- JWT Authentication using Supabase Auth
- ProtectedRoute Guards
- Role-Based Access Control
- Row Level Security (RLS)
- Environment Variable Protection

---

# 🌿 Git Branching Strategy

```text
main
 └── develop
      ├── feature/realtime-notifications
      ├── feature/typescript-migration
      └── feature/pwa-support
```

---

# 📊 Virtual Clinix Project Implementation Report

| Task | Status |
|---|---|
| Redux Wiring | ✅ Completed |
| Backend Integration | ✅ Completed |
| Protected Routing | ✅ Completed |
| Video Call Integration | ✅ Completed |
| Form Validations | ✅ Completed |
| UI/Avatar Improvements | ✅ Completed |

---

# 🎥 Jitsi Meet Integration

- Dynamic room joining
- Shared doctor/patient session rooms
- Audio/Video Controls
- Hangup & Session End Handling

---

# ✅ Form Validation

Implemented using:

- React Hook Form
- Zod Schemas
- Real-time Validation Feedback

---

# 🎨 UI Improvements

Integrated Dicebear avatars:

```text
https://api.dicebear.com/7.x/adventurer/svg?seed=username
```

---

# 🛠️ Build Verification

```bash
npm run build
```

✅ Build Successful  
✅ No Syntax Errors  
✅ Production Ready

---

# 🤝 Contributing

1. Fork Repository
2. Create Feature Branch
3. Commit Changes
4. Push Changes
5. Open Pull Request

---

# 👨‍💻 Team

| Role | Name |
|---|---|
| Lead Developer | Asim |
| University | UET Pakistan |
| Course | Software Engineering |

---

<div align="center">

## ❤️ Made with Passion at UET Pakistan

### *Virtual Clinix — Bringing Quality Healthcare to Every Home*

</div>
