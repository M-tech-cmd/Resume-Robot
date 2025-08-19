# GuestGlow 🏨✨

[![License: MIT](https://img.shields.io/badge/license-MIT-yellow.svg)](LICENSE) [![Stack: MERN](https://img.shields.io/badge/stack-MERN-blue.svg)](#) [![Auth: Clerk](https://img.shields.io/badge/Auth-Clerk-orange.svg)](https://clerk.com) [![Images: Cloudinary](https://img.shields.io/badge/Images-Cloudinary-lightgrey.svg)](https://cloudinary.com) [![Emails: Nodemailer+Brevo](https://img.shields.io/badge/Emails-Nodemailer+Brevo-red.svg)](#)

A modern **MERN** full-stack hotel booking app built with **React**, **Express**, **MongoDB**, and **Node.js**, using **Clerk** for authentication, **Cloudinary** for image hosting, **Nodemailer + Brevo (Sendinblue)** for email notifications, and **Stripe** for payments.

---

## 📋 Features

* 🔑 **User Authentication** – Sign up / login via **Clerk** (social login supported)
* 🏨 **Hotel Management** – Create, update, delete hotels with images
* 🔍 **Search & Filter** – By location, price, rating
* 📅 **Booking System** – Real-time availability
* 📧 **Email Notifications** – Booking confirmations, receipts & updates via **Nodemailer + Brevo**
* 💳 **Payments** – Secure online payments with **Stripe**
* 📱 **Responsive UI** – Mobile-friendly design
* 🔒 **Secure REST API** – Protected routes with Clerk middleware

---

## 🛠 Tech Stack

**Frontend:** ReactJS, React Router, Axios, TailwindCSS

**Backend:** Node.js, Express.js, MongoDB + Mongoose

**Integrations:** Clerk (Auth), Cloudinary (Images), Nodemailer + Brevo (Emails), Stripe (Payments)

---

## 📂 Folder Structure

```
guestglow/
├─ client/   # React frontend
├─ server/   # Express backend
└─ README.md
```

---

## 🚀 Getting Started

### Prerequisites

* Node.js (>= 16)
* MongoDB Atlas/local
* Clerk account
* Cloudinary account
* Brevo account (for emails)
* Stripe account (for payments)

### Installation

```bash
git clone https://github.com/yourusername/guestglow.git
cd guestglow

# Install backend
cd server && npm install

# Install frontend
cd ../client && npm install
```

### Environment Variables

**server/.env**

```
PORT=5000
MONGO_URI=your_mongodb_uri
CLOUDINARY_CLOUD_NAME=your_cloud_name
CLOUDINARY_API_KEY=your_api_key
CLOUDINARY_API_SECRET=your_api_secret
CLERK_SECRET_KEY=your_clerk_secret
BREVO_API_KEY=your_brevo_api_key
EMAIL_FROM=your_email_address
STRIPE_SECRET_KEY=your_stripe_secret
STRIPE_WEBHOOK_SECRET=your_stripe_webhook_secret
```

**client/.env**

```
VITE_CLERK_PUBLISHABLE_KEY=your_publishable_key
VITE_API_BASE_URL=http://localhost:5000
VITE_STRIPE_PUBLIC_KEY=your_stripe_public_key
```

---

## ▶️ Running the App

Backend:

```bash
cd server
npm run dev
```

Frontend:

```bash
cd client
npm run dev
```

---

## 📡 API Endpoints

| Method | Endpoint         | Description       | Auth |
| ------ | ---------------- | ----------------- | ---- |
| GET    | /api/hotels      | Get all hotels    | No   |
| POST   | /api/hotels      | Create hotel      | Yes  |
| GET    | /api/hotels/\:id | Get hotel details | No   |
| POST   | /api/bookings    | Create booking    | Yes  |
| GET    | /api/bookings    | Get user bookings | Yes  |
| POST   | /api/payments    | Create payment    | Yes  |

---

## 🔐 Authentication Flow

1. User logs in via Clerk (frontend)
2. Clerk issues session token
3. Frontend sends token with API requests
4. Backend verifies token using Clerk middleware

---

## 🖼 Image Uploads with Cloudinary

```js
const data = new FormData();
data.append('file', file);
data.append('upload_preset', 'unsigned_preset');

const res = await fetch(`https://api.cloudinary.com/v1_1/${cloudName}/image/upload`, {
  method: 'POST',
  body: data
});

const fileData = await res.json();
console.log(fileData.secure_url);
```

---

## 📧 Email Notifications (Nodemailer + Brevo)

GuestGlow integrates **Nodemailer** with **Brevo (Sendinblue)** SMTP API to send:

* Booking confirmations
* Payment receipts
* Account updates

Required environment variables:

```
BREVO_API_KEY=your_brevo_api_key
EMAIL_FROM=your_email_address
```

---

## 💳 Payments with Stripe

GuestGlow integrates **Stripe** for secure payment processing.

Required environment variables:

```
STRIPE_SECRET_KEY=your_stripe_secret
STRIPE_WEBHOOK_SECRET=your_stripe_webhook_secret
VITE_STRIPE_PUBLIC_KEY=your_stripe_public_key
```

Flow:

1. Frontend collects payment info using **Stripe Elements**
2. Payment intent is created via backend
3. Stripe processes payment securely
4. Confirmation email is sent to the user

---

## 📌 Future Enhancements

* 🛎 Advanced filters (amenities, room type)
* 📊 Admin dashboard
* 🌍 Multi-language support

---

## 📄 License

MIT License © M-Tech-Cmd

Copyright (c) 2025 M-Tech-Cmd
All Rights Reserved.

This repository and its contents are provided for viewing purposes only.
You are NOT permitted to copy, modify, fork, distribute, or use this code,
in whole or in part, for any purpose without explicit written permission
from the author.

Unauthorized use may result in legal action.
