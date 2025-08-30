# 🌩️ LLM Powered Cloud Architecture Recommendation Engine

## 📖 What is this project?
This project is an **AI-powered assistant** that helps developers and teams choose the **right cloud/software architecture** for their needs.  
It uses **Stack Overflow Q&A data, semantic search, and Large Language Models (LLMs)** to suggest patterns like Monolith, Microservices, Event-Driven, or Serverless — along with recommended tech stacks.

---

## 🚀 What problem does it solve?
Choosing the right architecture is tough:
- Too many options (monolith, microservices, serverless…).
- Tech stack decisions vary by team size, scalability, and workload.
- Searching the web often leads to fragmented or outdated answers.

👉 This engine **retrieves real-world developer discussions** from Stack Overflow and combines them with **LLM reasoning** + a **knowledge base of best practices** to give **tailored recommendations**.
---

## 📊 Dataset Used

We use the Stack Overflow “stacksample” dataset
 from Kaggle.
It contains:

Questions.csv → Stack Overflow questions

Answers.csv → Accepted & top answers

Tags.csv → Question tags

📌 These files are not included in this repo (due to size), but they will be downloaded automatically via Kaggle API when you run the notebook.
---

## 🔧 Tech Stack Used
- **Python + Jupyter** → development environment
- **LangChain + HuggingFaceHub** → LLM interface
- **Falcon-7B-Instruct** → main model for recommendations
- **Mistral-7B-Instruct** → optional model for reasoning-heavy outputs
- **SentenceTransformers (MiniLM-L6-v2)** → embeddings for semantic search
- **FAISS** → vector database for fast retrieval
- **Pandas, NumPy** → data preprocessing
- **YAML** → knowledge base for architecture patterns
- **Kaggle API** → dataset download (Stack Overflow sample)

---

## ⚙️ How it Works
1. **Dataset**: Downloads Stack Overflow `stacksample` dataset from Kaggle.  
2. **Preprocessing**: Cleans Questions, Answers, and Tags → filters architecture/cloud-related tags.  
3. **Chunking**: Splits long answers into ~250 token chunks.  
4. **Embeddings**: Uses MiniLM-L6-v2 to embed chunks into vectors.  
5. **FAISS Search**: Builds index for fast retrieval.  
6. **Knowledge Base**: Architecture patterns (monolith, microservices, etc.) defined in YAML.  
7. **LLM Generation**: Falcon-7B (or Mistral-7B) takes the query + retrieved chunks + KB → generates recommendation.  

---

## 🛠️ How to Run (Google Colab)
1. Upload this project folder to Colab.  
2. Install dependencies:
   ```bash
   pip install -r requirements.txt
