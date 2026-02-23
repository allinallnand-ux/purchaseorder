# 📋 Purchase Manager
### Purchase Order Management System for Rupkali Construction Pvt. Ltd.

A full-stack web app (deployable to Vercel) with Supabase backend for creating, managing, and exporting Purchase Orders as PDFs. Works on web, and can be installed on Android/iOS as a Progressive Web App (PWA).

---

## ✅ Features
- Create Purchase Orders matching your exact format
- Auto-calculates amounts + 13% VAT
- Export professional PDFs with jsPDF
- Save/auto-fill: Customers, Suppliers, Vehicles
- Upload signature image + company stamp
- Full order history with search & filter
- Email/password login (multi-user)
- All data synced to Supabase (accessible from any device)

---

## 🚀 Deployment Guide (Step by Step)

### Step 1: Create a Supabase Project (FREE)

1. Go to **https://supabase.com** → Sign Up (free)
2. Click **"New project"**
   - Name: `rupkali-po`
   - Database password: (save this somewhere safe)
   - Region: **Southeast Asia (Singapore)** — closest to Nepal
3. Wait ~2 minutes for project to spin up
4. Go to **SQL Editor** (left sidebar)
5. Copy the entire contents of `supabase/schema.sql` and paste → click **Run**
6. Go to **Storage** → Click **New Bucket**
   - Name: `signatures`
   - Toggle **Public bucket** ON
   - Click Create

### Step 2: Get Your Supabase Keys

1. In Supabase, go to **Settings → API**
2. Copy:
   - **Project URL** (looks like `https://abcdef.supabase.co`)
   - **anon/public key** (long string starting with `eyJ...`)

### Step 3: Deploy to Vercel (FREE)

**Option A: GitHub (Recommended)**
1. Create a free account at **https://github.com**
2. Create a new repository called `rupkali-po`
3. Upload all these project files to the repository
4. Go to **https://vercel.com** → Sign up with GitHub
5. Click **"Add New Project"** → Import your GitHub repo
6. In **Environment Variables**, add:
   ```
   NEXT_PUBLIC_SUPABASE_URL = https://your-project-id.supabase.co
   NEXT_PUBLIC_SUPABASE_ANON_KEY = your-anon-key-here
   ```
7. Click **Deploy** — done! Your app will be live at `your-project.vercel.app`

**Option B: Vercel CLI (Advanced)**
```bash
npm install -g vercel
cd rupkali-po
vercel
# Follow prompts, then set env variables in Vercel dashboard
```

### Step 4: Configure Email Auth in Supabase

1. Supabase → **Authentication → Settings**
2. Set **Site URL** to your Vercel URL (e.g. `https://rupkali-po.vercel.app`)
3. Add to **Redirect URLs**: `https://rupkali-po.vercel.app/**`
4. Under **Email**, you can disable email confirmation for easier testing:
   - Authentication → Settings → Disable "Enable email confirmations"

### Step 5: Create Your Admin Account

1. Visit your live Vercel URL
2. Click **"Create new account"**
3. Sign up with your email + password
4. Start creating Purchase Orders!

---

## 📱 Install on Android / iOS (PWA)

No app store needed! Install directly from the browser:

**Android (Chrome):**
1. Open your Vercel URL in Chrome
2. Tap the **⋮ menu** → "Add to Home screen"
3. Tap "Add" → App appears on home screen

**iPhone (Safari):**
1. Open your Vercel URL in Safari
2. Tap the **Share button** (box with arrow)
3. Scroll down → "Add to Home Screen"
4. Tap "Add" → App appears on home screen

The app will open full-screen like a native app and all data syncs in real-time.

---

## 🔧 Local Development

```bash
# Install dependencies
npm install

# Copy environment file
cp .env.example .env.local
# Edit .env.local with your Supabase keys

# Run development server
npm run dev
# Open http://localhost:3000
```

---

## 📁 Project Structure

```
rupkali-po/
├── pages/
│   ├── index.js          # New PO creation form
│   ├── history.js        # PO history & search
│   ├── customers.js      # Customer management
│   ├── suppliers.js      # Supplier management
│   ├── vehicles.js       # Vehicle management
│   └── auth.js           # Login / Signup
├── components/
│   ├── Layout.js         # Navigation wrapper
│   └── EntityManager.js  # Reusable CRUD component
├── lib/
│   ├── supabase.js       # Supabase client
│   └── generatePDF.js    # jsPDF generator
├── styles/
│   └── globals.css       # Tailwind + custom styles
├── supabase/
│   └── schema.sql        # Database schema (run once)
├── .env.example          # Environment variables template
├── package.json
└── vercel.json
```

---

## 🛟 Troubleshooting

**"Cannot read properties of undefined"**
→ Check your `.env.local` has both Supabase variables set correctly

**PDF not downloading**
→ Make sure `jspdf` and `jspdf-autotable` are installed: `npm install`

**Images not uploading**
→ Verify the `signatures` Storage bucket exists in Supabase and is set to Public

**"Row Level Security" errors**
→ Re-run the `schema.sql` file in Supabase SQL Editor

---

## 💰 Cost

| Service | Free Tier | Paid |
|---------|-----------|------|
| Vercel | ✅ Free forever for hobby | $20/mo Pro |
| Supabase | ✅ 500MB DB, free forever | $25/mo Pro |
| Domain (optional) | — | ~$10/year |

**Total cost: $0/month** on free tiers for a small business.

---

Built for Rupkali Construction Pvt. Ltd. | VAT: 606903745
