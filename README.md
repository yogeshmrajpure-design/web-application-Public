# 🎄 Xmas Countdown - AWS Jenkins CI/CD Pipeline

This project is a modern, responsive CSS and JavaScript countdown timer deployed using a fully automated DevOps pipeline.

## 🚀 Project Overview
* **Frontend:** HTML5, CSS3 (Modern Modules), and Vanilla JavaScript.
* **Target Date:** December 25, 2026.
* **Containerization:** Docker (Nginx Alpine base image).
* **CI/CD:** Jenkins Pipeline (Pipeline-as-Code).
* **Cloud Hosting:** AWS EC2 Instance.

## 🛠️ DevOps Architecture
The pipeline is triggered automatically via **GitHub Webhooks** on every push to the `main` branch.

1.  **Checkout:** Jenkins pulls the latest code from GitHub using SSH/Token credentials.
2.  **Docker Build:** A new Docker image is built using the provided `Dockerfile`. It handles the project's sub-directory structure using JSON-array path mapping.
3.  **Docker Deploy:** * Stops and removes any existing `css-container`.
    * Starts a new container mapping **Host Port 3000** to **Container Port 80**.

## 📦 Local Setup
If you want to run this project locally using Docker:
```bash
docker build -t xmas-countdown .
docker run -d -p 3000:80 xmas-countdown
