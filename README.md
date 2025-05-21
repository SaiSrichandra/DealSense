# DealSense -- AI Deal Hunter

An autonomous, multi-agent AI system that scans online deals, estimates
true product value using an ensemble of pricing models, and notifies you
when a deal is genuinely underpriced.

## Overview

**DealSense** continuously: 1. Scans deal RSS feeds 2. Selects
clean, well-structured deals using an LLM 3. Estimates the true market
price using multiple AI models 4. Calculates potential savings 5. Sends
push notifications when a deal exceeds a savings threshold 6. Visualizes
product embeddings in 3D

## Key Features

-   Multi-agent architecture
-   Ensemble price estimation (Fine tuned LLM + retrieval + neural network)
-   Persistent vector database (ChromaDB)
-   Interactive Gradio dashboard
-   Push notifications via Pushover
-   3D embedding visualization (t-SNE)

## Architecture

RSS Feeds → ScannerAgent → Preprocessor → EnsembleAgent\
(Frontier LLM + Specialist LLM + Neural Network) → Opportunity Scoring →
Notifications → UI

## Project Structure

dealsense.py --- Gradio UI (main entrypoint)\
deal_agent_framework.py --- Orchestration and persistence\
pricer.py --- Modal GPU service for fine-tuned pricer\
log_utils.py --- ANSI to HTML log formatting\
memory.json --- Persistent opportunity memory\
products_vectorstore/ --- ChromaDB persistent store
agents/ --- All agent implementations

## Running the Project

### Requirements

-   Python 3.10+
-   OpenAI-compatible API key
-   Modal account
-   (Optional) Pushover account

### Environment Variables

OPENAI_API_KEY\
PUSHOVER_USER\
PUSHOVER_TOKEN\
PRICER_PREPROCESSOR_MODEL (optional)

### Launch

python dealsense.py

## Modal Deployment

Deploy the specialist pricer:

modal deploy pricer.py

## Persistence

-   memory.json stores past opportunities
-   ChromaDB persists embeddings across runs
