# Distributed Video Streaming with Python and Kafka

A simple distributed video streaming pipeline using **Kafka**, **Python**, **OpenCV**, and **Flask**.  
This project demonstrates how to stream video frames from a producer to a consumer over Kafka, and serve the video in a web browser.

---

## ⚡ Features

- **Kafka-based streaming:** Frames are published to a Kafka topic and consumed in real-time.
- **Video sources:** Supports webcam or video file input.
- **Web streaming:** Flask serves video frames to `http://localhost:5000/video`.
- **Distributed-ready:** Can be extended with multiple producers/consumers and multi-broker Kafka clusters.

---

## 🛠️ Prerequisites

- [Docker & Docker Compose](https://docs.docker.com/compose/install/)
- Python 3.8+
- WSL2 (if using Windows)
- Optional: webcam for live streaming

---

## 🚀 Setup

1. **Clone the repository**
```bash
git clone https://github.com/radmehr-vafadar/Distributed-Video_streaming.git
cd Distributed-Video_streaming
```

2. **Start Kafka & Zookeeper**
```bash
docker compose up -d
```

3. **Set up Python environment**
```bash
python3 -m venv venv
source venv/bin/activate
pip install -r requirements.txt
```

---

## 🎬 Running the Project

1. **Start the consumer (Flask server)**
```bash
cd consumer
python consumer.py
```
Open your browser at:
```bash
http://localhost:5000/video
```

2. **Start the producer (video source)**
- **Webcam:**
```bash
cd producer
python producer.py
```
- **Video file:**
```bash
python producer.py ../videos/sample.mp4
```

The producer publishes frames to Kafka.

The consumer serves the stream in your browser.

---

## 🔧 Customization

Change the Kafka topic or broker in `producer/producer.py` and `consumer/consumer.py`:
```python
KAFKA_TOPIC = "video-stream"
KAFKA_SERVER = "localhost:9092"
```
Replace `producer.py` input with any video file.

---

## ⚡ Notes

- WSL2 may not support direct webcam access; use a video file if needed.
- Flask runs in development mode; for production, use a WSGI server (e.g., Gunicorn).
- Docker ensures Kafka/Zookeeper runs consistently across environments.
