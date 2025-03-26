# 🚀 Project Name
Personalized Financial Recommendations Powered by AI

## 📌 Table of Contents
- [Introduction](#introduction)
- [Demo](#demo)
- [Inspiration](#inspiration)
- [What It Does](#what-it-does)
- [How We Built It](#how-we-built-it)
- [Challenges We Faced](#challenges-we-faced)
- [How to Run](#how-to-run)
- [Tech Stack](#tech-stack)
- [Team](#team)

---

## 🎯 Introduction
This project is a Flask-based intelligent recommendation system that leverages machine learning (ML), vector databases, and large language models (LLMs) to provide personalized financial recommendations. It predicts a customer's likelihood of applying for a home loan and generates tailored suggestions for home loans or investment products based on their financial profile and retrieved knowledge.

The purpose of this project is to address the lack of personalization in financial services by combining predictive analytics with context-aware recommendations. By integrating a Retrieval-Augmented Generation (RAG) pipeline, the system ensures that recommendations are both relevant and actionable.

## 🎥 Demo
🔗 [Live Demo](#) (if applicable)  
📹 [Video Demo](#) (if applicable)  
🖼️ Screenshots:

![Screenshot 1](link-to-image)

## 💡 Inspiration
   The inspiration for this project stems from the growing need for personalized financial services in the banking and financial sector. Customers today expect tailored recommendations that align with their unique financial profiles, goals, and circumstances. Traditional financial systems often rely on static rules or generic advice, which fails to address individual needs effectively.

   This project aims to bridge that gap by leveraging machine learning (ML), vector databases, and large language models (LLMs) to provide context-aware, personalized financial recommendations.

## ⚙️ What It Does
Key Features and Functionalities of the Project
   This project is a Flask-based REST API that predicts a customer's likelihood of applying for a home loan and generates personalized financial recommendations using a Retrieval-Augmented Generation (RAG) pipeline. Below are the key features and functionalities:

1. **Home Loan Prediction**
   Functionality:
   Predicts whether a customer is "Likely to apply" or "Unlikely to apply" for a home loan based on their profile data.
   How It Works:
   A pre-trained machine learning model (home_loan_model.pkl) is used for prediction.
   Customer data is preprocessed:
   Missing values are filled with default values.
   Categorical features are encoded using pre-trained label encoders.
   Numerical features are scaled using a pre-trained scaler.

2. **Retrieval-Augmented Generation** (RAG)
   Functionality:
   Retrieves relevant context from a vector database (Chroma) to enhance the recommendations generated by the LLM.
   How It Works:
   Based on the prediction:
   If "Likely to apply," the system queries the vector store for Home Lending Products.
   If "Unlikely to apply," the system queries the vector store for Investment Products.
   The retrieved documents are used as context for the LLM to generate more informed recommendations.

3. **Personalized Recommendations**
   Functionality:
   Generates tailored financial recommendations using a Large Language Model (LLM).
   How It Works:
   The LLM (e.g., Llama) is invoked with a detailed prompt containing:
   Customer profile data.
   Retrieved context from the vector database.
   Recommendations are:
   Home Loan Options (if "Likely to apply").
   Investment Product Options (if "Unlikely to apply").
   The recommendations are concise, relevant, and tailored to the customer's profile.

4. **REST API Endpoint**
   Endpoint: /api/predict_home_loan
   Method: POST
   Input:
   Customer profile data in JSON format, including fields like age, income, account balance, employment status, etc.
   Output:
   A JSON response containing:
   Home Loan Likelihood: "Likely to apply" or "Unlikely to apply."
   Recommendations: A list of 3 personalized financial product suggestions.

5. **Vector Database Integration**
   Functionality:
   Stores and retrieves document embeddings for context-aware recommendations.
   How It Works:
   Uses Chroma as the vector database.
   Embeddings are generated using Hugging Face's sentence-transformers/all-MiniLM-L6-v2 model.
   The similarity_search method retrieves the most relevant documents based on the query.

6. **Machine Learning Integration**
   Functionality:
   Uses a pre-trained machine learning model to predict home loan likelihood.
   How It Works:
   The model is loaded using joblib.
   Preprocessing steps include:
   Encoding categorical features.
   Scaling numerical features.
   The prediction output is used to determine the type of recommendations to generate.
   
7. **Large Language Model (LLM) Integration**
   Functionality:
   Generates human-like recommendations based on customer data and retrieved context.
   How It Works:
   The LLM (e.g., Llama) is initialized using LangChain's init_chat_model.
   A detailed prompt is constructed with customer data and retrieved context.
   The LLM generates recommendations in a structured format.
   
8. **Data Preprocessing**
   Functionality:
   Ensures customer data is clean and ready for prediction.
   How It Works:
   Missing values are replaced with default values.
   Categorical features are encoded using pre-trained label encoders.
   Numerical features are scaled using a pre-trained scaler.

10. **Environment Management**
   Functionality:
   Manages sensitive information like API keys using environment variables.
   How It Works:
   Uses dotenv to load environment variables from a .env file (e.g., Hugging Face API key).

12. **Debugging and Logging**
   Functionality:
   Provides detailed logs for debugging and monitoring.
   How It Works:
   Logs key steps, such as:
   Adding documents to the vector store.
   Retrieving context from the vector store.
   Generating recommendations using the LLM.

**Example Workflow**
   Input:
   A customer submits their profile (e.g., age, income, account balance) via the /api/predict_home_loan endpoint.
   Prediction:
   The ML model predicts whether the customer is "Likely to apply" or "Unlikely to apply" for a home loan.
   Context Retrieval:
   Relevant documents (e.g., home loan or investment products) are retrieved from the vector database.
   Recommendation Generation:
   The LLM generates 3 personalized recommendations based on the profile and retrieved context.
   Output:
   The API returns the prediction and recommendations in JSON format.

**Key Benefits**
   Combines machine learning, vector databases, and LLMs for intelligent, context-aware recommendations.
   Provides a scalable and modular architecture for financial recommendation systems.
   Ensures personalized and relevant suggestions for customers based on their profiles and retrieved knowledge.

## 🛠️ How We Built It
Brief Summary of the Program
This program is a Flask-based REST API that predicts a customer's likelihood of applying for a home loan and generates personalized recommendations using a Retrieval-Augmented Generation (RAG) pipeline. It combines traditional machine learning, vector databases, and large language models (LLMs) to deliver context-aware recommendations.

Key Functionalities
Home Loan Prediction:

A pre-trained machine learning model (home_loan_model.pkl) predicts whether a customer is "Likely to apply" or "Unlikely to apply" for a home loan based on their profile data.
The profile data is preprocessed using a scaler and label encoders.
Retrieval-Augmented Generation (RAG):

The program uses a Chroma vector database to retrieve relevant context (e.g., "Home Lending Products" or "Investment Products") based on the prediction.
The retrieved context is passed to an LLM (e.g., Llama) to generate personalized recommendations.
Personalized Recommendations:

If the customer is "Likely to apply," the LLM suggests 3 suitable home loan options.
If "Unlikely to apply," the LLM suggests 3 suitable investment product options.
The recommendations are concise and tailored to the customer's profile and retrieved context.
REST API Endpoint:

Endpoint: /api/predict_home_loan
Method: POST
Input: Customer profile data in JSON format.
Output: A JSON response containing:
Home loan likelihood prediction.
Recommendations generated by the LLM.

**Technologies and Tools Used**

Flask: For building the REST API.
Joblib: For loading the pre-trained ML model, scaler, and label encoders.
LangChain: For integrating the LLM and vector database.
Chroma: A vector database for storing and retrieving document embeddings.
Hugging Face: For generating embeddings using the sentence-transformers/all-MiniLM-L6-v2 model.
LLM (Llama): For generating personalized recommendations based on the customer profile and retrieved context.
NumPy and Pandas: For data preprocessing.
dotenv: For managing environment variables (e.g., API keys).

Workflow
Workflow: 
    A[User sends POST request to /api/predict_home_loan] --> B[Extract JSON data from request]
    B --> C[Predict home loan interest]
    C -->|Call predict_home_loan| D[Preprocess customer data]
    D -->|Scale and encode data| E[Run ML model prediction]
    E -->|Prediction result| F{Likely to apply?}
    F -->|Yes| G[Query vector store for "Home Lending Products"]
    F -->|No| H[Query vector store for "Investment Products"]
    G --> I[Retrieve relevant documents]
    H --> I[Retrieve relevant documents]
    I --> J[Generate LLM prompt with customer profile and context]
    J --> K[Invoke LLM model]
    K --> L[Parse LLM response into recommendations]
    L --> M[Return JSON response with likelihood and recommendations]

Explanation of the Workflow:
   **User Interaction**:
      The user sends a POST request to /api/predict_home_loan with customer data in JSON format.
   **Prediction**:
      The predict_home_loan function preprocesses the data (scaling, encoding) and uses a machine learning model to predict whether the customer is "Likely to apply" or "Unlikely        to apply" for a home loan.
   **Context Retrieval**:
      Based on the prediction, the system queries a vector store for relevant documents (either "Home Lending Products" or "Investment Products").
   **LLM Integration**:
      A prompt is generated with the customer profile and retrieved context, and an LLM is invoked to generate personalized recommendations.
   **Response:**
      The recommendations and prediction result are returned as a JSON response to the user.

Example Use Case
A customer submits their profile (e.g., age, income, account balance).
The API predicts they are "Likely to apply" for a home loan.
The system retrieves relevant home loan product details from the vector database.
The LLM suggests 3 suitable home loan options tailored to the customer's profile.

## 🚧 Challenges We Faced
Technical Challenges
Integration of Machine Learning and LLMs:

Challenge: Combining traditional machine learning (ML) models for prediction with large language models (LLMs) for generating recommendations required careful design.
Solution: Used a modular approach where the ML model predicts the likelihood, and the LLM generates recommendations based on the prediction and retrieved context.
Vector Database Integration (Chroma):

Challenge: Setting up and managing the Chroma vector database for storing and retrieving embeddings was complex, especially ensuring compatibility with Hugging Face embeddings.
Solution: Used LangChain's Chroma integration to simplify the process and ensure seamless retrieval of relevant documents.
Prompt Engineering for LLMs:

Challenge: Crafting effective prompts for the LLM to generate accurate and concise recommendations was iterative and time-consuming.
Solution: Designed structured prompts that included customer profiles, retrieved context, and clear instructions for the LLM.
Data Preprocessing:

Challenge: Handling missing or inconsistent customer data while ensuring compatibility with the pre-trained ML model.
Solution: Implemented default values for missing keys and used pre-trained label encoders and scalers to preprocess the data.
Performance Optimization:

Challenge: Ensuring the system responded quickly, especially when retrieving context from the vector database and invoking the LLM.
Solution: Limited the number of retrieved documents (k=1) and optimized the LLM invocation process to reduce latency.
Error Handling:

## 🏃 How to Run
1. Clone the repository  
   
   git clone https://github.com/ewfx/aidhp-craters-ai-innovators.git

   
2. Install dependencies  
   pip install flask joblib numpy pandas langchain langchain-community chromadb python-dotenv scikit-learn

   Need API Key or Access Token form groqcloud and huggingface.Create a .env file and save the following key.
   GROQ_API_KEY=<key>
   HF_TOKEN=<token>

4. Run the project  
   python3 rag_recomend_api.py

## 🏗️ Tech Stack
Backend Framework: Flask
Machine Learning: Pre-trained model (joblib), Scaler, Label Encoders
Vector Database: Chroma
Embeddings: Hugging Face Inference API
LLM: Llama (via LangChain)
Data Processing: NumPy, Pandas
Environment Management: dotenv
API Type: REST API

## 👥 Team
- Karthik Neela 
- Bipul Biswas
- 
