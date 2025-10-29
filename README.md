# 📸 Snapchat Clone – DevOps CI/CD Project

A simple Snapchat-style landing page built with **HTML + CSS**, packaged with **Maven**, containerized with **Docker**, and deployed automatically to **AWS EC2** using **Jenkins**.

---

## 🚀 Project Overview

This project demonstrates a **complete DevOps CI/CD pipeline** for deploying a static web application.  
It uses:
- **GitHub** → Source Code Management  
- **Jenkins** → Continuous Integration & Continuous Deployment  
- **Maven** → Build and package `.war` file  
- **Docker** → Containerize the app  
- **Tomcat** → Application server  
- **AWS EC2** → Deployment environment  

---

## 🧩 Tech Stack
| Tool | Purpose |
|------|----------|
| **HTML, CSS** | Frontend (Snapchat-style landing page) |
| **Maven** | Build management and `.war` packaging |
| **Tomcat** | Web application server |
| **Docker** | Containerization |
| **Jenkins** | CI/CD automation |
| **AWS EC2** | Cloud hosting |
| **GitHub** | Source control |

---

## ⚙️ Setup Instructions

### 🧱 1. Prerequisites
- Java 11+
- Maven 3.9+
- Docker installed
- Jenkins installed
- AWS EC2 instance running (with Docker installed)
- GitHub account

---

### ⚒️ 2. Build the Project
```bash
mvn clean package
```
### 3. Provide jenkins user permission
```bash
visudo
```
