# Customer Support Workflow (n8n)

This workflow automates the process of handling customer support emails using AI-powered tools within the n8n platform.

## 🚀 Overview

This n8n workflow:
1. Triggers on incoming Gmail emails.
2. Classifies emails as **Customer Support** or **Other**.
3. If it's a customer support request:
   - Uses GPT-4o-mini to generate friendly, helpful replies.
   - Retrieves relevant FAQ info from a Pinecone vector database.
   - Sends a response email automatically via Gmail.

---

## 📦 Nodes Breakdown

### 1. **Gmail Trigger**
- Monitors the Gmail inbox for new messages (polling every minute).

### 2. **Text Classifier**
- Categorizes emails using a language model into:
  - Customer support
  - Other

### 3. **AI Agent (Langchain + OpenAI)**
- Responds to customer inquiries using:
  - System prompt defining tone and instructions.
  - Pinecone Vector Store for FAQ context.
  - GPT-4o-mini model.

### 4. **Pinecone Vector Store**
- Retrieves FAQ-related content via semantic search to support the AI agent’s response.

### 5. **OpenAI Embeddings**
- Converts FAQ text into vector form for Pinecone indexing and search.

### 6. **Gmail Reply**
- Sends the AI-generated response back to the customer.

---

## 🔐 Credentials Setup

### 🧠 OpenAI
1. Go to [OpenAI API dashboard](https://platform.openai.com/account/api-keys).
2. Copy your API key.
3. In n8n:
   - Go to **Credentials** > **Create New** > **OpenAI API**.
   - Paste the API key and name it (e.g., `n8n free OpenAI API credits`).

### 📧 Gmail
1. Go to **Credentials** > **Create New** > **Gmail OAuth2 API**.
2. Authorize your Gmail account.
3. Save it with a recognizable name.

> Make sure to enable Gmail API in your Google Cloud Console and set correct redirect URI to your n8n instance.

### 📚 Pinecone
1. Log into [Pinecone Console](https://app.pinecone.io/).
2. Create an Index (e.g., `demon8nrag`) with namespace `FAQ`.
3. Copy your **API Key** and **Environment**.
4. In n8n:
   - Go to **Credentials** > **Create New** > **Pinecone API**.
   - Paste the API key and environment.
   - Name the credential (e.g., `MyAccount n8nrag`).

---

## 🧠 AI Prompt Instructions

The AI is prompted as:
> “You are a customer support agent for Tech Haven. Your job is to respond to incoming emails with relevant information using your knowledge and tools. Use a friendly tone, include emojis, and sign off as 'Mr. Helpful from Tech Haven Solutions'.”

---

## ✅ Usage

1. Add your FAQ content to Pinecone using the Embeddings node.
2. Turn on the workflow.
3. Let the system handle support emails automatically!

---

🛠 Created with ❤️ using n8n, OpenAI, and Pinecone.
