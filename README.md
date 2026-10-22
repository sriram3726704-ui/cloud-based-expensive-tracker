# 💸 SpendCloud - Cloud-Based Expense Tracker

A modern, responsive, and real-time **Cloud-Based Expense Tracker** built with **HTML5, Vanilla CSS3, JavaScript (ES6+ Modules)**, and **Google Firebase Firestore**.

Track your everyday spending, categorize transactions, visualize expense breakdowns with interactive charts, manage monthly budgets, and seamlessly synchronize your data across devices in the cloud.

---

## ✨ Features

- **☁️ Cloud Firestore Integration:** Real-time data synchronization across all devices and browsers using Google Firebase Firestore.
- **⚡ Zero Setup Demo Mode:** Automatically falls back to local storage with pre-populated sample expenses if Firebase is not yet configured, letting you test immediately!
- **📝 Full CRUD Operations:** Add, view, edit, and delete expense entries with real-time updates.
- **🏷️ Smart Categories:** Pre-configured categories (Food & Dining, Shopping, Housing & Rent, Transportation, Utilities & Bills, Entertainment, Healthcare, Travel, Education, and Others) with color tokens and icons.
- **📊 Interactive Visual Analytics:**
  - **Category Doughnut Chart:** Dynamic percentage distribution powered by Chart.js.
  - **Monthly Spending Trend Bar Chart:** Visualizes spending trends over the last 6 months.
- **🎯 Monthly Budget Tracking:** Set and edit monthly budget goals with dynamic progress bars and over-budget warnings.
- **🔍 Advanced Search & Filters:**
  - Instant text search across titles, notes, and payment methods.
  - Category-based filter.
  - Time range filter (All Time, This Month, Last 30 Days, This Year).
  - Sorting by date (newest/oldest) or amount (highest/lowest).
- **💱 Multi-Currency Support:** Switch between USD ($), INR (₹), EUR (€), GBP (£), CAD (C$), AUD (A$), and JPY (¥).
- **📥 CSV Export:** One-click export of all transactions to a `.csv` spreadsheet report.
- **💎 Premium Fintech UI:** Glassmorphism, deep obsidian dark mode, smooth micro-interactions, responsive mobile layout, and custom toast notifications.

---

## 📁 Project Structure

```
cloud-based-expense-tracker/
│
├── index.html              # Main HTML5 application shell & modals
├── css/
│   └── style.css           # Modern Fintech design system & responsive layout
├── js/
│   ├── firebase-config.js  # Firebase configuration and storage helpers
│   └── app.js              # Core CRUD, Firestore sync, Chart.js & UI logic
└── README.md               # Setup and configuration guide
```

---

## 🚀 How to Run the Project Locally

Because this application uses standard **ES6 Modules** (`import` / `export`), it should be served over an HTTP/HTTPS local server (or Live Server in VS Code) for module loading.

### Option 1: Using Python (Recommended & Built-in)
Open a terminal in the project directory and run:

```bash
# Python 3
python -m http.server 3000
```
Then visit: `http://localhost:3000` in your web browser.

### Option 2: Using Node.js / npx
```bash
npx -y serve .
```

### Option 3: Using VS Code Live Server
1. Open the project folder in **Visual Studio Code**.
2. Install the **Live Server** extension by Ritwick Dey.
3. Right-click on `index.html` and click **"Open with Live Server"**.

---

## ⚙️ How to Configure Firebase Firestore

To store your expense records in the Google Cloud, follow these simple steps:

### Step 1: Create a Firebase Project
1. Navigate to the [Firebase Console](https://console.firebase.google.com/).
2. Click **"Add project"** (or **"Create a project"**).
3. Name your project (e.g., `spendcloud-expense-tracker`) and follow the on-screen steps (Google Analytics is optional).

### Step 2: Create a Cloud Firestore Database
1. In the Firebase console left sidebar, navigate to **Build** > **Firestore Database**.
2. Click **"Create database"**.
3. Choose your database location (select a location closest to you or your users).
4. For security rules, select **"Start in test mode"** for quick testing, and click **Enable**.

### Step 3: Configure Firestore Security Rules
Go to the **Rules** tab in your Firestore Database dashboard and update the rules:

```javascript
rules_version = '2';
service cloud.firestore {
  match /databases/{database}/documents {
    match /expenses/{expenseId} {
      allow read, write: if true; // Allows read/write during testing/development
    }
  }
}
```
> 💡 *Note: For production apps with user authentication, you can restrict rules to `allow read, write: if request.auth != null;`.*

### Step 4: Register a Web App & Get Credentials
1. In your Firebase Project Overview dashboard, click the **Web icon (`</>`)** to add a web application.
2. Enter an App nickname (e.g., `SpendCloud Web`) and click **Register app**.
3. Firebase will generate a `firebaseConfig` object looking like this:

```javascript
const firebaseConfig = {
  apiKey: "AIzaSyD-YourActualApiKeyHere",
  authDomain: "your-project-id.firebaseapp.com",
  projectId: "your-project-id",
  storageBucket: "your-project-id.appspot.com",
  messagingSenderId: "123456789012",
  appId: "1:123456789012:web:abcdef123456"
};
```

### Step 5: Apply Credentials to the App
You can add your credentials in **either of two convenient ways**:

#### Method A: Direct in the Web UI (No code editing needed!)
1. Open the app in your browser (`http://localhost:3000`).
2. Click the **"Firebase Setup"** button in the top right header.
3. Either click **"Quick Paste Firebase Config Object"** and paste the snippet, or type your `apiKey` and `projectId`.
4. Click **"Connect & Save"**. The status pill will change to **"Cloud Synced"** and automatically save expenses to your Firestore `expenses` collection!

#### Method B: Edit `js/firebase-config.js`
Open `js/firebase-config.js` and replace the placeholder values:

```javascript
export const defaultFirebaseConfig = {
  apiKey: "YOUR_ACTUAL_API_KEY",
  authDomain: "YOUR_PROJECT_ID.firebaseapp.com",
  projectId: "YOUR_PROJECT_ID",
  storageBucket: "YOUR_PROJECT_ID.appspot.com",
  messagingSenderId: "YOUR_MESSAGING_SENDER_ID",
  appId: "YOUR_APP_ID"
};
```

---

## 🛠️ Technologies Used

- **HTML5:** Semantic architecture, accessible forms, and SVG icon integration.
- **CSS3:** Custom properties (CSS variables), CSS Grid & Flexbox, glassmorphism, responsive breakpoints.
- **JavaScript (ES6+):** Modular scripts, asynchronous async/await, DOM manipulation, custom state management.
- **Firebase Firestore v10 (Modular SDK):** Real-time cloud database via official CDN ES modules.
- **Chart.js v4:** Interactive doughnut and bar charts.
- **FontAwesome 6:** Clean iconography.

---

## 📱 Browser Compatibility

SpendCloud is compatible with all modern browsers:
- Google Chrome (Desktop & Mobile)
- Mozilla Firefox
- Microsoft Edge
- Apple Safari (iOS & macOS)
