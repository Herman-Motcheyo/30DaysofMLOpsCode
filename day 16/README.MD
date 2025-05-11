# 🌦️ Weather Data Pipeline – Airflow, PostgreSQL, Node.js & Flutter

A real-world, end-to-end ETL pipeline for collecting, transforming, storing, and visualizing weather data, built as part of my **#30DaysOfMLOpsCode** challenge.

## 🚧 Project Status: In Development
The core architecture is defined and partially implemented. Integration and testing of services are ongoing.

---

## 📦 Architecture Overview

This project automates the ETL process of fetching real-time weather data, storing it in PostgreSQL, and serving it via a REST API to a mobile app built with Flutter.

### 🔁 ETL Pipeline (Airflow + Astro)

- **Scheduler, Webserver, Workers** are containerized via Docker
- Uses `SimpleHttpOperator` to fetch data from the [OpenWeather API](https://openweathermap.org/api)
- Airflow DAG handles:
  - Fetching data
  - Fahrenheit to Celsius conversion
  - Data cleaning and preparation
  - Dynamic table creation using `PostgresHook`

### 🧪 Data Transformation

- Converts temperatures from °F to °C
- Removes irrelevant fields or malformed records
- Prepares data for analytics and ML tasks (e.g. forecasting)

### 🗄️ Data Storage (PostgreSQL)

- Central relational database for storing historical weather records
- Used by both the API and potential ML workloads
- Tables created dynamically if missing

### 🌐 REST API (Node.js + Express)

- Built with Express.js and PostgreSQL client
- Provides endpoints to query weather data
- Future-proof: ready for ML inference integration

### 📱 Mobile Interface (Flutter)

- Displays real-time weather data
- Simple and intuitive UI for mobile weather insights

---

## ⚙️ Technologies Used

| Layer | Stack |
|-------|-------|
| Orchestration | Airflow via [Astronomer](https://www.astronomer.io/) |
| Transformation | Python (in Airflow DAG) |
| Storage | PostgreSQL |
| API | Node.js + Express |
| Frontend | Flutter |
| DevOps | Docker + Docker Compose |

---

## 💡 MLOps Use Case

This ETL pipeline is designed as a foundation for:

- 🔮 Weather forecasting models
- 🧠 Anomaly detection (e.g., unexpected spikes or dips)
- 📈 Trend analysis over time

---

## 🐞 Current Challenges

- Airflow ↔ PostgreSQL integration via `PostgresHook` took time to configure
- Full DAG testing still ongoing
- Docker Compose integration for multi-service orchestration
- Handling edge cases like API errors or missing data

---

![alt text](<flow_challege (2).jpg>)
