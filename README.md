# MyChatbot

A Flask chatbot powered by Google Gemini. It can read replies aloud and generate AI images and animated GIFs with Stable Diffusion.

**Live demo (demo reply mode):** https://mychatbot-web.vercel.app

## Features (Python app)
- Chat with Google Gemini (`gemini-1.5-flash`) through `POST /chat`
- **Listen:** text-to-speech of any bot reply with pyttsx3 (`POST /speak`, saves a WAV file)
- **Image:** generate an image from a prompt with Stable Diffusion v1.5 (`POST /generate_image`)
- **GIF:** generate an image and turn it into an 8-frame zoom-and-rotate animated GIF at 256, 512 or 768 px (`POST /generate_gif`)
- In-memory chat history and a dark, responsive chat UI

## Web version (`web/`)
A static page with the same UI. It has no server and no API key, so:
- Chat replies are **pre-written demo messages, clearly labelled, not AI output**
- **Listen** works for real, using the browser's Speech Synthesis API
- **GIF** applies the same `make_gif` effect to an image you upload, in the browser (gifenc)
- Stable Diffusion image generation is only available in the Python app

## Tech stack
Python, Flask, google-generativeai, pyttsx3, diffusers (Stable Diffusion), PyTorch, Pillow, HTML/CSS/JS.

## Run locally
```bash
pip install flask google-generativeai pyttsx3 diffusers transformers torch pillow
# Put your own Gemini API key in main.py (API_KEY), or better, load it from an environment variable
python main.py   # http://localhost:5000
```
The first image request downloads the Stable Diffusion weights, which are several GB.

---

Portfolio: [khuwaish-portfolio.vercel.app](https://khuwaish-portfolio.vercel.app) · Built by **Khuwaish Goyal**
