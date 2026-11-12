---
name: swarm-dashboard
description: Launches and manages the standalone Swarm Command Center on http://127.0.0.1:4820 for real-time visualization of agent swarms, roster, and message board.
---

# Swarm Dashboard

This skill launches and provides direct browser access to the full-size Swarm Command Center dashboard.

## Usage

When the user asks to open, view, or launch the Swarm dashboard:
1. Ensure the background dashboard server is running on port 4820:
   `node .agents/plugins/swarm-dashboard/sidecars/swarm_board/main.mjs`
2. Provide the direct browser URL with the current conversation ID:
   `http://127.0.0.1:4820/?conversationId=<CONVERSATION_ID>`

## Compatibility
Works cross-platform on macOS and Linux with zero external npm dependencies.
