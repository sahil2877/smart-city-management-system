<div align="center">

<img src="https://capsule-render.vercel.app/api?type=waving&color=0:0f2027,50:203a43,100:2c5364&height=200&section=header&text=SmartCity%20—%20Civic%20Portal&fontSize=42&fontColor=ffffff&fontAlignY=38&desc=Full-Stack%20Civic%20Management%20Platform&descAlignY=58&descSize=16" width="100%"/>

<br/>

![AngularJS](https://img.shields.io/badge/AngularJS-1.8.3-E23237?style=flat-square&logo=angularjs&logoColor=white)
![Node.js](https://img.shields.io/badge/Node.js-v18+-339933?style=flat-square&logo=nodedotjs&logoColor=white)
![Express](https://img.shields.io/badge/Express-4.x-000000?style=flat-square&logo=express&logoColor=white)
![MongoDB](https://img.shields.io/badge/MongoDB-v6+-47A248?style=flat-square&logo=mongodb&logoColor=white)
![JWT](https://img.shields.io/badge/Auth-JWT-000000?style=flat-square&logo=jsonwebtokens&logoColor=white)
![Bootstrap](https://img.shields.io/badge/Bootstrap-5.3-7952B3?style=flat-square&logo=bootstrap&logoColor=white)

<br/>

> **A complete Smart City civic management platform with role-based access control for citizens and administrators.**

<br/>

</div>

---

## 📁 Project Structure
```
smartcity/
├── backend/                        # Node.js + Express API Server
│   ├── config/
│   │   ├── imagekit.js             # ImageKit cloud storage setup
│   │   └── multer.js               # Multer file upload config
│   ├── middleware/
│   │   └── auth.js                 # JWT auth + admin guard middleware
│   ├── models/                     # MongoDB Mongoose schemas
│   │   ├── User.js
│   │   ├── Complaint.js
│   │   ├── Announcement.js
│   │   ├── Feedback.js
│   │   ├── Parking.js
│   │   ├── ServiceRequest.js
│   │   └── Report.js
│   ├── routes/                     # Express REST API routes
│   │   ├── userRoutes.js           # /api/users
│   │   ├── complaintRoutes.js      # /api/complaints
│   │   ├── announcementRoutes.js   # /api/announcements
│   │   ├── feedbackRoutes.js       # /api/feedback
│   │   ├── parkingRoutes.js        # /api/parking
│   │   ├── serviceRoutes.js        # /api/services
│   │   └── reportRoutes.js         # /api/reports
│   ├── server.js                   # Express app entry point
│   ├── package.json
│   └── .env.example                # Environment variable template
│
└── frontend/                       # AngularJS SPA
    ├── index.html                  # Main SPA shell + navbar
    ├── css/
    │   └── style.css               # Full custom dark theme
    ├── js/
    │   ├── app.js                  # AngularJS module + routes
    │   ├── services/
    │   │   ├── authService.js      # JWT session management
    │   │   └── apiService.js       # All HTTP API calls
    │   └── controllers/
    │       ├── NavController.js
    │       ├── AuthController.js
    │       ├── DashboardController.js
    │       ├── ComplaintController.js
    │       ├── AdminController.js
    │       ├── ParkingController.js
    │       └── MiscController.js
    └── views/                      # AngularJS HTML templates
        ├── home.html               ├── dashboard.html
        ├── login.html              ├── parking.html
        ├── register.html           ├── emergency.html
        ├── add-complaint.html      ├── admin-dashboard.html
        ├── add-report.html         ├── admin-complaints.html
        ├── add-service.html        ├── admin-announcements.html
        ├── add-feedback.html       ├── admin-parking.html
        ├── admin-feedback.html     ├── admin-reports.html
        ├── admin-services.html     └── admin-users.html
```

---

## ⚙️ Prerequisites

Make sure these are installed on your machine before getting started:

| Tool | Version | Download |
|------|---------|----------|
| ![Node.js](https://img.shields.io/badge/-Node.js-339933?style=flat-square&logo=nodedotjs&logoColor=white) | v18+ | [nodejs.org](https://nodejs.org) |
| ![MongoDB](https://img.shields.io/badge/-MongoDB-47A248?style=flat-square&logo=mongodb&logoColor=white) | v6+ | [mongodb.com](https://mongodb.com/try/download/community) |
| ![npm](https://img.shields.io/badge/-npm-CB3837?style=flat-square&logo=npm&logoColor=white) | v8+ | Comes with Node.js |

---

## 🚀 Step-by-Step Setup

### Step 1 — Clone / Extract the Project
```bash
# If using the ZIP file:
unzip smartcity.zip
cd smartcity
```

### Step 2 — Set Up the Backend
```bash
cd backend
npm install
```

### Step 3 — Configure Environment Variables
```bash
# Copy the example env file
cp .env.example .env
```

Open `.env` and fill in your values:
```env
# MongoDB (use localhost for local MongoDB)
MONGO_URI=mongodb://localhost:27017/smartcity

# JWT Secret — change this to any long random string
JWT_SECRET=my_super_secret_key_change_this_123

# Server port
PORT=5000

# ImageKit (get free credentials at https://imagekit.io)
IMAGEKIT_PUBLIC_KEY=public_xxxxxxxxxxxxxxx
IMAGEKIT_PRIVATE_KEY=private_xxxxxxxxxxxxxxx
IMAGEKIT_URL_ENDPOINT=https://ik.imagekit.io/your_id_here
```

> **💡 Note on ImageKit:** Create a free account at [imagekit.io](https://imagekit.io). Go to **Dashboard → Developer Options** to find your keys. If you skip ImageKit, complaints/reports will still work — images just won't be stored.

### Step 4 — Start MongoDB
```bash
# macOS / Linux:
mongod

# Windows (run as Administrator):
net start MongoDB

# Or open MongoDB Compass — it starts the server automatically.
```

### Step 5 — Start the Backend Server
```bash
# In the /backend directory:
node server.js

# Or with auto-restart on file changes:
npx nodemon server.js
```

You should see:
```
✅  MongoDB connected successfully
🚀  Server running on http://localhost:5000
```

### Step 6 — Serve the Frontend

> ⚠️ Opening `index.html` directly via `file://` **won't work** due to CORS/routing. Use one of the options below.

<table>
<tr>
<th>Option</th>
<th>Method</th>
<th>URL</th>
</tr>
<tr>
<td>⭐ <strong>VS Code Live Server</strong> (Recommended)</td>
<td>Install "Live Server" extension → right-click <code>frontend/index.html</code> → Open with Live Server</td>
<td><code>http://127.0.0.1:5500</code></td>
</tr>
<tr>
<td><strong>npx serve</strong></td>
<td><code>cd frontend && npx serve .</code></td>
<td><code>http://localhost:3000</code></td>
</tr>
<tr>
<td><strong>Python</strong></td>
<td><code>cd frontend && python -m http.server 8080</code></td>
<td><code>http://localhost:8080</code></td>
</tr>
</table>

---

## 🌐 Accessing the Application

| URL | Description |
|-----|-------------|
| `http://localhost:5500` *(or your port)* | Frontend SPA |
| `http://localhost:5000` | Backend API |
| `http://localhost:5000/api/users` | Users API endpoint |

---

## 👤 First-Time Setup — Create an Admin Account

1. Open the frontend in your browser
2. Click **Register**
3. Fill in your details and set **Role: Administrator**
4. Click **Create Account**
5. You'll be redirected to the **Admin Dashboard**

> For a citizen account, register with **Role: Citizen (User)**

---

## 🔑 Role-Based Features

<table>
<tr>
<td width="50%" valign="top">

### 👤 Citizen Features

| Feature | Route |
|---------|-------|
| Dashboard with stats | `/dashboard` |
| File a Complaint (with image) | `/add-complaint` |
| Report Cleanliness Issue (with image) | `/add-report` |
| Request Utility Service | `/add-service` |
| Submit Feedback & Rating | `/add-feedback` |
| View Smart Parking | `/parking` |
| Emergency Contacts | `/emergency` |
| View City Announcements | Dashboard |
| View Air Quality Index (AQI) | Dashboard |

</td>
<td width="50%" valign="top">

### 🛡️ Admin Features

| Feature | Route |
|---------|-------|
| Admin Overview Dashboard | `/admin` |
| Manage All Complaints | `/admin/complaints` |
| Post/Delete Announcements | `/admin/announcements` |
| Manage Parking Locations | `/admin/parking` |
| View Citizen Feedback | `/admin/feedback` |
| Manage Cleanliness Reports | `/admin/reports` |
| Manage Service Requests | `/admin/services` |
| View All Users | `/admin/users` |

</td>
</tr>
</table>

---

## 📡 REST API Reference

<details>
<summary><b>👤 Users — /api/users</b></summary>
<br/>

| Method | Endpoint | Auth | Description |
|--------|----------|------|-------------|
| `POST` | `/api/users/register` | None | Register new user |
| `POST` | `/api/users/login` | None | Login |
| `GET` | `/api/users/profile` | User | Get own profile |
| `GET` | `/api/users/all` | Admin | Get all users |
| `DELETE` | `/api/users/:id` | Admin | Delete user |

</details>

<details>
<summary><b>📋 Complaints — /api/complaints</b></summary>
<br/>

| Method | Endpoint | Auth | Description |
|--------|----------|------|-------------|
| `POST` | `/api/complaints` | User | Submit complaint |
| `GET` | `/api/complaints/my` | User | Own complaints |
| `GET` | `/api/complaints` | Admin | All complaints |
| `GET` | `/api/complaints/stats` | Admin | Analytics |
| `PUT` | `/api/complaints/:id` | Admin | Update status |
| `DELETE` | `/api/complaints/:id` | Admin | Delete |

</details>

<details>
<summary><b>📢 Announcements — /api/announcements</b></summary>
<br/>

| Method | Endpoint | Auth | Description |
|--------|----------|------|-------------|
| `GET` | `/api/announcements` | User | All announcements |
| `POST` | `/api/announcements` | Admin | Post announcement |
| `DELETE` | `/api/announcements/:id` | Admin | Delete |

</details>

<details>
<summary><b>🔧 Other Endpoints</b></summary>
<br/>

All follow the same REST pattern:

| Endpoint | Description |
|----------|-------------|
| `/api/feedback` | Feedback CRUD |
| `/api/parking` | Parking management |
| `/api/services` | Utility service requests |
| `/api/reports` | Cleanliness reports |

</details>

---

## 🗄️ MongoDB Schema Overview
```
users           → name, email, password (hashed), phone, role
complaints      → user, title, description, category, imageUrl, status
announcements   → title, content, priority, postedBy
feedback        → user, subject, message, rating, isRead
parking         → name, address, totalSlots, availableSlots, status, fee
serviceRequests → user, serviceType, description, address, status
reports         → user, category, location, description, imageUrl, status
```

---

## 🔧 Troubleshooting

<details>
<summary><b>❌ MongoDB not connecting?</b></summary>

- Make sure `mongod` is running in a separate terminal
- Check that port `27017` is not blocked by a firewall
</details>

<details>
<summary><b>❌ CORS errors in browser?</b></summary>

- Make sure the backend is running on port `5000`
- The frontend **must** be served via HTTP server, not opened as a local file
</details>

<details>
<summary><b>❌ Image upload not working?</b></summary>

- Add valid ImageKit credentials to your `.env` file
- Complaints still work without images — `imageUrl` will just be empty
</details>

<details>
<summary><b>❌ Port already in use?</b></summary>

- Change `PORT=5001` in your `.env` file
- Update `var BASE = 'http://localhost:5001/api'` in `frontend/js/services/apiService.js`
</details>

---

## 🎨 Tech Stack

| Layer | Technology |
|-------|-----------|
| **Frontend Framework** | AngularJS 1.8.3 |
| **Frontend Routing** | ngRoute |
| **UI Library** | Bootstrap 5.3 |
| **Icons** | Bootstrap Icons 1.11 |
| **Fonts** | Sora + JetBrains Mono (Google Fonts) |
| **Backend** | Node.js + Express 4 |
| **Database** | MongoDB + Mongoose |
| **Authentication** | JWT (jsonwebtoken) |
| **Password Hashing** | bcryptjs |
| **File Upload** | Multer (memory storage) |
| **Image Hosting** | ImageKit |
| **Environment** | dotenv |

---

<div align="center">
  <img src="https://capsule-render.vercel.app/api?type=waving&color=0:2c5364,50:203a43,100:0f2027&height=100&section=footer" width="100%"/>
</div>
