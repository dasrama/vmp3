<h1 align="center">🎵 vmp3 — Video to MP3 Converter</h1>

<p align="center">
  <img src="https://img.shields.io/badge/Python-3.10+-blue?logo=python&logoColor=white" />
  <img src="https://img.shields.io/badge/FastAPI-Backend-009688?logo=fastapi&logoColor=white" />
  <img src="https://img.shields.io/badge/Docker-Containerization-2496ED?logo=docker&logoColor=white" />
</p>

<p align="center">
  <b>Microservice-based video to mp3 converter built with FFmpeg</b><br/>
  Leverages <b>RabbitMQ</b>, <b>Redis</b>, <b>Amazon S3</b>, and <b>Docker</b> for scalable processing.
</p>

---

## 🚀 Features
- 🔑 **User Authentication** for secure access  
- 🌐 **API Gateway** as a single entry point for clients  
- 🎶 **Video → MP3 Conversion** powered by **FFmpeg**  
- 🔔 **Notifications** on job completion  
- 📨 **Asynchronous processing** with **RabbitMQ**  
- ☁️ File storage on **Amazon S3**  
- ⚡ **Redis** for caching & fast job lookups  

---

## 🛠️ Architecture

<p align="center">
  <img src="https://img.shields.io/badge/RabbitMQ-Message%20Broker-FF6600?logo=rabbitmq&logoColor=white" />
  <img src="https://img.shields.io/badge/Redis-Cache-C00000?logo=redis&logoColor=white" />
  <img src="https://img.shields.io/badge/Amazon%20S3-Storage-569A31?logo=amazonaws&logoColor=white" />
  <img src="https://img.shields.io/badge/FFmpeg-Media%20Tool-007808?logo=ffmpeg&logoColor=white" />
</p>

The system is composed of **4 core microservices** + **RabbitMQ** backbone:

1. **🔑 User Auth Service**  
   - Handles user registration, login, and authentication  
   - Issues tokens for secure API access  

2. **🌐 API Gateway**  
   - Entry point for all client requests  
   - Routes requests to appropriate microservices  
   - Applies authentication & authorization  

3. **🎶 Conversion Service**  
   - Consumes jobs from **RabbitMQ**  
   - Converts videos to MP3 using **FFmpeg**  
   - Uploads output files to **Amazon S3**  

4. **🔔 Notification Service**  
   - Sends notifications (e.g., email, webhook, or push) when jobs finish  
   - Subscribes to **RabbitMQ** events  

---
