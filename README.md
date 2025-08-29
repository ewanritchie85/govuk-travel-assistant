
# Travel Assist AI App


An AI-powered travel assistant platform for embassy and travel queries.

- **Copilot Studio Agent** provides the chat interface and orchestrates calls to Azure Logic Apps.
- **Azure Logic Apps** automate retrieval and orchestration of embassy and travel information.
- **Foundry Chat Completion** is used within the workflow to summarise information from the GOV.UK website.

## Project Structure
- `/embassy-logic-app/` — Azure Logic App for embassy info retrieval and summarisation
- `/travel-logic-app/` — Azure Logic App for travel-related workflows
- `/foundry-chat/` — Foundry chat completion integration and utilities
- `/copilot-agent/` — Copilot Studio agent logic and configuration
- `/config/` — Shared configuration files and secrets

## Getting Started
1. Clone the repository
2. Set up environment variables in `/config/` and update parameters in each Logic App folder
3. Deploy Logic Apps using the provided JSON and parameter files
4. Follow integration guides in each folder

## Features
- Automated retrieval and summarisation of British embassy information from GOV.UK
- Travel workflow orchestration using Azure Logic Apps
- Advanced conversational AI via Foundry Chat Completion
- Modular agent logic for extensibility

## Next Steps
- Implement and connect each integration in its respective folder
- Add documentation and usage examples
- Ensure secrets are managed securely and not committed to git history
