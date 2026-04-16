# M-Academy | MVP Technical Leadership Showcase 🇬🇷

**Company:** The Factory Music Group - Athens, Greece  
**Duration:** March 2026 - June 2026  
**Role:** Technical Lead & Fullstack Developer (Internship)  
**Project:** M-Academy (Proprietary Music Business LMS)

---

## 👋 Introduction
This repository serves as a professional documentation of my role as **Technical Lead** during the MVP phase of **M-Academy**, a high-end educational ecosystem designed for the music industry. 

My work focused on architecting a scalable bridge between complex backend logic (**Firebase/NoSQL**) and high-performance frontend interfaces (**React/TypeScript**), ensuring a robust foundation for the company's market launch.

> **Confidentiality Note:** To comply with NDA policies, the full project name has been abbreviated and no proprietary source code is shared. This showcase focuses on architectural decisions, system design, and high-level problem-solving.

---

## 🚀 Key Achievements & Technical Solutions

### 1. Dynamic Certification Engine (Canvas API)
* **The Problem:** The need for official, downloadable credentials without the cost and latency of server-side PDF generation.
* **The Solution:** Developed a client-side rendering engine using the **HTML5 Canvas API**. It dynamically merges student identity and date metadata with high-resolution templates.
* **Result:** Instant, high-fidelity certificate generation and download (JPG/PNG) with zero server overhead.

### 2. Hardened Admin Studio & Data Analytics
* **The Problem:** Lack of visibility into student progress combined with a dashboard that crashed due to unsanitized or incomplete user records ("null" values in sorting).
* **The Solution:** * Refactored the data-fetching layer with **strict sanitization**.
    * Implemented real-time synchronization using **Firebase Listeners**, allowing staff to monitor student progress and subscription tiers live.
* **Impact:** A crash-proof administrative tool capable of managing thousands of unique student profiles.

### 3. Social Engine & Modular Community Hub
* **The Problem:** A monolithic community structure that hindered feature scalability and student engagement.
* **The Solution:** * Decoupled the architecture into a **feature-based system**, separating UI components from business logic.
    * Implemented **Optimistic UI** patterns to ensure social interactions (likes, posts) feel instantaneous.

### 4. Atomic Cloud Storage Lifecycle
* **The Problem:** Deleting database records left "orphaned" media assets in the cloud bucket, leading to unnecessary storage costs.
* **The Solution:** Engineered an **asynchronous deletion pipeline** that ensures a "Storage-First" purge; metadata is only destroyed after the physical binary is removed.

---

## 🏗️ Technical Milestones

| Milestone | Key Technologies | Documentation |
| :--- | :--- | :--- |
| **Resilient Analytics Engine** | Angular 19, Tailwind v4, Feature Flags | [View Deep Dive Case Study](https://github.com/dalva-code/angular-tailwind-ui-architecture) |
| **Cloud Storage Atomic Cleanup** | Firebase Storage, Firestore, Async/Await | [View Case Study](./milestones/cloud-storage-atomic-cleanup) |
| **Real-Time Social Engine** | React, Firebase, Data Normalization | [View Case Study](./milestones/real-time-social-engine) |
| **Admin Data Architecture** | NoSQL Schema Design, TypeScript | [View Case Study](./milestones/admin-data-architecture) |
| **UI/UX Cinematic Refactor** | CSS Specificity, WebKit Masking | [View Case Study](./milestones/community-hub-architecture) |
| **Onboarding Quiz & Sync** | CSS Wildcards, Flexbox, UI Sync | [View Case Study](./milestones/onboarding-quiz-neon-refactor) |
| **Credentials Engine** | HTML5 Canvas, Media Buffers | [View Case Study](./milestones/quiz-ui-refactor) |

---

## 🛠️ Problem Solving (Case Study)
During the final MVP stages, I identified a critical failure where sorting users would freeze the browser due to `null` value comparisons. I implemented a **Nullish Coalescing Sort Algorithm** that ensures data stability even with incomplete profiles, improving app reliability for the administrative staff.

---

## 📩 Contact

**David Esteban Correa Alvarado** *Technical Lead & Fullstack Developer* [LinkedIn](https://www.linkedin.com/in/david-esteban-correa-alvarado) | [GitHub Profile](https://github.com/dalva-code)
