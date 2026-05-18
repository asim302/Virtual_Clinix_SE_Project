<div align="center">
# 🏥 Virtual Clinix
### *Pakistan's Modern Telemedicine Platform*
[![React](https://img.shields.io/badge/React-19.x-61DAFB?style=for-the-badge&logo=react&logoColor=black)](https://react.dev)
[![Vite](https://img.shields.io/badge/Vite-8.x-646CFF?style=for-the-badge&logo=vite&logoColor=white)](https://vite.dev)
[![Supabase](https://img.shields.io/badge/Supabase-Backend-3ECF8E?style=for-the-badge&logo=supabase&logoColor=white)](https://supabase.com)
[![Redux Toolkit](https://img.shields.io/badge/Redux_Toolkit-State_Mgmt-764ABC?style=for-the-badge&logo=redux&logoColor=white)](https://redux-toolkit.js.org)
[![TailwindCSS](https://img.shields.io/badge/Tailwind_CSS-4.x-06B6D4?style=for-the-badge&logo=tailwindcss&logoColor=white)](https://tailwindcss.com)
[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg?style=for-the-badge)](LICENSE)
**A full-stack telemedicine web application featuring live video consultations, AI-assisted appointment scheduling, digital e-prescriptions, and role-based secure portals for Patients, Doctors, and Administrators.**
[🚀 Live Demo](#) · [📖 Documentation](./HOW_IT_WORKS.md) · [🐛 Report Bug](../../issues) · [✨ Request Feature](../../issues)
---
</div>
## 📋 Table of Contents
- [✨ Features](#-features)
- [🛠️ Tech Stack](#️-tech-stack)
- [🏗️ Architecture & Database Schema](#️-architecture--database-schema)
- [🚀 Getting Started](#-getting-started)
- [⚙️ Environment Variables](#️-environment-variables)
- [📁 Project Structure](#-project-structure)
- [🔐 Authentication & Security](#-authentication--security)
- [🌿 Git Branching Strategy](#-git-branching-strategy)
- [🤝 Contributing](#-contributing)
- [👨‍💻 Team](#-team)
---
## ✨ Features
### 👤 Patient Portal
- **Secure Registration & Login** — Email/password auth with Zod schema validation
- **Doctor Discovery** — Browse and filter verified doctors by specialty and fee
- **Online Appointment Booking** — Date, time, and reason selection with real-time confirmation
- **Live Video Consultation** — One-click join via Jitsi Meet (no download required)
- **Digital Prescriptions** — View e-prescriptions issued directly by doctors
- **Profile Management** — Update personal info and notification preferences
### 🩺 Doctor Portal
- **Dedicated Dashboard** — View all scheduled and completed appointments at a glance
- **Patient Directory** — Full clinical history and contact details per patient
- **Live Video Room** — Join patient sessions via a unique, secure room ID
- **E-Prescription Writer** — Issue structured digital prescriptions with medications, dosage, and frequency
- **Session Timer** — Auto-running session clock with call controls (Mute, Camera, Hangup)
### 🛡️ Admin Portal
- **Doctor Verification Queue** — Review and Approve/Reject new doctor applications
- **Analytics Dashboard** — Real-time metrics (patients, doctors, appointments) with Recharts graphs
- **User Management** — View all registered users and manage their roles
- **System Health Monitor** — Live audit panel for API status and system uptime
---
## 🛠️ Tech Stack
| Category | Technology |
| :--- | :--- |
| **Frontend Framework** | React 19 with Vite 8 |
| **Styling** | TailwindCSS 4.x + Custom CSS Design Tokens |
| **State Management** | Redux Toolkit + React-Redux |
| **Routing** | React Router DOM v7 |
| **Backend & Database** | Supabase (PostgreSQL + Auth + RLS) |
| **Form Validation** | React Hook Form + Zod |
| **Video Calls** | Jitsi Meet External API |
| **Charts & Analytics** | Recharts |
| **Icons** | Lucide React |
| **Avatars** | Dicebear Adventurer API |
| **Build Tool** | Vite with PostCSS + Autoprefixer |
---
## 🏗️ Architecture & Database Schema
The application follows a **role-based, three-portal architecture** backed by a PostgreSQL database on Supabase with **Row Level Security (RLS)** policies to ensure data isolation.
### Database Tables
```
┌──────────────────────────────────────────────────────────────┐
│                       profiles                               │
│  id (UUID, PK) · full_name · role · created_at               │
└────────────────────────┬─────────────────────────────────────┘
                         │ 1:1
         ┌───────────────┴──────────────┐
         │                              │
┌────────▼──────────────┐   ┌──────────▼────────────────────┐
│     doctors_info      │   │         appointments           │
│  id · specialty · fee │   │  id · patient_id · doctor_id   │
│  rating · city        │   │  appointment_date · status     │
│  is_verified · about  │   │  reason · created_at           │
└───────────────────────┘   └───────────────────────────────┘
```
### Row Level Security (RLS) Policies
- **Profiles:** Users can only read/update their own profile data
- **Doctor Info:** Publicly readable; only the doctor can write to their own record
- **Appointments:** Restricted to the patient and doctor involved in that session
---
## 🚀 Getting Started
### Prerequisites
Make sure you have the following installed:
- [Node.js](https://nodejs.org/) (v18 or higher)
- npm (comes bundled with Node.js)
- A [Supabase](https://supabase.com) account (free tier is sufficient)
### 1. Clone the Repository
```bash
git clone https://github.com/YOUR_USERNAME/virtual-clinix.git
cd virtual-clinix
```
### 2. Install Dependencies
```bash
npm install
```
### 3. Setup Supabase Database
- Go to your [Supabase Dashboard](https://app.supabase.com) → **SQL Editor**
- Copy the contents of [`supabase/schema.sql`](./supabase/schema.sql) and run it to create all required tables and RLS policies.
### 4. Configure Environment Variables
Create a `.env.local` file in the project root (see [⚙️ Environment Variables](#️-environment-variables) below).
### 5. Run the Development Server
```bash
npm run dev
```
Open your browser and navigate to **`http://localhost:5173`**
### 6. Build for Production
```bash
npm run build
```
---
## ⚙️ Environment Variables
Create a `.env.local` file in the root of your project and add the following keys from your Supabase project settings:
```env
# Supabase Configuration
# Get these from: https://app.supabase.com → Project Settings → API
VITE_SUPABASE_URL=your_supabase_project_url
VITE_SUPABASE_ANON_KEY=your_supabase_anon_key
```
> **⚠️ Important:** Never commit your `.env.local` file to Git. It is already listed in `.gitignore`.
---
## 📁 Project Structure
```
virtual-clinix/
├── public/                     # Static assets
├── src/
│   ├── components/
│   │   ├── ProtectedRoute.jsx  # Auth guard for role-based routing
│   │   ├── AdminLayout.jsx     # Admin portal layout wrapper
│   │   └── DoctorLayout.jsx    # Doctor portal layout wrapper
│   ├── lib/
│   │   └── supabaseClient.js   # Supabase client initialization
│   ├── pages/
│   │   ├── LandingPage.jsx         # Public homepage
│   │   ├── AuthPage.jsx            # Patient/Doctor auth (login & register)
│   │   ├── DoctorLogin.jsx         # Doctor-specific login
│   │   ├── AdminLogin.jsx          # Admin-specific login
│   │   ├── PatientDashboard.jsx    # Patient portal home
│   │   ├── DoctorDashboard.jsx     # Doctor portal home
│   │   ├── DoctorSearchPage.jsx    # Browse & filter verified doctors
│   │   ├── BookingPage.jsx         # Appointment booking flow
│   │   ├── ConsultationRoom.jsx    # Live video room (Patient)
│   │   ├── DoctorConsultationRoom.jsx  # Live video room (Doctor)
│   │   ├── EPrescription.jsx       # Digital prescription writer
│   │   ├── DoctorPatientList.jsx   # Patient history directory
│   │   ├── ProfileSettings.jsx     # Profile management
│   │   ├── AdminAnalyticsDashboard.jsx # Platform analytics
│   │   ├── AdminDoctorVerification.jsx # Doctor approval queue
│   │   └── AdminUserManagement.jsx     # User management
│   ├── store/
│   │   ├── index.js                # Redux store + custom hooks
│   │   └── slices/
│   │       ├── authSlice.js        # Auth state & async thunks
│   │       ├── appointmentSlice.js # Appointment CRUD operations
│   │       └── doctorSlice.js      # Doctor data fetching
│   ├── App.jsx                 # Root router & route configuration
│   └── main.jsx                # React + Redux app entry point
├── supabase/
│   └── schema.sql              # Full database schema with RLS policies
├── .env.local                  # 🔒 Local secrets (not committed)
├── .gitignore
├── vite.config.js
└── package.json
```
---
## 🔐 Authentication & Security
Virtual Clinix uses **Supabase Auth** for secure, JWT-based authentication, combined with a custom **`ProtectedRoute`** component in React for frontend route guarding.
| Guard Level | Implementation |
| :--- | :--- |
| **Unauthenticated Users** | Redirected to `/auth` or specific login pages |
| **Role Mismatch** | A patient accessing `/admin` is blocked and redirected |
| **Database Level** | Supabase RLS policies enforce data ownership at query level |
| **Sensitive Keys** | Stored in `.env.local`, excluded from version control |
---
## 🌿 Git Branching Strategy
This project follows the **Git Flow** branching model:
```
main           → Production-ready stable releases
  └─ develop   → Active development integration base
       ├─ feature/realtime-notifications  → (planned) Real-time alerts
       ├─ feature/typescript-migration    → (planned) Type safety upgrade
       └─ feature/pwa-support            → (future)  Offline PWA mode
```
- All new features branch off from `develop`
- Tested, stable features merge back into `develop`
- When a release milestone is reached, `develop` merges into `main` for production deployment
---
## 🤝 Contributing
Contributions are always welcome! Please follow these steps:
1. **Fork** the repository
2. Create a feature branch: `git checkout -b feature/your-feature-name`
3. Commit your changes: `git commit -m 'feat: add some amazing feature'`
4. Push to your branch: `git push origin feature/your-feature-name`
5. Open a **Pull Request** targeting the `develop` branch
---
## 👨‍💻 Team
**University of Engineering & Technology (UET)**
*Semester 3 — Software Engineering Project*
| Role | Name |
| :--- | :--- |
| **Lead Developer** | Asim |
| **Project** | Virtual Clinix — Telemedicine Platform |
| **Course** | Software Engineering |
---
<div align="center">
**Made with ❤️ at UET Pakistan**
*Virtual Clinix — Bringing Quality Healthcare to Every Home*
</div>
