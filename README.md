# IoT Temperature and Humidity Monitoring System

## Project Overview

This IoT project is designed to monitor temperature and humidity levels using an Arduino-based sensor system. The system sends data to a Django backend server every 20 minutes, which processes and stores it in a database. A React-based frontend provides a user-friendly interface for viewing statistics, charts, and alerts, ensuring temperature and humidity remain within a safe range.

---

## Features

1. **Temperature and Humidity Monitoring**  
   - Real-time data collection using DHT11/DHT22 sensors connected to an Arduino.
   - Data transmission to the Django server every 20 minutes.

2. **Alerts System**  
   - Automatically detects abnormal temperature or humidity levels.
   - Sends alerts to the React frontend until the issue is resolved.

3. **Data Visualization**  
   - Interactive charts to display:
     - Temperature and humidity trends over the last week, month, and year.
     - Maximum and minimum temperature and humidity levels.
     - Number of issues detected and resolved.
     - Median time taken to fix issues.

4. **Issue Tracking**  
   - Tracks all alerts with timestamps.
   - Displays the status of each issue (resolved/unresolved).

---

## System Architecture

1. **Hardware (Arduino)**  
   - Arduino collects temperature and humidity data using the sensor.
   - Sends the data via Wi-Fi module (e.g., ESP8266) to the Django server.

2. **Backend (Django)**  
   - REST API endpoints to receive, store, and serve sensor data.
   - Logic for detecting abnormalities and creating alerts.
   - Serves data and alerts to the frontend.

3. **Frontend (React)**  
   - Displays real-time sensor data and charts.
   - Shows active alerts and provides a resolution workflow.
   - Interactive dashboards with statistical analysis.

---

## Installation

### Prerequisites
- Arduino with DHT11/DHT22 sensor.
- Django server with Python 3.x.
- React frontend with Node.js.

### Steps

1. **Setup Arduino**  
   - Connect the DHT sensor to the Arduino.
   - Flash the Arduino with the provided code in `/arduino-code`.
   - Ensure the Wi-Fi module is configured to send data to the Django server.

2. **Backend (Django)**  
   - Navigate to `/backend`.
   - Install dependencies:
     ```bash
     pip install -r requirements.txt
     ```
   - Run migrations:
     ```bash
     python manage.py makemigrations
     python manage.py migrate
     ```
   - Start the server:
     ```bash
     python manage.py runserver
     ```

3. **Frontend (React)**  
   - Navigate to `/frontend`.
   - Install dependencies:
     ```bash
     npm install
     ```
   - Start the development server:
     ```bash
     npm start
     ```

---

## Usage

1. **Monitor Sensor Data**  
   - Access the React dashboard to view temperature and humidity trends.

2. **Resolve Alerts**  
   - View active alerts on the React dashboard.
   - Mark alerts as resolved once the issue is fixed.

3. **View Statistics**  
   - Explore charts to analyze historical data.
   - Gain insights into the system's performance and issue resolution.

---

## API Endpoints

### Arduino to Django
- `POST /api/sensor-data/`
  - Payload: `{ "temperature": float, "humidity": float }`
  - Stores data and checks for abnormal conditions.

### Frontend to Django
- `GET /api/sensor-data/`
  - Retrieves historical sensor data.
- `GET /api/alerts/`
  - Retrieves active and resolved alerts.
- `POST /api/alerts/resolve/`
  - Marks an alert as resolved.

---

## Charts and Analytics

- **Trends:** Temperature and humidity trends over different periods (week, month, year).
- **Statistics:** Maximum, minimum, and average temperature and humidity.
- **Issue Analytics:** Number of issues detected, median resolution time.

---

## Future Enhancements

1. Add push notifications for critical alerts.
2. Integrate predictive analytics for better environmental control.
3. Enable multi-sensor support for larger environments.

---

## Contributing

We welcome contributions!  
Fork this repository and submit a pull request for any enhancements or fixes.

