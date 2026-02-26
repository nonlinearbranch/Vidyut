#  Vidyut: Electricity Theft Detection System

**Vidyut** is an advanced multi layered anomaly detection system designed to detect electricity theft, visualize grid health, and identify risky consumers using a multi-layer machine learning pipeline. This system empowers utility companies to minimize revenue loss and ensure grid stability.

![Vidyut Logo](frontend/public/favicon.svg)

## 🌍 Sustainable AI Hackathon Perspective
**Vidyut** strongly aligns with **UN Sustainable Development Goals 7 (Affordable and Clean Energy)** and **9 (Industry, Innovation, and Infrastructure)**. By leveraging Explainable AI to combat electricity theft, Vidyut offers a highly practical, sustainable solution to grid management:

- **Carbon Footprint Reduction:** Electricity theft forces utility companies to over-generate power—often utilizing non-renewable sources to handle the unmetered load. By identifying and stopping theft, Vidyut directly prevents unnecessary carbon emissions and resource waste.
- **Resource Efficiency:** Vidyut utilizes a lightweight, compute-efficient ML pipeline (Isolation Forests, Z-Scores) rather than heavy, energy-intensive Deep Learning models. This makes the AI itself sustainable and cheap to deploy at scale.
- **Infrastructure Longevity:** Unmetered connections overload transformers, leading to hardware destruction and localized blackouts. Vidyut's geospatial mapping and transformer loss detection allow grid operators to proactively dispatch maintenance teams, saving the environmental cost of manufacturing and shipping replacement transformers.

##  Key Features

###  Multi-Layer Anomaly Detection
The core engine (`electrical_bomb.py`) uses a weighted ensemble of detection techniques:
1.  **Behavioral Analysis (ML):** Isolation Forest model to detect unusual consumption patterns.
2.  **Statistical Outliers:** Z-Score analysis for extreme deviation from personal history.
3.  **Transformer Loss:** Discrepancy between transformer input and total consumer load.
4.  **Peer Comparison:** Deviations from the average consumption of connected peers.
5.  **Voltage & Seasonal:** Alerts on voltage irregularities and seasonal consumption drops.

###  Risk Classification
The system categorizes consumers into risk levels for actionable insights:
-   **CRITICAL (Red):** Immediate theft likely. Top priority for inspection.
-   **HIGH (Orange):** strong indicators of theft (Top 20% risk).
-   **MILD (Yellow):** Suspicious behavior detected but requires monitoring.
-   **NORMAL (Green):** Safe patterns.

*Note: The "Anomalies" dashboard focuses strictly on **Critical** and **High** risk cases.*

###  Interactive Dashboard
-   **Grid Health Overview:** Real-time metrics on system status and estimated revenue loss.
-   **Transformer Analytics:** Interactive Pie & Bar charts showing risk distribution per transformer.
-   **Geospatial Map:** Google Maps integration that pins **High (Orange)** and **Critical (Red)** risk locations for field teams.
-   **Detailed Reporting:**
    -   **Detected Anomalies:** Actionable list of high-risk consumers with "Select Status" workflow.
    -   **Other Entries:** Secondary view for "Mild" and "Normal" consumers.

###  Export & Management
-   **PDF Export:** Generate professional audit reports (`electricity_theft_report.pdf`).
-   **Inspection Tracking:** Track status (Initiated, In Process, Completed) directly from the dashboard.

---

##  Tech Stack

### Frontend
-   **React 18** (Vite)
-   **Recharts** for interactive data visualization
-   **Lucide React** for modern UI icons
-   **Google Maps API** for geospatial visualization
-   **jspdf & autotable** for report generation

### Backend
-   **FastAPI** (Python 3.10+) - High-performance API
-   **Pandas & NumPy** - Data manipulation
-   **Scikit-Learn** - Machine Learning (Isolation Forest)
-   **Uvicorn** - ASGI Server

---


##  Project Structure

```
Vidyut/
├── backend/                  # FastAPI Backend
│   ├── app/
│   │   ├── core/             # Core Logic (ml_engine.py, electrical_bomb.py)
│   │   ├── services/         # Service Adapters
│   │   └── main.py           # API Entry point
│   └── requirements.txt      # Python Dependencies
├── frontend/                 # React Frontend
│   ├── src/
│   ├── public/
│   └── vite.config.js
├── Updated_scripts/          # Backup/Reference Scripts
└── README.md                 # Project Documentation
```

---

##  Installation & Setup

### Prerequisites
-   Node.js (v16+)
-   Python (v3.8+)

### 1. Clone the Repository
```bash
git clone https://github.com/nonlinearbranch/Vidyut.git
cd Vidyut
```

### 2. Backend Setup
Navigate to the backend folder and set up the Python environment.

```bash
cd backend
python -m venv venv
source venv/bin/activate  # On Windows: venv\Scripts\activate
pip install -r requirements.txt
```

**Run the Backend Server:**
```bash
# Run from the 'backend' directory
uvicorn app.main:app --reload --port 8000
```
*The backend API will be available at `http://localhost:8000`*

### 3. Frontend Setup
Open a new terminal, navigate to the **frontend** folder, and install dependencies.

```bash
# Return to root if in backend, then enter frontend
cd ../frontend 

npm install
```

**Run the Frontend Development Server:**
```bash
npm run dev
```
*The application should now be running at `http://localhost:5173`*

---

##  Usage Guide

1.  **Launch:** Open the web app at `http://localhost:5173`.
2.  **Upload Data:** Drag & drop your dataset (single merged CSV or the 5 standard separate files). [Sample](https://www.kaggle.com/datasets/samayrajat/final-electricity-skewed)
3.  **Analyze:** Watch the pipeline process data in real-time.
4.  **Investigate:**
    -   Check the **Global Map** for Red/Orange pins.
    -   Review the **Anomalies Table** and set inspection status.
    -   Click the **Pie Chart Icon** on the "Est. Loss" card to analyze specific transformers.
5.  **Report:** Download the PDF report for offline audits.

---

##  Contribution

Contributions are welcome! Please fork the repository and submit a pull request.

<!-- working -->
# Vidyut-Electricity_Theft_Detection_System
