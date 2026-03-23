# Label M... | MVP Technical Leadership Showcase 🇬🇷

**Company:** The Factory Music Group - Athens, Greece
**Duration:** March 2026 - June 2026
**My Role:** Technical Lead & Fullstack Developer (Internship)
**Official Scope:** Backend software development, REST API integration, and Technical Leadership for MVP development.

---

## 👋 Introduction

This repository serves as a public showcase of my engineering journey and leadership role during my internship at The Factory Music Group. As the **Technical Lead for the MVP phase**, I am responsible for architecting and building **Label M...**, a cutting-edge music business education platform.

My work bridges the gap between complex backend logic (Firebase, SQL, Python) and intuitive frontend interfaces (React, Vite, Tailwind), ensuring a scalable architecture for the company's first market launch.

*(Note: To honor NDA policies, no source code is shared. This repository documents UI/UX architecture and high-level problem-solving).*

![Label MBA Header](./header.png)

---

## 🚀 Key Achievements & Feature Implementation

### 1. Unified Admin Studio & Real-Time Analytics

**The Problem:** The admin team needed a central hub to manage student approvals, track course progress, and view key platform metrics in real-time. The existing data was scattered across Firebase Console, making efficient user management impossible.

**The Solution:** I designed and implemented the **Admin Studio Dashboard** using React and TailwindCSS. It features:
* **Dynamic Analytics Cards:** Calculates "Total Instructors", "Total Courses", and "Total Students" (including a Pending/Approved status breakdown).
* **Real-Time Student Management Table:** Built with React state management to display student data instantly. Includes visual progress bars, subscription tracking, and instant action buttons (Approve/Reject).
* **Firebase Integration:** Utilized Firebase Firestore's `onSnapshot` for real-time data binding, ensuring the dashboard reflects database changes instantly without page reloads.

**UI/UX Showcase:**

![Label MBA Admin Studio Dashboard](./dashboard.png)

*Caption: The completed Admin Studio interface showing the unified student management workflow and real-time analytics.*

---

### 2. Google Auth Onboarding Bug Fix (Security & UX)

**The Problem:** While implementing the dashboard, I discovered a critical "destructive overwrite" bug. Users registering via Google had an incomplete profile (missing essential `uid`, `email`, and `joinedAt` fields in Firestore). This caused the Admin Panel's approval buttons to fail, as the code was attempting to update a "ghost" document.

**The Analysis:** I pinpointed the error in the `OnboardingModal.tsx` file. The submit handler was saving the new onboarding data (location, DOB) but wasn't capturing the required authentication metadata from the newly logged-in Google user object.

**The Fix:** I modified the `handleSubmit` function within the onboarding flow to ensure that during the first login (whether by email or Google), all base user data is successfully validated and stored in Firestore. I added implicit data merging (`{merge: true}`) to Firebase's `setDoc` calls to prevent accidental data loss in future updates.

---

## 🛠️ Upcoming Technical Challenges

As I continue my internship, I am looking forward to tackling the following:
* [ ] Integrating decentralized storage solutions (IPFS) for course assets.
* [ ] Developing blockchain-based credentialing for course completion certificates (NFTs).

---

## 📩 Contact Me

Feel free to connect with me to discuss my engineering journey in Greece:

* **GitHub (Portfolio):** [dalva-code](https://github.com/dalva-code)
