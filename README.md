# Assignment 2 — LangFlow Smart Bot

A general-purpose AI chatbot built visually in **Langflow**, using a prompt template, a language-model-powered Agent, a Tavily Search API tool, and a chat input/output interface.

## Project Overview

This project demonstrates how to connect a chat interface to an AI Agent and give the agent access to web search. The prompt template provides the agent with general-purpose instructions, while Tavily Search can retrieve online information when the agent chooses to use its configured tool.

The screenshots show a sample conversation asking about Lionel Messi and a second question about recently released movies.

## Workflow Components

| Component | Purpose |
|---|---|
| Chat Input | Receives the user's message |
| Prompt Template | Supplies general-purpose instructions to the agent |
| Agent | Uses the selected language model and connected tools to respond |
| Language Model (`llama3.2:3b`) | Generates the agent's responses |
| Tavily Search API | Provides the `FETCH_CONTENT_DATAFRAME` search action for web retrieval |
| Chat Output | Displays the response to the user |

## Workflow Architecture

```text
                         Prompt Template
                                |
                                v
Chat Input ---------------> Agent ----------------> Chat Output
                                ^
                                |
                         Tavily Search API
                         (tool connection)
```

## How It Works

1. The user submits a question through the chat interface.
2. The Prompt Template provides instructions for a general-purpose assistant.
3. The Agent receives the prompt and user input.
4. The agent uses the configured `llama3.2:3b` language model to formulate an answer.
5. When useful and supported by its instructions, the agent can call the Tavily Search API tool to retrieve web content.
6. The final response is shown in Chat Output.

Tool use depends on the agent's instructions and the user's query. Do not assume every response used web search; check the execution trace to verify tool calls.

## Technologies Used

- **Langflow** — visual low-code workflow builder
- **Ollama / `llama3.2:3b`** — local language model shown in the Agent component
- **Tavily Search API** — web search tool
- **Prompt Template** — prompt and instruction management
- **Chat Input / Chat Output** — conversational interface

## Example Tests

- `Who is Lionel Messi?`
- `What are some recently released movies?`

The included screenshots show example answers for these queries. For time-sensitive questions such as recent movie releases, verify the results against current sources.

## Repository Structure

```text
Assignment-2-LangFlow-Smart-Bot/
├── README.md
├── .gitignore
├── flow/
│   └── (add the exported Langflow flow JSON here)
└── screenshots/
    ├── chat-demo.png
    └── workflow-editor.png
```

## Setup and Usage

1. Open your Langflow instance.
2. Export/download the flow in JSON format and add it to the `flow/` directory.
3. Import the flow into your own Langflow instance if needed.
4. Configure the Ollama model (`llama3.2:3b`) and ensure Ollama is running locally.
5. Configure your own Tavily API key in the Tavily Search API component.
6. Open the Playground and test the sample questions.

Exact import/export options may vary by Langflow version. Configure credentials in your own instance; do not publish API keys.

## Screenshots

- `screenshots/workflow-editor.png` — Langflow visual workflow.
- `screenshots/chat-demo.png` — example chat session and responses.

## Security

Do not commit API keys, access tokens, credential exports, or private information. The screenshot contains a masked Tavily API key; ensure no unmasked key is included in any exported flow or repository file.

## Limitations

This starter repository is based on the provided screenshots. The actual Langflow flow export has not yet been included. Add the exported JSON file to make the project easier to import and reproduce.
