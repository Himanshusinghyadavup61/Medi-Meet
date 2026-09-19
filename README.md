# 🩺 Medi-Meet — Next-Gen Telemedicine & Doctor Consultation Platform

Medi-Meet is a modern, full-stack healthcare web application that connects patients with verified medical specialists. It features instant appointment booking, secure in-browser HD video consultations, an AI-powered medical assistant, and a credit-based subscription billing system.

---

## 🚀 Key Features

### 👨‍⚕️ For Doctors
- **Doctor Onboarding & Verification:** Submit professional credentials, experience, specialty, and bio for admin verification.
- **Availability Slot Management:** Set and toggle weekly consultation slots and working hours.
- **Appointment Management:** Review upcoming patient appointments, medical descriptions, and consultation notes.
- **Payout Management:** Track earned credits and request PayPal payouts with platform fee deductions.

### 🧑‍💼 For Patients
- **Specialty Directory:** Search and browse verified doctors across 15+ specialties (Cardiology, Dermatology, Pediatrics, etc.).
- **Seamless Booking:** Reserve doctor slots using consultation credits with instant confirmation.
- **Live Video Consultations:** One-click connect to secure, end-to-end encrypted video calls powered by the Vonage Video API.
- **Credit & Billing System:** Flexible packages (Starter, Standard, Premium) with automatic monthly credit replenishment.

### 🤖 AI Medical Assistant (MediMeet AI)
- **24/7 Smart Triage:** An interactive floating AI chat widget that evaluates symptoms and suggests the exact relevant specialist to consult on the platform.
- **Powered by Groq:** Ultra-fast, low-latency LLM inference.

### 🛡️ Admin & Security
- **Role-Based Access Control:** Secure routes for `PATIENT`, `DOCTOR`, and `ADMIN` powered by Clerk middleware.
- **Doctor Credential Verification:** Admins review and approve/reject doctor applications.

---

## 🛠️ Tech Stack

- **Framework:** [Next.js 15](https://nextjs.org/) (App Router, Server Actions, Turbopack)
- **Frontend & UI:** [React 19](https://react.dev/), [Tailwind CSS](https://tailwindcss.com/), [Radix UI](https://www.radix-ui.com/), [Lucide Icons](https://lucide.dev/), [Sonner](https://sonner.emilkowal.ski/)
- **Authentication & Billing:** [Clerk Auth](https://clerk.com/) & Clerk Billing
- **Database & ORM:** [PostgreSQL (Neon Serverless)](https://neon.tech/) with [Prisma ORM](https://www.prisma.io/)
- **Video Conferencing:** [Vonage Video API (OpenTok)](https://www.vonage.com/communications-apis/video/)
- **AI / LLM:** [Groq Cloud API](https://groq.com/)
- **Deployment:** Vercel

---

## 📦 Getting Started

### 1. Prerequisites
- **Node.js** v18+ (v20+ recommended)
- **npm** or **pnpm** / **yarn**
- Accounts with:
  - [Neon](https://neon.tech/) (PostgreSQL Database)
  - [Clerk](https://clerk.com/) (User Authentication)
  - [Vonage](https://www.vonage.com/) (Video API)
  - [Groq](https://groq.com/) (AI Chat API)

---

### 2. Clone the Repository
```bash
git clone https://github.com/YOUR_USERNAME/Medi-Meet.git
cd Medi-Meet
```

---

### 3. Install Dependencies
```bash
npm install
```

---

### 4. Configure Environment Variables
Create a `.env` file in the root directory and copy the values from `.env.example`:

```env
# Database (Neon / PostgreSQL)
DATABASE_URL="postgresql://user:password@ep-sample-pooler.region.aws.neon.tech/medimeet?sslmode=require"

# Clerk Authentication
NEXT_PUBLIC_CLERK_PUBLISHABLE_KEY=pk_test_...
CLERK_SECRET_KEY=sk_test_...
NEXT_PUBLIC_CLERK_SIGN_IN_URL=/sign-in
NEXT_PUBLIC_CLERK_SIGN_UP_URL=/sign-up
NEXT_PUBLIC_CLERK_AFTER_SIGN_IN_URL=/onboarding
NEXT_PUBLIC_CLERK_AFTER_SIGN_UP_URL=/onboarding

# Vonage Video API
VONAGE_APPLICATION_ID=your_vonage_application_id
NEXT_PUBLIC_VONAGE_APPLICATION_ID=your_vonage_application_id

# AI Medical Assistant
GROQ_API_KEY=gsk_...
GROQ_MODEL=qwen/qwen3.8-27b
```

> **Note:** Place your Vonage private key at `src/lib/private.key` (ignored by git).

---

### 5. Setup Database & Prisma
Push your Prisma schema to your database:

```bash
npx prisma generate
npx prisma db push
```

---

### 6. Run the Development Server
```bash
npm run dev
# Windows PowerShell alternative:
# npm.cmd run dev
```

Open [http://localhost:3000](http://localhost:3000) in your browser.

---

## 📂 Project Structure

```
Medi-Meet/
├── prisma/
│   ├── schema.prisma       # Database schema & models
│   └── migrations/         # SQL database migrations
├── public/                 # Static assets & icons
├── src/
│   ├── actions/            # Next.js Server Actions
│   │   ├── admin.js        # Doctor verification & platform management
│   │   ├── ai-chat.js      # Groq AI assistant integration
│   │   ├── appointments.js # Slot booking & Vonage session creation
│   │   ├── credits.js      # Plan credit allocations & deduction
│   │   ├── doctor.js       # Doctor profile & availability handlers
│   │   └── payout.js       # Payout calculations & processing
│   ├── app/                # Next.js App Router pages & layouts
│   │   ├── (auth)/         # Clerk Sign-in & Sign-up routes
│   │   ├── (main)/         # Protected main application routes
│   │   ├── globals.css     # Global styles & theme tokens
│   │   └── page.js         # Landing page
│   ├── components/         # Reusable React components & UI primitives
│   ├── hooks/              # Custom React hooks
│   ├── lib/                # Database clients, utilities & helpers
│   └── middleware.js       # Clerk route protection & auth redirection
├── .env.example            # Environment variables template
├── package.json
└── README.md
```

---

## 📜 Available Scripts

| Command | Description |
| :--- | :--- |
| `npm run dev` | Starts the Next.js development server with Turbopack |
| `npm run build` | Builds the optimized production application |
| `npm run start` | Runs the production build server |
| `npm run lint` | Runs ESLint checks across the codebase |
| `npx prisma studio` | Opens the visual database management GUI |
| `npx prisma db push` | Synchronizes the Prisma schema with your database |

---

## 👨‍💻 Author

**Himanshu Singh Yadav**
- GitHub: [@Himanshusinghyadavup61](https://github.com/Himanshusinghyadavup61)

---

## 📄 License

This project is open source and available under the [MIT License](LICENSE).

