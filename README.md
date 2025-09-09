# 🎵 vmp3 — Video to MP3 Converter (Microservice Architecture)

`vmp3` is a distributed system that converts video files into MP3 audio using **FFmpeg**.  
It is designed with a **microservice architecture** for scalability and reliability, leveraging:

- **RabbitMQ** → For asynchronous job queueing and task distribution.
- **Redis** → For caching and fast data access.
- **Amazon S3** → For secure and scalable storage of uploaded videos and generated MP3 files.
- **FFmpeg** → For efficient video-to-audio conversion.

---

## 🚀 Features

- Upload videos and convert them into high-quality MP3 files.
- Scalable job processing using **RabbitMQ workers**.
- Caching layer with **Redis** for faster metadata and job lookups.
- File storage and retrieval from **Amazon S3**.
- Modular **microservices** that can be scaled independently.

---

## 🛠️ Architecture

The system consists of **4 microservices**:

1. **Upload Service**  
   - Handles file uploads from clients.  
   - Stores video files in **Amazon S3**.  
   - Publishes conversion tasks to **RabbitMQ**.

2. **Conversion Service**  
   - Consumes video conversion tasks from **RabbitMQ**.  
   - Uses **FFmpeg** to convert videos into MP3 format.  
   - Uploads the converted MP3 back to **Amazon S3**.

3. **Metadata Service**  
   - Stores and retrieves job status, file metadata, and conversion progress.  
   - Uses **Redis** for quick lookups and caching.

4. **API Gateway / Download Service**  
   - Provides a unified API for clients.  
   - Handles job creation, status queries, and MP3 download links.  
   - Connects all services together.

---

## 📦 Tech Stack

- **Backend:** Python (FastAPI / Flask)  
- **Message Broker:** RabbitMQ  
- **Cache/Store:** Redis  
- **File Storage:** Amazon S3  
- **Media Processing:** FFmpeg  
- **Containerization:** Docker & Docker Compose  

---

## 🔧 How It Works

1. Client uploads a video via the **Upload Service**.  
2. Upload service stores the video in **S3** and sends a conversion task to **RabbitMQ**.  
3. **Conversion Service** picks the task, processes it with **FFmpeg**, and stores the MP3 back in **S3**.  
4. **Metadata Service** updates job status in **Redis** for fast lookups.  
5. Client queries the **API Gateway** to check conversion status or download the final MP3.

---

## 📂 Repository Structure

Each microservice is maintained as an independent repository:

- [Upload Service](https://github.com/your-username/vmp3-upload-service)  
- [Conversion Service](https://github.com/your-username/vmp3-conversion-service)  
- [Metadata Service](https://github.com/your-username/vmp3-metadata-service)  
- [API Gateway / Download Service](https://github.com/your-username/vmp3-api-gateway)  

---
