# 🧠 Day 2 Summary — Agent Tools & Interoperability with MCP

## Overview
Day 2 covers how AI agents use external tools to access real-world data or perform actions, and introduces the Model Context Protocol (MCP) — a universal standard for connecting agents and tools.

## Key Learnings
- Tools let agents **know something** (retrieve data) or **do something** (take actions).
- Types: Function Tools, Built-in Tools, Agent Tools.
- Best practices: clear names, short parameters, granular design, validation, and concise output.

## What is MCP?
MCP (Model Context Protocol) is an open standard that allows AI agents and tools to communicate seamlessly, solving the “N × M” integration problem.

### MCP Architecture
- **Host:** manages tools and user experience.  
- **Client:** sends and receives messages.  
- **Server:** provides tools/data.  
- Communication via **JSON-RPC** using stdio or HTTP.

## Security Risks
- Dynamic tool injection  
- Tool shadowing  
- Sensitive data leaks  
- Confused deputy problem  
**Mitigation:** Allowlisting, validation, human-in-loop approvals.

## Tasks
1. Listen to the podcast.
2. Read the whitepaper.
3. Complete Kaggle codelabs (tool creation + MCP implementation).
4. Verify your Kaggle account.
5. Optional: Add whitepaper to NotebookLM.

## Glossary
- **Interoperability:** Ability of systems to work together smoothly.
- **MCP:** Protocol for connecting AI agents with tools in a standardized, secure way.

## Conclusion
MCP enables agents to extend their power with tools but requires strict governance and security layers for enterprise safety.
