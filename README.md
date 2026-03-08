# as-bump-maker

## Demo
![Demo](https://raw.githubusercontent.com/Matthunker/as-bump-maker/main/assets/demo.gif)

Full video (with sound): https://github.com/Matthunker/as-bump-maker/blob/main/assets/demo.mp4


A lightweight web app for creating **Adult Swim–style bumps** and exporting them as **MP4** in the browser.

Use it to generate custom filler/commercial clips you can add to **Jellyfin** libraries or schedule via **Tunarr**.

## Features
- Text card timeline (text + duration)
- Per-card text placement (presets + drag-to-place)
- Optional background image/video (cover/contain + dim)
- Optional music upload (muxed into export)
- Runs as a simple Nginx container

## Quick start (Docker)
Run:

    docker run --rm -p 5173:80 matthuey/as-bump-maker:latest

Open:

    http://localhost:5173

## Docker Compose
Create `docker-compose.yml`:

    services:
      bump-maker:
        image: matthuey/as-bump-maker:latest
        ports:
          - "5173:80"
        restart: unless-stopped

Then run:

    docker compose up -d

## How to use
1. Add cards (set text + seconds)
2. Optional: upload music
3. Optional: upload a background image/video + dim it
4. Preview
5. Export MP4

## Notes
- MP4 export is done in-browser (MediaRecorder when supported; otherwise WebM → MP4 via ffmpeg.wasm).
- First export may download browser-side encoder assets depending on your setup.
