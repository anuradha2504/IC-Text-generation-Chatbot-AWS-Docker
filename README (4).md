# 🤖 AI Story Generator API (Gemini 2.0 Flash)

A lightweight, high-performance **Text Generation Service** built using **FastAPI** and powered by Google's **Gemini 2.0 Flash** model.
The solution is containerized with **Docker** and designed for deployment on **AWS EC2** for scalable cloud-based inference.

---

## 🚀 Features

- 💬 Story Generator API
- ⚡️ **FastAPI Backend**: High-performance, asynchronous REST API.
- 🤖 **Gemini 2.0 Flash**: Utilizes Google's latest model for rapid story generation.
- 🐳 **Dockerized**: Fully containerized for consistent deployment.
- ☁️ **AWS EC2 Ready**: Configured for public cloud access.
- 🔌 **Simple Endpoint**: Clean JSON-based API for generating creative content.
---

## 🧩 Technology Stack

| Layer | Technology | Description |
|-------|-------------|-------------|
| Framework | FastAPI | RESTful API framework |
| Model | Gemini 2.0 Flash | Generative AI Model by Google |
| Language | Python 3.11 | Runtime environment |
| Packaging | Docker | Containerization |
| Cloud | AWS EC2 (Ubuntu 24.04) | Hosting and deployment |

---

## 🧱 Project Structure

```
├── app.py                  # Main FastAPI application with Gemini integration
├── requirements.txt        # Python dependencies (fastapi,requests,etc.)
├── Dockerfile              # Docker build configuration.Container setup ( APIs)
├── supervisord.conf        # Manages multiple processes
└── README.md               # Documentation
```
## ⚙️ Setup & Local Run

### 1️⃣ Add Your API Key
Create `.streamlit/secrets.toml` and include:
```toml
OPENAI_API_KEY = "YOUR_API_KEY"
```
Since this is a headless API (no UI), you interact with it using HTTP requests (Postman, cURL, or Python scripts).

### **Endpoint:** `POST /generate-story`

**Request Body:**
```json
{
  "prompt": "A brave knight fighting a dragon in space",
  "max_tokens": 500
}
**Response:**
JSON

{
  "story": "Once upon a time in a galaxy far, far away..."
}


### 2️⃣ Install Requirements
```bash
pip install -r requirements.txt
```

### 3️⃣ Run Locally
```bash
python lang_chat.py    # Runs LangChain API on port 8000
python llamaindex_chat.py  # Runs LlamaIndex API on port 8001
streamlit run app.py   # Runs Streamlit UI on port 8501
```

Access at 👉 **http://localhost:8501**

---

## 🐳 Docker Deployment

### Build Image
```bash
sudo docker build -t gemini-story-api .
```

### Run Container
```bash
sudo docker run -d -p 8001:8001 gemini-story-api
```

Then open your browser at  
👉 **http://16.171.139.199:8001/docs/**
---

## ☁️ AWS EC2 Deployment (Free Tier Eligible)

1. Launch an **Ubuntu 24.04 EC2 Instance (t2.micro)**  
2. SSH into instance  
3. Install Docker  
   ```bash
   sudo apt update && sudo apt install docker.io -y
   ```
4. Copy project files using **WinSCP** or **git clone**  
5. Build & Run Docker  
   ```bash
   docker build -t ai-frameworks-chatbot .
   docker run -d -p 8501:8501 -p 8000:8000 -p 8001:8001 ai-frameworks-chatbot
   ```
6. Add **Inbound Rules** to Security Group  
   - TCP 22 → SSH (Your IP only)  
   - TCP 8501, 8000, 8001 → 0.0.0.0/0  

✅ Access at:  
**http://<your-ec2-public-ip>:8501**

---

## 🧠 Technical Architecture

### 📘 Architecture Overview

Below is the architecture representing:
- FastApi Powered by Gemini
- Docker container orchestration
- AWS EC2 deployment layer

<img width="1536" height="1024" alt="image" src="https://github.com/anuradha2504/IC-Text-generation-Chatbot-AWS-Docker/blob/main/System-architecture-flow-Story-generation-aws.png" />

---

🌍 **Deployed Endpoint:**  
End Point -16.171.139.199:8001/docs/

---

## 📚 Example Output

### 🔹 Output responses
<img width="680" alt="OutPut Response" src="https://github.com/anuradha2504/IC-Text-generation-Chatbot-AWS-Docker/blob/main/AWS_deployment.docx" />

---

**🧠 Application Logic**
The application uses a straightforward architecture:
FastAPI receives the StoryRequest (prompt + token limit).
The app constructs a payload for the Google Gemini API.
It authenticates using the API Key configured in app.py.
It sends a POST request to generativelanguage.googleapis.com.
The generated text is extracted and returned as JSON.

## 🔐 Security Notes

- ✅ API Keys are **never hardcoded** 
- ✅ AWS-level network security (controlled inbound rules)
---

## 📄 Repository & License

🧾 **Repository:** (https://github.com/anuradha2504/IC-Text-generation-Chatbot-AWS-Docker/tree/main) 

🛡️ **License:** MIT License © 2025 — Open for educational and research use

---

