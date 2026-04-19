# SUPAA Backend System Architecture

## Overview
This repository contains the backend orchestration layer and API Gateway for the SUPAA multi-agent platform, focusing heavily on our MVP: the English-Japanese AI Tutor.

## Core Components
1. **FastAPI Backend (`api/`)**: The core application server built with Python and FastAPI. It orchestrates agent interactions, handles database models (via SQLAlchemy), and serves public and internal endpoints.
2. **PostgreSQL + pgvector**: Primary relational database handling user states, chats, and vector embeddings for semantic retrieval.
3. **Redis**: Manages sessions, ephemeral task states, and WebSocket connection state tracking.
4. **Cloud Run**: The serverless execution environment handling backend autoscaling and deployment.

## Data Flow
1. **Client Request**: The frontend or an agent makes a REST/WebSocket call to the FastAPI Gateway.
2. **State Management**: The API validates the session via Redis and retrieves the context from PostgreSQL.
3. **Model Inference**: If an LLM response is needed, the backend communicates with the `gemma4-4b` or `gemma4-coding` service via HTTP streams.
4. **Tool Execution (Paperclip)**: Specialized agents execute tasks through the Paperclip adapter layer, and the backend captures these state changes, streaming the "Internal Monologue" back to the user via WebSocket.

## Inter-Service Communication
The backend communicates directly with specialized model deployments (vLLM on Cloud Run) and handles rate limiting, authentication, and structured output parsing.

## Design Patterns
- **Dependency Injection**: Extensively used across FastAPI routers to manage database sessions and service layers.
- **Asynchronous I/O**: `asyncio` and asynchronous database drivers (`asyncpg`) are mandatory for all I/O bound operations to ensure high throughput.
