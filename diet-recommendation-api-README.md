# Diet Recommendation API

**Containerized backend pairing model predictions with GPT-driven, readable meal personalization.**

## Overview

A backend service that predicts suitable dietary recommendations using a trained scikit-learn model, then hands those raw predictions to GPT to turn them into clear, personalized, human-readable meal guidance. The split keeps the numeric prediction and the natural-language explanation as separate, independently improvable concerns.

## Tech Stack

- **FastAPI** — API layer and request handling
- **scikit-learn** — trained model for diet/nutrition predictions
- **OpenAI** — natural-language personalization of model output

## How It Works

1. A client submits user data (e.g. dietary preferences, health metrics, goals) to the API.
2. The scikit-learn model produces a structured recommendation (e.g. macro targets, food categories to favor/avoid).
3. The structured output is passed to an OpenAI model along with user context, which turns it into a personalized, readable explanation and meal suggestions.
4. The API returns both the structured prediction and the generated explanation.

## Getting Started

### Prerequisites

- Python 3.10+
- OpenAI API key
- Docker (optional, for containerized deployment)

### Environment

```bash
OPENAI_API_KEY=your_key_here
MODEL_PATH=models/diet_model.pkl
```

### Run locally

```bash
uvicorn app.main:app --reload
```

### Run with Docker

```bash
docker build -t diet-recommendation-api .
docker run -p 8000:8000 --env-file .env diet-recommendation-api
```

## API Reference

```
POST /recommend
```

Request body: user profile and dietary goals.
Response: structured model prediction + GPT-generated personalized explanation.

Interactive docs are available at `/docs` (Swagger UI, via FastAPI).

## License

MIT
