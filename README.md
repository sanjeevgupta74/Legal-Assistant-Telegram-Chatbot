# Legal Assistant Automation Suite

An integrated AI-powered legal assistant built using n8n, LangChain, OpenAI, and Pinecone.  
This system automates document processing, vector storage, and conversational legal assistance through Telegram.

---

## Overview

This repository contains two interconnected workflows:

### 1. Vector Legal Assistant
Automates the ingestion, processing, and embedding of legal documents into a vector database for retrieval-based AI applications.

**Key Features**
- Google Drive folder trigger for new legal files  
- Downloads and processes PDFs automatically  
- Generates document embeddings using OpenAI embeddings (1536 dimensions)  
- Uploads vector data to Pinecone for semantic search  
- Uses recursive text splitting for optimized chunking  
- Automated synchronization every hour

### 2. Legal Assist Telegram Bot
Provides a live chat interface over Telegram where users can ask legal questions, restricted to stored context.

**Key Features**
- Telegram trigger for real-time chat handling  
- GPT-4.1-mini model integration via LangChain  
- Context-limited responses: replies only using stored legal data  
- Pinecone-powered memory and recall  
- Conversation tracking via n8n memory buffer  
- Custom system prompt enforcing legal domain constraints  

---

## Architecture

[Google Drive] → [n8n Workflow] → [OpenAI Embeddings] → [Pinecone Vector Store]
[TG User] → [Telegram Bot] → [LangChain Agent] → [Pinecone Search & Reply]

<img width="972" height="614" alt="image" src="https://github.com/user-attachments/assets/24efea9c-1432-4c4d-b859-56c39f78aedf" />


<img width="853" height="536" alt="image" src="https://github.com/user-attachments/assets/450210ac-a66c-476f-9191-d8f4ac5ac072" />

---

## Dependencies

- n8n (≥ v1.2)
- LangChain (≥ v0.2)
- Pinecone Vector Database
- OpenAI API (GPT-4, Embeddings)
- Telegram Bot API
- Google Drive API credentials

---
## Installation

1. **Clone this repository**

2. **Import Workflows into n8n**
- Upload `Vector-Legal-Assistant.json`
- Upload `Legal-Assist-Telegram.json`

3. **Connect Credentials**
- Google Drive OAuth2
- OpenAI API Key
- Pinecone API Key
- Telegram Bot Token

4. **Activate the Workflows**
- Ensure both are active and linked under the same owner context in n8n.

---

## Usage

1. Add legal documents to the designated Google Drive folder.  
2. The Vector Assistant ingests and vectors documents automatically.  
3. Interact with the Telegram Bot to query the database:
- The bot will only respond using the stored legal data.
- If information is not found, it will politely decline the query.

---

## Example Prompts

- “What are the requirements for contract termination?”
- “Summarize the contents of the latest policy document.”
- “Can you provide the legal definition of due diligence?”

---

## Security Considerations

- Responses restricted to vector context ensure legal compliance.
- No external data leakage beyond configured sources.
- All credentials stored securely through n8n credential management.

---

## Future Enhancements

- Add support for multiple law firm-specific knowledge bases.
- Expand language model context window for lengthy document summaries.
- Integrate Google Sheets automation for case tracking.

---

## Authors

**Maintainer:** The Innovative Technology Solutions and Consultancy Services   
**Contact:** sanjeev_gupta74@yahoo.com
**Version:** 1.0.0  
**Last Updated:** October 2025
