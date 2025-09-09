<h1 align="center">✨ vmp3 — Microservice Video ➡ MP3 Converter</h1>

<p align="center">
  <img src="https://img.shields.io/badge/Python-3.10+-blue?logo=python&logoColor=white" />
  <img src="https://img.shields.io/badge/FastAPI-Backend-009688?logo=fastapi&logoColor=white" />
  <img src="https://img.shields.io/badge/Docker-Containerization-2496ED?logo=docker&logoColor=white" />
</p>

<p align="center">
  <b>Scalable video-to-audio conversion platform</b><br/>
  Powered by <b>FFmpeg</b>, orchestrated with <b>RabbitMQ</b>, <b>Redis</b>, and <b>Amazon S3</b>.
</p>

---

## 🌟 Highlights
- 🔑 Secure **User Authentication**  
- 🌐 Central **API Gateway** for client access  
- 🎶 Fast **Video → MP3 Conversion** with FFmpeg  
- 🔔 Real-time **Notifications** after conversion  
- 📨 **RabbitMQ** for async task distribution  
- ☁️ **Amazon S3** for video & MP3 storage  
- ⚡ **Redis** caching for speed  

---

<p align="center">
  <img src="https://img.shields.io/badge/RabbitMQ-Message%20Broker-FF6600?logo=rabbitmq&logoColor=white" />
  <img src="https://img.shields.io/badge/Redis-Cache-C00000?logo=redis&logoColor=white" />
  <img src="https://img.shields.io/badge/Amazon%20S3-Storage-569A31?logo=amazonaws&logoColor=white" />
  <img src="https://img.shields.io/badge/FFmpeg-Media%20Tool-007808?logo=ffmpeg&logoColor=white" />
</p>

The ecosystem is composed of **4 microservices** + **RabbitMQ** backbone:

1. **🔑 User Auth Service**  
   Manages login, registration & token issuance  
   **Repo:** [vmp3-auth-service](https://github.com/dasrama/vmp3-user-auth)  

2. **🌐 API Gateway**  
   Routes requests, applies authentication, connects all services  
   **Repo:** [vmp3-api-gateway](https://github.com/dasrama/vmp3-api-gateway)  

3. **🎶 Conversion Service**  
   Converts video → MP3 with FFmpeg, saves results to S3  
   **Repo:** [vmp3-conversion-service](https://github.com/dasrama/vmp3-conversion-service)  

4. **🔔 Notification Service**  
   Sends notifications (email/webhook) after conversion is complete  
   **Repo:** [vmp3-notification-service](https://github.com/dasrama/vmp3-notification-service)  

---
