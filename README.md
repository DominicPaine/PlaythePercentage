# PlaythePercentage
# Play the Percentage Golf - Advanced Strokes Gained Analyzer

![P%P Logo](assets/logo.png)

A data-driven web application for golfers to track their performance using the powerful Strokes Gained methodology. This tool allows for detailed, shot-by-shot data entry and provides insightful visualizations to help golfers identify strengths, weaknesses, and a clear path to improvement.

**Live Demo:** [https://<your-username>.github.io/play-the-percentage-golf/](https://<your-username>.github.io/play-the-percentage-golf/)

---

## Key Features

* **Shot-by-Shot Data Entry:** A streamlined UI for capturing the details of every shot in a round (lie, distance, club, penalties).
* **Strokes Gained (SG) Analytics:** Automatically calculates SG for every shot and aggregates it across four core categories: Off-the-Tee (OTT), Approach (APP), Around the Green (ARG), and Putting.
* **"Tiger 5" Mistake Tracking:** Automatically identifies and tracks the five most costly mistakes in a round to help golfers focus on eliminating errors.
* **Interactive Dashboard:** Visualizes performance trends, SG category breakdowns, and mistake frequencies using Chart.js.
* **Persistent User Data:** Leverages Firebase (Firestore & Authentication) to securely store and retrieve all user data.
* **Intelligent Course Memory:** Saves course layouts (par and yardage) after the first entry to auto-fill hole data on subsequent rounds, dramatically improving data entry speed.
* **Durable Entry Sessions:** Automatically saves in-progress rounds to `localStorage`, allowing users to resume data entry later, even after closing the browser.

---

## Core Concepts & Skills Demonstrated

This project showcases a range of skills in frontend development, data modeling, and user experience design.

### 1. Data Analytics & Modeling

The core of this application is a sophisticated **Strokes Gained model** benchmarked against a scratch golfer.

* **Researched Data Model:** The `expectedStrokesData` object was built based on deep research of publicly available data from sources like Mark Broadie's "Every Shot Counts", Shot Scope, and scratch golfer benchmarks. It includes granular distance buckets and multiple lie types (Fairway, Rough, Bunkers, Recovery) for high precision.
* **Statistical Interpolation:** The `getExpectedStrokes` function uses linear interpolation to calculate the expected strokes for any distance, not just the fixed points in the data table. This creates a smooth and more accurate model than one relying on simple buckets.
* **Actionable Insights:** The app doesn't just present raw data; it calculates and visualizes high-impact metrics like SG and the "Tiger 5," turning data into a clear strategy for improvement.

### 2. Frontend Development & UI/UX

* **Modern JavaScript (ES6+):** The entire application is built with modern, modular JavaScript, using features like `async/await` for asynchronous operations.
* **DOM Manipulation:** The UI is dynamically rendered and manipulated in response to user actions and data from Firebase, creating a fluid single-page application experience.
* **Responsive Design:** Styled with **Tailwind CSS** (via CDN for this portfolio version) to ensure full usability and a polished look across all devices, from mobile phones to desktops.
* **Data Visualization:** Implemented interactive charts using **Chart.js** to make complex data easy to understand at a glance.
* **User-Centric Features:** Implemented crucial UX features like **session saving** (via `localStorage`) and **course memory** to respect the user's time and effort.

### 3. Backend-as-a-Service (BaaS) Integration

* **Firebase Firestore:** Used as the backend to store all user data in a scalable, NoSQL database. This includes a structured schema with sub-collections for rounds, holes, and individual shots.
* **Firebase Authentication:** Implemented anonymous authentication to provide a seamless user experience while securely associating data with a unique user ID.
* **Data Security:** Firestore Security Rules are configured to ensure users can only read and write their own data (`allow read, write: if request.auth.uid == userId;`).

---

## Setup & Local Installation

1.  Clone the repository: `git clone https://github.com/<your-username>/play-the-percentage-golf.git`
2.  Open the `index.html` file in a modern web browser.
3.  The application uses Firebase for its backend. For local development, you would need to create your own Firebase project and replace the `firebaseConfig` object in `js/script.js` with your own project's credentials. You must also enable **Anonymous Sign-in** and create a **Firestore Database** in your Firebase project console.
