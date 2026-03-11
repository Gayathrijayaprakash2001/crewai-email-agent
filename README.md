# CrewAI Email Assistant Agent

This project is a small **Agentic AI application** built using **CrewAI** and a **Groq large language model (LLM)**.  
The purpose of the project is to take a **rough, informal email** and automatically convert it into a **clear, professional, and well-structured email**.

In many teams, emails are often written quickly and may contain internal abbreviations, jargon, or informal language. While these may be understandable within the team, they can be confusing to others. This project explores how an **AI agent** can improve such emails by detecting jargon and rewriting the message in a professional tone.

The system is intentionally simple because the goal of the project is to **learn how AI agents work**, how they can use tools, and how frameworks like **CrewAI** coordinate the workflow.

---

# Idea Behind the Project

The main idea behind this project is to simulate a **communication assistant**.

Imagine you quickly write an email like this:


looping in Priya. TAS and PRX updates are in the deck.
ETA for SDS integration is Friday.
Let's sync tomorrow if SYNCBOT allows.
ping me if any blockers.


This message contains several problems:

- It is written informally  
- It contains internal abbreviations (**TAS, PRX, SDS**)  
- It uses casual language such as **"ping me"**  
- It lacks proper structure  

The goal of the AI agent is to **read this email, understand the context, expand abbreviations, and rewrite it as a professional email**.

---

# How the System Works

The system consists of **four main components** that work together.

---

## The Language Model (LLM)

The language model acts as the **core intelligence of the system**.  
In this project, the model is accessed through **Groq**, using the model:


llama-3.1-8b-instant


This model is responsible for **understanding the email and generating the improved version**.

---

## The Custom Tool

To help the agent understand internal terms, the project includes a **custom tool that detects jargon**.

Many organizations use abbreviations or internal terminology that are not obvious to outsiders. The tool checks the email for such terms and suggests clearer replacements.

For example:

| Jargon | Meaning |
|------|------|
| PRX | Project Phoenix |
| TAS | Technical Architecture Stack |
| SDS | Smart Data Syncer |
| SYNCBOT | Internal stand-up assistant bot |
| ping | reach out or contact |

The tool does **not rewrite the email itself**.  
Instead, it provides **suggestions that the AI agent can use while rewriting the message**.

---

## The AI Agent

The AI agent is configured to act like a **professional communication assistant**.

Its role is to:

- Read the rough email  
- Understand the meaning and context  
- Use the jargon detection tool if necessary  
- Rewrite the email in a professional tone  

Because the agent has access to tools, it can **augment the language model with additional capabilities**.  
This is an important concept in **Agentic AI systems**.

---

## The Task

In **CrewAI**, agents perform **tasks**.

The task in this project instructs the agent to:

- take the rough email  
- expand abbreviations  
- rewrite the message clearly  
- produce a professional email  

This task definition guides how the agent behaves.

---

## The Crew

CrewAI uses the concept of a **crew** to coordinate agents and tasks.

In this project the crew is simple, consisting of:

- **one agent**
- **one task**

When the crew starts running, the agent reads the instructions and completes the task using the language model and the tool.

---

# Workflow of the Application

The process of the application can be visualized as follows:


Rough Email
↓
Email Assistant Agent
↓
Jargon Detection Tool
↓
Language Model (Groq)
↓
Professional Email Output


The agent analyzes the email, optionally calls the tool to understand abbreviations, and then generates a **polished email**.

---

# Example Output

For the rough email shown earlier, the agent may produce something like this:


Hi Priya,

I'm including you in this thread regarding the latest updates on the
Technical Architecture Stack and Project Phoenix, which are included
in the presentation deck.

The estimated timeline for the Smart Data Syncer integration is Friday.
We can connect tomorrow if the internal stand-up assistant bot allows.

Please feel free to reach out if you encounter any issues.

Best regards


The rewritten email is:

- more structured  
- easier to understand  
- free of unexplained jargon  

---

# Technologies Used

This project was built using the following technologies:

- Python  
- CrewAI (agent framework)  
- Groq LLM API  
- python-dotenv (for environment variables)

---

# Project Structure

The repository is organized in a simple way:


crewai-email-agent
│
├── main.py
├── README.md
├── pyproject.toml
├── uv.lock
└── .env


The main logic of the application is contained in **main.py**, where the **agent, t