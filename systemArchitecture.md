
# 🏗️ System Architecture – MODASFIT

MODASFIT is a digital platform designed to support first-time mums and nursing mothers by providing expert-backed fitness guidance, nutritional education, and access to a safe community — all connected to a healthy-meal ordering service.

This document explains how the system works technically, describing the frontend, backend, database, communication flow, scalability, and technical feasibility.

## 📌 1. Overview of the Architecture        

> MODASFIT uses a client–server architecture:

- Frontend (React.js) – interacts with users and displays content

- Backend (Node.js + Express) – processes logic, authentication, and handles community features

- Database (MongoDB) – stores user profiles, content, community interactions

- External Services – video hosting (e.g., Cloudinary), Craveon referral link, email notifications

- Everything communicates over secure HTTPS REST APIs.

  

## 🖼️ 2. System Diagram Placeholder

<img width="500" height="441" alt="Screenshot 2025-11-08 004125" src="https://github.com/user-attachments/assets/3214b51e-eebb-4995-8cdc-70c0ae90eb51" />

## 🎨 3. Frontend Architecture (React.js)
> ✅ Key Responsibilities

- Displays user interface for onboarding, learning modules, and community

- Handles authentication (token-based)

- Fetches data via REST APIs

- Renders video & text content

- Provides anonymous community UI

> ✅ Tech Stack

- React.js

- React Router for navigation

- Axios for API calls

- Context API / Redux (optional) for global state

- TailwindCSS or Material UI for styling

> ✅ Why This Stack Works

- Fast, reusable components

- Easy integration with REST APIs

- Good for scaling into a mobile app later using React Native

## 🧠 4. Backend Architecture (Node.js + Express)
> ✅ Key Responsibilities

- User authentication (JWT)

- Manages fitness & nutrition content (videos, articles)

- Controls anonymous community system (posts, comments)

- Handles admin roles for nutritionists & fitness experts

- Stores referral actions to Craveon

- Connects to cloud storage for video uploads

> ✅ Tech Stack

- Node.js + Express

- JWT for secure auth

- Mongoose to interact with MongoDB

- Cloudinary SDK for video content

> ✅ Why This Stack Works

- Fast and scalable for many concurrent users

- Perfect alignment with React frontend

- Lightweight and ideal for MVP → production

## 🗄️ 5. Database Architecture (MongoDB)
> ✅ Collections

- Users

- name, email, role, preferences

- Content

- videos, text guides, categories

- CommunityPosts

- anonymous posts, replies, timestamps

- Experts

- dieticians, nutritionists, fitness coaches

- Referrals(optional)

- user → Craveon orders tracking

> ✅ Why MongoDB

- Flexible schema — ideal for fast-changing MVP

- Great for storing unstructured data (videos, posts, messages)

- Highly scalable

## 🔗 6. Communication Between Components
> 🌐 Frontend → Backend

- REST API calls via HTTPS

- Token (JWT) attached to protected endpoints

- Responses returned in JSON format

> Examples:

- /api/auth/login

- /api/content/videos

- /api/community/post

### 🛠️ Backend → Database

- Queries handled using Mongoose ORM

- All inputs validated before insertion

- Backend never exposes the database directly

### ☁️ Backend → Cloud Services

- Upload video content to Cloudinary

- Returns URL stored in MongoDB

- Email notifications via external service (e.g., SendGrid)

## 🧩 7. Technical Feasibility

> This solution is fully feasible because:

✅ React + Node + MongoDB is a proven trio used in many real-world products

✅ Infrastructure can scale gradually as user traffic increases

✅ Content (videos, articles) is easily handled via cloud services

✅ Anonymous community uses simple CRUD operations — low complexity

✅ System is modular → features can be added later (e.g., chat, subscription plans)

## 🚀 8. Future Enhancements

- Mobile app version

- AI-powered personalized meal plans

- Real-time chat between mums

- Subscription tiers for premium expert access

- Offline content caching
