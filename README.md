# Credit Card Analysis with Azure AI
This repository presents a **proof of concept (PoC)** for automated analysis of **credit card documents** using **Azure AI Document Intelligence** and **Azure Storage Account**, with a web interface built in **Streamlit** and backend logic implemented in **Python**.

The project demonstrates how **cloud-based AI services** can be integrated to extract structured data from sensitive documents, supporting **data validation**, **information security**, and **fraud prevention** scenarios.

⚠️ This project is educational and experimental and is not intended for production use.

## How It Works
The application follows the workflow below:

1. The user uploads a credit card image through the Streamlit interface  
2. The file is uploaded to Azure Blob Storage  
3. The blob URL is sent to Azure AI Document Intelligence for analysis  
4. The `prebuilt-creditCard` model extracts structured information  
5. The extracted data is displayed in the interface for validation  

## Project Architecture

    credit-card-analysis-with-azure-ai/
    ├── app.py
    ├── services/
    │   ├── blob_service.py
    │   └── credit_card_service.py
    ├── utils/
    │   └── Config.py
    ├── requirements.txt
    └── .env

## File Responsibilities

### app.py
Streamlit web interface responsible for:
- File upload
- Triggering backend services
- Displaying analysis results

### services/blob_service.py
Handles integration with Azure Blob Storage, uploading files and returning their URLs.

### services/credit_card_service.py
Integrates with Azure AI Document Intelligence using the `prebuilt-creditCard` model to extract:
- Cardholder name  
- Card number  
- Expiration date  
- Issuing bank  

### utils/Config.py
Centralizes sensitive configuration values loaded from environment variables.

## Technologies Used
- Python  
- Streamlit  
- Azure AI Document Intelligence  
- Azure Storage Account (Blob Storage)  
- azure-ai-documentintelligence SDK  
- azure-storage-blob SDK  
- python-dotenv  

## Getting Started

### Prerequisites
- Python 3.8+
- An Azure account with:
  - Azure AI Document Intelligence enabled
  - Azure Storage Account with an existing container

### Installation

    git clone https://github.com/beandy-dev/credit-card-analysis-with-azure-ai.git
    cd credit-card-analysis-with-azure-ai

    python -m venv venv
    venv\Scripts\activate   # Windows

    pip install -r requirements.txt

### Environment Configuration
Create a `.env` file in the project root with the following variables:

    ENDPOINT=YOUR_AZURE_DOCUMENT_INTELLIGENCE_ENDPOINT
    SUBSCRIPTION_KEY=YOUR_SUBSCRIPTION_KEY
    AZURE_STORAGE_CONNECTION_STRING=YOUR_STORAGE_CONNECTION_STRING
    CONTAINER_NAME=YOUR_CONTAINER_NAME

⚠️ The Blob Storage container must exist and allow file access so that Document Intelligence can retrieve the document via URL.

### Running the Application

    streamlit run app.py

The application will open in the browser and allow image uploads (`.png`, `.jpg`, `.jpeg`).

## Objectives and Learning Outcomes
- Test automated analysis of credit card documents  
- Explore integration between cognitive AI services and Python applications  
- Apply cloud computing concepts in a real-world-like scenario  
- Build a functional proof of concept for sensitive document processing  
- Gain practical experience with Azure AI Document Intelligence  
- Integrate Azure Blob Storage in a Python application  
- Develop interactive web interfaces using Streamlit  
- Structure Python projects with clear separation of concerns  
- Understand common challenges in cloud-based AI solutions  

## Limitations
- Validation logic is simplified and based on the presence of extracted fields  
- The `prebuilt-creditCard` model may not be available in all Azure regions  
- No PCI compliance or data masking is implemented  
- Intended for learning and experimentation only  

---

⚠️ No real credit card data is stored in this repository.  
All documents used are examples or anonymized data, strictly for educational purposes.
