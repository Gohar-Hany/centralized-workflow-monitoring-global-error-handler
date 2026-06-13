# Centralized Workflow Monitoring & Global Error Handler (n8n & MongoDB)

This repository contains the n8n workflow definition for a **Centralized Monitoring and Global Error Handler**. It captures workflow exceptions globally, logs diagnostic data to Google Sheets, alerts administrators via Telegram, and retrieves/formats MongoDB chat history.

## Key Technical Features
* **System-wide Error Catching:** Triggered globally by `ErrorTrigger` when any webhook or API node fails in the workspace.
* **Cairo Timezone Formatter:** Custom JS normalizes timestamps to Africa/Cairo timezone and extracts stack traces, execution IDs, and direct URLs.
* **Google Sheets Error Logs:** Appends clean failure logs to a centralized Google Sheets logger.
* **Telegram Admin Alerts:** Sends markdown alert messages containing direct execution URLs to R&D Telegram channels.
* **MongoDB NoSQL Integration:** Queries MongoDB collections (`n8n_chat_histories`) by `sessionId`.
* **Array Mapping:** Custom JS Code formats raw chat entries into standardized OpenAI `user`/`assistant` role JSON arrays.

## Workflows Included
1. `centralized-workflow-monitoring-global-error-handler.json` (Error monitor and chat logger)

## Deployment Instructions
1. Import `centralized-workflow-monitoring-global-error-handler.json` into n8n.
2. Set this workflow as the global Error Handler inside your n8n settings.
3. Configure credentials for Google Sheets, MongoDB, and Telegram API.
