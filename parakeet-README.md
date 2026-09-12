# Parakeet — AI Interview Copilot

**Real-time voice transcription with live answer suggestions during an actual conversation — not batch Q&A.**

## Overview

Parakeet listens to a live interview conversation, transcribes it in real time, and surfaces answer suggestions to the candidate as the conversation unfolds. Unlike tools that transcribe an interview and generate feedback afterward, Parakeet is built for the moment itself: low-latency transcription feeding directly into contextual suggestion generation while the conversation is still happening.

## Tech Stack

- **Deepgram** — real-time speech-to-text transcription
- **OpenAI GPT-4o** — contextual answer suggestion generation

## How It Works

1. Audio from the ongoing conversation is streamed to Deepgram for real-time transcription.
2. As transcript segments arrive, they're passed to GPT-4o along with conversation context.
3. GPT-4o generates concise, relevant answer suggestions.
4. Suggestions are surfaced to the candidate live, with minimal delay between question and suggestion.

The core engineering challenge is latency: keeping the transcription → suggestion → display pipeline fast enough that suggestions are useful in the moment, not after the question has already been answered.

## Getting Started

### Prerequisites

- Deepgram API key
- OpenAI API key (GPT-4o access)
- Node.js (or your chosen runtime)


Configure environment variables:

```bash
DEEPGRAM_API_KEY=your_key_here
OPENAI_API_KEY=your_key_here
```

### Run

```bash
npm run dev
```

## Roadmap

- Support for additional STT providers
- Tunable suggestion latency/quality tradeoff
- Session history and post-interview review

## License

MIT
