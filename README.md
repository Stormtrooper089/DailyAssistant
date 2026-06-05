# Agentic Daily Assistant

Local prototype for:

- NSE portfolio and wishlist stock alerts.
- Daily assistant briefing from PA-added tasks, planned slots, and follow-ups.

## Run Locally

```bash
npm start
```

Open:

```text
http://localhost:4173/stock-alert-agent.html
```

## PA Task Intake

The Day Assistant tab includes a local PA task form. Your PA can add tasks, assign a slot, choose a priority, and leave context that appears in your daily report.

No external account credentials are needed.

## Deploy To Render

This repo includes `render.yaml`, so Render can create a Node web service from the repo.

Use these settings if configuring manually:

- Runtime: Node
- Build command: `npm install`
- Start command: `npm start`
- Health check path: `/health`

Render deploys from a linked Git provider and runs the service on the port provided by `PORT`.
