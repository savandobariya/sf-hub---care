<div align="center">

# 📱 SF Hub & Care

Flagship mobile-store & hardware-service-station management app — photorealistic 3D smartphone showroom, IMEI inventory tracking, POS billing (GST invoices), repair job cards, customer/supplier khata (ledger), and reports/analytics.

</div>

---

## ⚠️ Important Note

This project was generated in **Google AI Studio**. It's a **React + TypeScript + Vite** frontend that ships with a **real, working PHP backend** — but that backend uses **PHP + MongoDB**, not MySQL.

By default the frontend runs on local mock data / `localStorage` (`src/data/mockData.ts`, `src/utils/storage.ts`). To use the real backend, connect `src/services/mongoPhpBackend.ts` to your running PHP server.

---

## 🛠️ Tech Stack

| Layer | Technology |
|---|---|
| Frontend | React 19 + TypeScript + Vite 6 |
| Styling | Tailwind CSS 4 |
| 3D | three.js (photorealistic phone viewer & showroom) |
| Extras | canvas-confetti, motion (animations) |
| Dev Server | Vite (`vite --port=3000`) — no Express server here |
| Real Backend | PHP 8.1+ REST APIs in `/php_backend` |
| Database | MongoDB (local or Atlas) via `php-mongodb` + Composer |
| AI | Google Gemini API (`@google/genai`) |

---

## 📁 Folder Structure

```
sf-hub-and-care/
├── index.html
├── package.json
├── vite.config.ts
├── tsconfig.json
├── .env.example
├── php_backend/
│   ├── README.md                 # backend's own setup guide
│   ├── composer.json
│   ├── config/
│   │   └── db.php                # MongoDB connection class
│   └── api/
│       ├── products.php
│       ├── imeis.php
│       ├── sales.php
│       ├── repairs.php
│       ├── crm.php
│       └── settings.php
└── src/
    ├── main.tsx
    ├── App.tsx
    ├── index.css
    ├── types.ts
    ├── data/
    │   └── mockData.ts
    ├── utils/
    │   └── storage.ts             # localStorage fallback layer
    ├── services/
    │   └── mongoPhpBackend.ts     # fetch wrapper for PHP API
    └── components/
        ├── Navbar.tsx / SFLogo.tsx
        ├── Dashboard.tsx / ReportsAnalytics.tsx
        ├── POSBilling.tsx / InvoiceModal.tsx / BarcodeModal.tsx
        ├── InventoryManager.tsx
        ├── RepairManager.tsx / RepairJobModal.tsx
        ├── CustomerSupplierLedger.tsx
        ├── SettingsModal.tsx
        ├── BackendDatabaseManager.tsx
        └── ThreeDPhoneViewer.tsx / ThreeDShopShowroom.tsx
```

---

## 🔑 Environment Variables

**Frontend (`.env`):**
```env
GEMINI_API_KEY=your_google_gemini_api_key
APP_URL=http://localhost:3000
```

**PHP backend (set on server, not frontend `.env`):**
```env
MONGODB_URI=mongodb://localhost:27017
MONGODB_DB=sfhub_care_db
PORT=8000
```

---

## 🚀 Setup / Run Locally

**Frontend:**
```bash
npm install
npm run dev          # Vite dev server on :3000
```

**Backend (separate terminal):**
```bash
cd php_backend
composer install
php -S 0.0.0.0:8000
# APIs live at http://localhost:8000/api/products.php etc.
```
Then point `src/services/mongoPhpBackend.ts`'s base URL to `http://localhost:8000`.

---

## 🗄️ MongoDB Collections

`sfhub_products` · `sfhub_imeis` · `sfhub_sales` · `sfhub_repairs` · `sfhub_customers` · `sfhub_suppliers` · `sfhub_settings`

---

## 🔄 Switching to MySQL Instead of MongoDB

The current backend uses `MongoDB\Client` (NoSQL). To make it a classic PHP+MySQL project you'd need to rewrite `config/db.php` with PDO/MySQLi and convert each `api/*.php` file's Mongo queries to SQL — this is a full backend rewrite, not a small tweak.

---

## 🏷️ Suggested Repo Metadata

**Description:**
> Mobile store & repair-service management system — POS billing, IMEI inventory, repair job cards, customer khata, 3D showroom (React + PHP/MongoDB backend).

**Topics:**
`react` `typescript` `vite` `tailwindcss` `threejs` `php` `mongodb` `pos-system` `inventory-management` `repair-shop`

---

## Note

Also add `php_backend/vendor/` (Composer dependencies) to `.gitignore` if not already there — don't commit it.
