# 🤖 My First AI Agent with n8n

This project contains my **first AI Agent workflow** built using [n8n](https://n8n.io/) and **LangChain integration**. It uses **Google Gemini** as the chat model and includes memory to maintain conversational context.  

## 🚀 Features  
- **Trigger**: Listens for incoming chat messages  
- **AI Agent**: Powered by LangChain’s Agent node  
- **Model**: Uses **Google Gemini (PaLM)** for natural language processing  
- **Memory**: Implements buffer memory to keep track of conversations  

## 🛠 Workflow Overview  

The workflow consists of four main nodes:  

1. **When chat message received** – Triggers whenever a chat message is received  
2. **AI Agent** – The main logic engine that connects model + memory  
3. **Google Gemini Chat Model** – Provides powerful conversational AI  
4. **Simple Memory** – Stores short-term conversation history  

## 📂 Repository Structure  
```
├── First Agent.json   # Exported n8n workflow
├── README.md          # Documentation
```

## 🔧 Setup Instructions  

1. Clone this repository:  
   ```bash
   git clone https://github.com/your-username/first-n8n-agent.git
   cd first-n8n-agent
   ```
2. Import the workflow (`First Agent.json`) into your **n8n** instance.  
3. Configure your **Google Gemini (PaLM) API credentials** inside n8n.  
4. Activate the workflow and start chatting with your AI Agent! 🎉  

## 📸 Workflow Preview  
![Workflow Screenshot](./workflow.png)

## 🙌 Acknowledgments  
Special thanks to:  
- [n8n](https://n8n.io/) for the no-code/low-code automation platform  
- [LangChain](https://www.langchain.com/) for the agent and memory components  
- **Google Gemini API** for powering the language model  

## Architecture Diagram
```
    A[Chat Message Trigger] --> B[AI Agent]
    B --> C[Google Gemini Chat Model]
    B --> D[Simple Memory]
```

## Chat in Action
![Workflow Screenshot](./demo%20chat.png)