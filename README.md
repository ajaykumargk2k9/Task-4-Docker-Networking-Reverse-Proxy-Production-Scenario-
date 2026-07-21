# Task-4-Docker-Networking-Reverse-Proxy-Production-Scenario-
Task 4: Docker Networking &amp; Reverse Proxy (Production Scenario)

---

🎯 Objective

Build an 👨‍💼 Employee Management System using 4️⃣ Microservices 🐳 Docker Networking 📦 Docker Compose and 🌐 Nginx Reverse Proxy to enable seamless communication between services through a single entry point.

---

In this project we use a Microservices Architecture. This architecture is used because instead of building one large application (Monolithic Architecture) companies divide the application into multiple smaller independent services. This makes the application easier to develop, test, deploy and maintain.

For example in an Employee Management System we can have the following four microservices:

👨‍💼 Employee Service – Manages employee details.
🏢 Department Service – Manages department information.
💰 Payroll Service – Handles employee salary and payroll.
📅 Attendance Service – Tracks employee attendance.

Each service works independently and has:

📁 Its own source code
🐳 Its own Dockerfile
📦 Its own Docker container
🚀 Its own deployment

Even though these services are independent they communicate with each other whenever required to provide a complete Employee Management System.

---

🏗️ Project Architecture – Employee Management System

![image alt](https://github.com/ajaykumargk2k9/Task-4-Docker-Networking-Reverse-Proxy-Production-Scenario-/blob/main/Images/Project%20Architecture%20%E2%80%93%20Employee%20Management%20System.PNG?raw=true)
