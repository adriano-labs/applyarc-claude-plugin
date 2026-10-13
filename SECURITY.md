# Security policy

## What this repository contains

This repository holds only the ApplyArc plugin for Claude: skill and command instructions in Markdown, plugin metadata in JSON, and an icon. It contains no server code, no secrets and no user data.

The plugin connects to the ApplyArc MCP server at `https://claude-mcp.applyarc.com/mcp`. Account tools require the user to sign in with their own ApplyArc login through OAuth 2.0 with PKCE. Each request is checked on the ApplyArc servers, so a copy or fork of this repository cannot read anyone's data.

## Reporting a vulnerability

Please do not open a public issue. Use GitHub's private vulnerability reporting on this repository, or email security@applyarc.com.

We aim to acknowledge reports within 3 working days.
