<h1 align="center">🎵 vmp3 — Video to MP3 Converter</h1>

<p align="center">
  <img src="https://img.shields.io/badge/Python-3.10+-blue?logo=python&logoColor=white" />
  <img src="https://img.shields.io/badge/FastAPI-Backend-009688?logo=fastapi&logoColor=white" />
  <img src="https://img.shields.io/badge/Docker-Containerization-2496ED?logo=docker&logoColor=white" />
</p>

<p align="center">
  <b>Microservice-based video to mp3 converter built with FFmpeg</b><br/>
  Leverages <b>RabbitMQ</b>, <b>Redis</b>, and <b>Amazon S3</b> for distributed processing and storage.
</p>

---

## 🚀 Features
- 🎥 Upload video and get high-quality **MP3** output  
- 📦 Scalable microservice architecture  
- 📨 Asynchronous processing with **RabbitMQ**  
- ⚡ Fast lookups with **Redis**  
- ☁️ Store and retrieve files from **Amazon S3**  
- 🔄 Conversion handled by **FFmpeg** workers  
- 🐳 Fully containerized with **Docker**  

---

## 🛠️ Architecture

<p align="center">
  <img src="https://img.shields.io/badge/RabbitMQ-Message%20Broker-FF6600?logo=rabbitmq&logoColor=white" />
  <img src="https://img.shields.io/badge/Redis-Cache-C00000?logo=redis&logoColor=white" />
  <img src="https://img.shields.io/badge/Amazon%20S3-Storage-569A31?logo=amazonaws&logoColor=white" />
  <img src="https://img.shields.io/badge/FFmpeg-Media%20Tool-007808?logo=ffmpeg&logoColor=white" />
</p>

The system is composed of **4 microservices**:

1. **📤 Upload Service**  
   - Accepts video uploads  
   - Stores them in **S3**  
   - Publishes conversion jobs to **RabbitMQ**

2. **🎶 Conversion Service**  
   - Consumes jobs from **RabbitMQ**  
   - Converts videos to MP3 using **FFmpeg**  
   - Saves results to **S3**

3. **📊 Metadata Service**  
   - Tracks job status, metadata, and progress  
   - Uses **Redis** for fast lookups

4. **🌐 API Gateway / Download Service**  
   - Provides REST API endpoints  
   - Clients can check job status & download MP3s  

---

## ⚡ System Workflow

```mermaid
flowchart LR
    A[Client Uploads Video] -->|POST /upload| B[Upload Service]
    B -->|Stores Video| S3[(Amazon S3)]
    B -->|Publish Job| RQ[(RabbitMQ)]
    RQ --> C[Conversion Service]
    C -->|Convert with FFmpeg| MP3[MP3 File]
    C -->|Store MP3| S3
    C -->|Update Status| R[Redis]
    A -->|Check Status / Download| D[API Gateway]
    D --> R
    D --> S3
