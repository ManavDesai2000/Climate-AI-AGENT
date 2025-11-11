# 🌤️ Climate-AI-Agent

**CLIMATE-AI-AGENT** is a multi-agent system built with **LangGraph** that analyzes **global air quality data** and turns it into **actionable recommendations** for residents, city planners, and policymakers.

It combines:

- 🧮 **Data-aware reasoning** over a real-world AQI dataset (per city & country)  
- 📚 **RAG (Retrieval-Augmented Generation)** for health & climate context  
- 🧠 **Agentic orchestration with LangGraph** (Router, Data, RAG, Planner, QA agents)  
- 💬 A conversational interface you can run directly from **Google Colab**

---

## ✨ Key Features

- **Data Agent (Pandas + LangGraph)**  
  - Answers questions directly from a Kaggle AQI dataset with columns:
    - `Country`, `City`
    - `AQI Value`, `AQI Category`
    - `CO / NO2 / Ozone / PM2.5 AQI Value + Category`
    - `lat`, `lng`
  - Supports queries like:
    - _“Which country has most number of cities with AQI more than 100?”_
    - _“Which cities in Brazil have AQI category listed as Good?”_
    - _“Show the top 5 cities by highest AQI.”_
    - _“What is the AQI and PM2.5 profile for Indore?”_

- **RAG Agent (Chroma + LangChain)**  
  - Retrieves knowledge about:
    - AQI category thresholds (Good, Moderate, Unhealthy, etc.)
    - Health impacts of PM2.5 and long-term exposure
    - How climate and weather patterns influence air quality

- **Planner Agent (LLM)**  
  - Combines:
    - `data_insight` from the Data Agent  
    - `rag_context` from the RAG Agent  
  - Returns:
    - Plain-language explanation  
    - 3–5 concrete recommendations (e.g., policy ideas, personal actions)  
    - Notes on at-risk groups (children, elderly, pre-existing conditions)

- **Router + QA Agents (LangGraph)**  
  - Router decides which agent should handle each query:
    - Data vs. RAG vs. Planner vs. QA
  - QA agent acts as a fallback for general questions.

---

## 🛠 Tech Stack

- **Language:** Python (Google Colab)
- **Orchestration:** [LangGraph](https://github.com/langchain-ai/langgraph)
- **LLM + RAG:** LangChain, OpenAI (optional, mock mode supported), Chroma
- **Data:** Kaggle – *World Air Quality Index by City and Coordinates*
- **Environment:** Google Colab (copy–paste friendly)

---

## 📊 Example Queries & Outputs

### 1. Country-level AQI threshold

**User:**  
> Which country has most number of cities with AQI more than 100?

**Bot:**  
> The country with the most cities with AQI above 100 is **India** with **475** cities.  
>  
> Top 5 countries by number of cities with AQI above 100:  
> - India: 475 cities  
> - China: 251 cities  
> - United States of America: 146 cities  
> - Pakistan: 94 cities  
> - Mexico: 74 cities  

---

### 2. Planner / recommendations for city planners

**User:**  
> What recommendations would you give to city planners?

**Bot (Planner Agent):**  
- Enhance public transport and promote electric vehicles  
- Expand green spaces and urban forests  
- Tighten industrial emission regulations  
- Improve walking and cycling infrastructure  
- Run public awareness campaigns on air quality & health  

---

### 3. Ranking cities by AQI

**User:**  
> Show the top 5 cities by highest AQI.

**Bot (Data Agent):**  
Returns a ranked list of cities with the highest average AQI values, computed directly from the dataset (grouped by `City` and sorted by `AQI Value`).

---

## 🚀 How to Run (Colab)

1. **Open the notebook**: https://colab.research.google.com/drive/1rIa7WidUO7GEfuVjsH15q35AS2QClfPt?usp=sharing
