# Smart Semantic Resume–Job Recommendation System (Endee Vector DB)

**Python | FastAPI | Semantic Search | RAG**

An intelligent recruitment matching platform that applies vector embeddings and the Endee vector database to connect candidate resumes with job descriptions. The system integrates Retrieval-Augmented Generation (RAG) to deliver transparent and explainable match results.

---

## 🎯 Overview
This project demonstrates a practical implementation of semantic search for hiring workflows. By converting resumes and job descriptions into embedding vectors, the system detects the most relevant matches and provides meaningful explanations supporting each recommendation.

### Key Features
- **Context-Aware Matching:** Understands meaning instead of simple keyword comparison  
- **Bidirectional Matching:** Find suitable jobs for resumes or candidates for jobs  
- **Explainable Results:** Generates reasoning for every match  
- **Scalable Design:** Uses Endee vector database for fast similarity search  
- **REST API Service:** FastAPI endpoints with Swagger interactive documentation  

---

## 🏗️ Architecture
┌─────────────────────────┐
│ Endee Vector DB │
│ (localhost:8080) │
└───────────┬─────────────┘
│ HTTP API
┌───────────▼─────────────┐
│ FastAPI Backend │
│ - Embedding Generator │
│ - Matching Engine │
│ - RAG Explanation │
└───────────┬─────────────┘
│
┌───────────▼─────────────┐
│ Swagger UI │
│ (/docs) │
└─────────────────────────┘

---

## 🛠️ Technology Stack
- Endee Vector Database – Vector similarity search engine  
- Python 3.8+ – Core language  
- FastAPI – API framework  
- Sentence Transformers – Embedding generation  
- PyMuPDF (fitz) – Resume text extraction  
- Uvicorn – ASGI production server  
- WSL (Ubuntu) – Development environment  

---

## 📁 Project Structure
endee_resume_project/
├── backend/
│ ├── init.py
│ ├── app.py
│ ├── embed.py
│ ├── endee_client.py
│ ├── ingest_resumes.py
│ └── ingest_job.py
├── data/
│ ├── resumes/
│ └── jobs/
├── requirements.txt
└── README.md


---

## 📊 Dataset

### Resume Data
- Location: `data/resumes/`
- Format: PDF / TXT
- Contains: skills, education, work experience
- Structure: one file per candidate

### Job Description Data
- Location: `data/jobs/`
- Format: TXT
- Contains: requirements, responsibilities, skills
- Structure: one file per role

Benefits:
- Ethical local data usage  
- Easy reproducibility  
- Simple dataset extension  
- Academic-friendly dataset design  

---

## 🔍 RAG Matching Process

**1. Retrieval Phase**
- Perform vector similarity search in Endee to fetch relevant resumes/jobs

**2. Augmentation Phase**
- Combine retrieved data with query context (skills, experience, requirements)

**3. Generation Phase**
- Produce explainable reasoning for the match results

Advantages:
- Fact-based explanations  
- Transparent recommendation logic  
- Audit-friendly workflow  

---

## ⚙️ Installation & Setup

### Prerequisites
- Python 3.8+
- Git
- WSL (Ubuntu) for Endee

### Step 1 – Install Endee```bash
Endee runs at: http://localhost:8080

Step 2 – Install Dependencies
cd endee_resume_project
pip3 install -r requirements.txt

Step 3 – Ingest Data
python3 -m backend.ingest_resumes
python3 -m backend.ingest_job

Step 4 – Run API
uvicorn backend.app:app --reload

API Endpoints
Endpoint	Method	Description
/match/resume-to-job	POST	Find matching jobs for a resume
/match/job-to-resume	POST	Find matching resumes for a job
/explain/{match_id}	GET	Get explanation of match
/health	GET	Check API status

Testing
python3 -m pytest tests/
python3 -m pytest tests/test_api.py -v
locust -f tests/load_test.py

Performance

Embedding generation: ~50 ms per document

Vector search: <10 ms (top-10 results)

Average end-to-end latency: <100 ms

Throughput: 100+ requests per second

Security

Resume data stored locally

No external embedding API calls

Secure HTTP communication

No personal data stored in embeddings
License

MIT License

👤 Author

Kishora Y E 
GitHub: @Kishor9380
LinkedIn: Kishor
