# Image to 3D Generator

[![Open in Streamlit](https://static.streamlit.io/badges/streamlit_badge_black_white.svg)](https://gituserc1140-rk3dpsv2-streamlit-app-main.streamlit.app)

Streamlit app for turning text prompts into images and then converting those images into 3D models.

## Features

- Image generation with OpenAI
- 3D model generation with Stability AI
- Interactive GLB viewer in the browser
- Interactive AI workflow agent (Cohere-powered) with explicit modes for idea generation, prompt refinement, troubleshooting, and conversion guidance
- Shared in-app agent context (image mode, model mode, latest prompt, generated assets, and conversion state) for grounded responses
- One-click agent actions to apply suggestions to image prompts, prompt ideas, blog topics, and social captions
- Cohere-powered blog writer tab for generating Markdown blog drafts from a question/topic
- Cohere-powered prompt examples tab for generating reusable prompt ideas from a topic
- MoviePy video editor tab for trimming, changing playback speed, fading, and applying simple effects before sharing
- Social Share tab for preparing generated images or 3D preview snapshots for TikTok-style posting
- PWA metadata and service worker support

## Run locally

Install dependencies:

```bash
pip install -r requirements.txt
```

**Important:** Never commit API keys to version control. Image and 3D model generation keys are entered through password fields in the app for the active browser session and are not read from backend configuration. **Do not commit API keys or a `.env` file.**

Example `.env` file (required only for the Cohere AI agent/chat, blog writer, and prompt ideas):

```bash
COHERE_API_KEY=your_cohere_key
```

Start the app:

```bash
streamlit run streamlit_app.py
```

## Troubleshooting OpenAI Image Generation

- If you see an OpenAI error like `billing_hard_limit_reached`, the active key/project has no remaining billing capacity.
- Rotate to a funded key and update `OPENAI_API_KEY` in your local `.env` (or Streamlit secrets).
- The app re-reads `.env` during key lookup, so key rotation is picked up on the next request.

## Streamlit Cloud

Use `streamlit_app.py` as the app entry point. Demo users supply their own OpenAI or Stability AI credentials in the generation tabs; configure only `COHERE_API_KEY` in Streamlit secrets or environment variables when enabling Cohere features. The repo is structured so it can be connected directly to Streamlit Cloud.

MoviePy processing is local to the Streamlit instance and runs only after an edit is
requested. Video editing uses CPU and temporary disk space, so large or long videos
may be slower or exceed the memory/storage limits of Streamlit Community Cloud.