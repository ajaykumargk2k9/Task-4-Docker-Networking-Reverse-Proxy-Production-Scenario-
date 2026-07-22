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

---

We use Nginx which acts as a high-performance reverse proxy and web server. It routes requests to backend services and is widely used in production.
Docker Networking allows containers to communicate securely using service names instead of IP addresses.

---

# Project Setup & Creating the Employee Service

# Step 1: Create the Project Folder

Open Terminal 

Navigate to the location where we keep our projects.

cd C:\Users\asus

Create the main project folder

mkdir employee-management-system

Go inside it

cd employee-management-system

![image alt](https://github.com/ajaykumargk2k9/Task-4-Docker-Networking-Reverse-Proxy-Production-Scenario-/blob/main/Images/Employee%20Management%20System.PNG?raw=true)

---

Open VS Code

code .

![image alt](https://github.com/ajaykumargk2k9/Task-4-Docker-Networking-Reverse-Proxy-Production-Scenario-/blob/main/Images/VS%20Code%20Employee%20Management%20System.PNG?raw=true)

---

# Step 2: Create the Folder Structure

![image alt](https://github.com/ajaykumargk2k9/Task-4-Docker-Networking-Reverse-Proxy-Production-Scenario-/blob/main/Images/Project%20Structure.PNG?raw=true)

---

# Step 3: Create Employee Service

Go into the folder

cd employee-service

Initialize Node.js

npm init -y

![image alt](https://github.com/ajaykumargk2k9/Task-4-Docker-Networking-Reverse-Proxy-Production-Scenario-/blob/main/Images/Create%20Employee%20service.PNG?raw=true)

---

# Step 4: Install Express

Run

npm install express

![image alt](https://github.com/ajaykumargk2k9/Task-4-Docker-Networking-Reverse-Proxy-Production-Scenario-/blob/main/Images/employee%20service%20install%20express.PNG?raw=true)

---

# Step 5: Create app.js

Inside employee-service, create app.js

Paste the code 

![image alt](https://github.com/ajaykumargk2k9/Task-4-Docker-Networking-Reverse-Proxy-Production-Scenario-/blob/main/Images/app.js%20code.PNG?raw=true)

---

# Step 6: Start the Application

Run: node app.js

We should see: Employee Service running on port 3001

![image alt](https://github.com/ajaykumargk2k9/Task-4-Docker-Networking-Reverse-Proxy-Production-Scenario-/blob/main/Images/Employee%20service%20running%20cmd.PNG?raw=true)

---

# Step 7: Test in Browser

http://localhost:3001/employees

Expected Output: Employee Service Running

![image alt](https://github.com/ajaykumargk2k9/Task-4-Docker-Networking-Reverse-Proxy-Production-Scenario-/blob/main/Images/Employee%20service%20running%20browser.PNG?raw=true)

---

# Create the Department Service

# Step 1: Go to Department Service

Open a new terminal

cd department-service

# Step 2: Initialize Node Project

npm init -y

![image alt](https://github.com/ajaykumargk2k9/Task-4-Docker-Networking-Reverse-Proxy-Production-Scenario-/blob/main/Images/Department%20service%20npm.PNG?raw=true)

---

# Step 3: Install Express

npm install express

![image alt](https://github.com/ajaykumargk2k9/Task-4-Docker-Networking-Reverse-Proxy-Production-Scenario-/blob/main/Images/department%20service%20install%20express.PNG?raw=true)

---

# Step 4: Create app.js

const express = require("express");

const app = express();

const PORT = 3002;

app.get("/departments", (req, res) => {
    res.send("Department Service Running");
});

app.listen(PORT, () => {
    console.log(`Department Service running on port ${PORT}`);
});

---

# Step 5: Run the Service

node app.js

![image alt](https://github.com/ajaykumargk2k9/Task-4-Docker-Networking-Reverse-Proxy-Production-Scenario-/blob/main/Images/Department%20service%20running%20cmd.PNG?raw=true)

---

# Step 6: Test

http://localhost:3002/departments

![image alt](https://github.com/ajaykumargk2k9/Task-4-Docker-Networking-Reverse-Proxy-Production-Scenario-/blob/main/Images/Department%20service%20running%20browser.PNG?raw=true)


---

# Create the Payroll Service

# Step 1: Navigate to Payroll Service

Open a new terminal

cd payroll-service

# Step 2: Initialize Node.js

npm init -y

![image alt](https://github.com/ajaykumargk2k9/Task-4-Docker-Networking-Reverse-Proxy-Production-Scenario-/blob/main/Images/Payroll%20npm.PNG?raw=true)

---

# Step 3: Install Express

npm install express

![image alt](https://github.com/ajaykumargk2k9/Task-4-Docker-Networking-Reverse-Proxy-Production-Scenario-/blob/main/Images/Payroll%20install.PNG?raw=true)

---

# Step 4: Create app.js

const express = require("express");

const app = express();

const PORT = 3003;

app.get("/payroll", (req, res) => {
    res.send("Payroll Service Running");
});

app.listen(PORT, () => {
    console.log(`Payroll Service running on port ${PORT}`);
});

---

# Step 5: Run the Service

node app.js

![image alt](https://github.com/ajaykumargk2k9/Task-4-Docker-Networking-Reverse-Proxy-Production-Scenario-/blob/main/Images/Payroll%20running%20cmd.PNG?raw=true)

---

# Step 6: Test

http://localhost:3003/payroll

![image alt](https://github.com/ajaykumargk2k9/Task-4-Docker-Networking-Reverse-Proxy-Production-Scenario-/blob/main/Images/Payroll%20running%20browser.PNG?raw=true)

---

# Create the Attendance Service

# Step 1: Navigate to Attendance Service

Open a new terminal

cd attendance-service

# Step 2: Initialize Node.js

npm init -y

![image alt](https://github.com/ajaykumargk2k9/Task-4-Docker-Networking-Reverse-Proxy-Production-Scenario-/blob/main/Images/Attendance%20npm.PNG?raw=true)

---

# Step 3: Install Express

npm install express

![image alt](https://github.com/ajaykumargk2k9/Task-4-Docker-Networking-Reverse-Proxy-Production-Scenario-/blob/main/Images/Attendance%20install%20express.PNG?raw=true)

---

# Step 4: Create app.js

const express = require("express");

const app = express();

const PORT = 3004;

app.get("/attendance", (req, res) => {
    res.send("Attendance Service Running");
});

app.listen(PORT, () => {
    console.log(`Attendance Service running on port ${PORT}`);
});

---

# Step 5: Run the Service

node app.js

![image alt](https://github.com/ajaykumargk2k9/Task-4-Docker-Networking-Reverse-Proxy-Production-Scenario-/blob/main/Images/Attendance%20running%20cmd.PNG?raw=true)

---

# Step 6: Test

http://localhost:3004/attendance

![image alt](https://github.com/ajaykumargk2k9/Task-4-Docker-Networking-Reverse-Proxy-Production-Scenario-/blob/main/Images/Attendance%20running%20browser.PNG?raw=true)

---

# Final Microservices Architecture

![image alt](https://github.com/ajaykumargk2k9/Task-4-Docker-Networking-Reverse-Proxy-Production-Scenario-/blob/main/Images/Final%20Microservices%20Architecture.PNG?raw=true)

Currently users access each service directly using its port.

Nginx will expose only one entry point. 

Nginx receives the request and forwards it to the correct service.
