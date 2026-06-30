# ✨ Sparkle Cinematic Story

A single-page, no-backend web app for creating cinematic, scroll-driven love stories and "Will You...?" proposal pages. Build a personalized timeline of memories, pick a color theme and background music, then generate a single shareable link or QR code — no server, no database, no sign-up.

## Overview

Sparkle Cinematic Story lets you turn a relationship's milestones into a beautifully animated, story-like web experience. Visitors scroll through a cinematic timeline of dates, captions, photos, and videos, then arrive at a customizable proposal/question screen with a celebration animation on acceptance.

Everything needed to render the story — text, theme, and even compressed images — is encoded directly into the generated URL (or stored locally in the browser), so there is no server-side component required to host or share a story.

## Features

- **Cinematic scroll timeline** — Alternating left/right story cards with date labels, captions, and media, animated in as the user scrolls.
- **Rich media support** — Use photos, MP4/video files, or embedded YouTube videos for each timeline step and for the final success screen.
- **Built-in image compression** — Uploaded photos are automatically resized and compressed client-side (canvas-based JPEG compression) so they can be safely embedded in a URL.
- **Background music** — Add a YouTube track as ambient background audio, with a floating mute/unmute control and an "unlock autoplay" start overlay.
- **6 built-in color themes** — Navy, Rose, Ocean, Forest, Midnight, and Sunset, plus a **custom theme** generator from any picked color.
- **Interactive proposal flow** — A "No" button that playfully runs away from the cursor/touch, a "Yes" button that triggers a full-screen confetti/particle celebration.
- **Magic Link generation** — Encodes the entire story configuration into a single shareable URL (Base64 + URI-encoded JSON), with automatic QR code generation for easy sharing.
- **Creator Dashboard** — A local history of every story you've created on this device, with quick copy/share/delete actions.
- **Privacy-first by design** — No images or text are ever uploaded to a server. All data lives inside the generated link or in the browser's `localStorage` on your own device.
- **Terms & Privacy modal** — A built-in, user-facing explanation of how data is (and isn't) stored, including a "Wipe All Data" control.
- **Fully responsive** — Optimized layouts for mobile, tablet, and desktop.

## How It Works

1. **Create** — Open `index.html` in a browser. Fill in the creator form: title, theme, background music (optional), timeline steps (date, caption, photo/video/YouTube), and the proposal question/success screen.
2. **Generate** — Click **"Generate Magic Link & QR Code"**. The app compresses any uploaded images, serializes the whole configuration to JSON, and encodes it into the page's own URL as a `?data=` query parameter.
3. **Share** — Send the generated link (or its QR code) to the recipient. Opening the link loads the app directly in *viewer mode*, decodes the embedded data, and renders the cinematic story — no server lookup required.
4. **Revisit** — Every story you generate is also saved to your local **Dashboard** (via `localStorage`) so you can find, re-copy, or delete it later from the same browser/device.

## Tech Stack

- **HTML5** — single self-contained file
- **[Tailwind CSS](https://tailwindcss.com/)** (via CDN) with a custom CSS-variable-driven theme system
- **Vanilla JavaScript** — no build step, no framework, no bundler
- **Google Fonts** — Playfair Display, Dancing Script, Montserrat
- **YouTube IFrame API** — for embedded videos and background music playback
- **[QR Server API](https://goqr.me/api/)** — for on-the-fly QR code generation of magic links
- Browser **Canvas API** for client-side image compression
- Browser **`localStorage`** for the creator dashboard/history

No backend, database, or build tools are required.

## Project Structure

```
Sparkle_cinematic_Story-main/
├── index.html          # The entire application (markup, styles, and logic)
└── img/
    ├── Sparkle_Cinematic_Story_Logo.png
    ├── Sparkle_Cinematic_Story_Logo (1).png   # used as the favicon
    └── form logo.png
```

## Getting Started

Because the app is a single static HTML file, no installation or build process is needed.

### Option 1 — Open directly
Double-click `index.html` or open it in your browser:
```
file:///path/to/Sparkle_cinematic_Story-main/index.html
```

### Option 2 — Serve locally (recommended for full functionality)
Some browsers restrict certain features (like file inputs or clipboard access) on the `file://` protocol. Serving it locally avoids this:
```bash
# Using Python
python3 -m http.server 8000

# Using Node.js
npx serve .
```
Then visit `http://localhost:8000` in your browser.

### Option 3 — Deploy as a static site
Since there's no backend, the app can be hosted on any static file host, such as GitHub Pages, Netlify, Vercel, or Cloudflare Pages. Simply upload `index.html` and the `img/` folder.

## Browser Compatibility

Works in all modern evergreen browsers (Chrome, Edge, Firefox, Safari) on both desktop and mobile. An internet connection is required for the Tailwind CDN, Google Fonts, the YouTube IFrame API, and QR code generation.

## Privacy & Data Handling

- No images, videos, or text entered into the form are sent to or stored on any external server.
- Photos are compressed and embedded directly into the generated link as Base64 data.
- Story history is saved only in the creator's own browser via `localStorage` and can be fully cleared at any time using the **Wipe All Data** option in the Terms & Privacy modal.
- Because data is embedded in the URL itself, very image-heavy stories can produce long links — this is expected behavior given the no-server design.

## License

No license file is currently included in this project. Add a `LICENSE` file to specify usage terms if you intend to share or distribute this project.
