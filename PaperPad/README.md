# PaperPad

> Repository name: **SCAMslayer** &nbsp;·&nbsp; App name: **PaperPad**

A voice-first notebook for people who'd rather talk than type. Built especially for older users — anyone used to writing things down on paper but tired of fumbling with tiny keyboards.

## What it does

You tap one big button, speak naturally, and your words become tidy bullet points on the screen. When you're finished, one more tap saves everything as a **PDF**, **Word document**, or **plain text file** — ready to print, email, or keep.

The interface is deliberately stripped down. Three buttons do the work: **Start Listening**, **Next Point**, **Add Table**. Save buttons live at the bottom. Nothing else gets in the way.

## Voice commands

Three things to remember:

| Say this                                            | What happens                                                |
|-----------------------------------------------------|-------------------------------------------------------------|
| "next point" / "new bullet"                         | Starts a new bullet                                         |
| "erase that" / "erase the last bullet" / "scratch that" / "delete the last one" / "remove the line" | Removes the last bullet — works whether you say "that," "this," "the last one," "the last bullet," "the line," etc. |
| "make a table" / "create a table"                   | Opens the table builder, then keeps listening               |

Inside the table builder, three more:

| Say this                  | What happens                                  |
|---------------------------|-----------------------------------------------|
| (just speak with commas)  | Each comma-separated phrase becomes a row     |
| "next row" / "new row"    | Commits the current row, starts a new one    |
| "finish table"            | Saves the table and goes back to your notes   |

## Numbers come out as digits

When you say a number like *"twenty-five"*, *"one hundred"*, or *"five thousand"*, PaperPad writes it as **25**, **100**, **5000** instead of spelling it out. So *"buy two eggs and twelve apples"* becomes *"Buy 2 eggs and 12 apples"* automatically.

## Building tables by voice

Say **"make a table"**. The table builder opens and the microphone keeps listening. Speak the column names first (with commas between them, like *"Name, Age, City"*). Then speak each row the same way. Say **"next row"** when you want to start a new row, or it'll keep adding to the current one. When you're done, say **"finish table"** — or tap the green **Finish Table** button.

You can always edit any cell by tapping it, and you can mix voice and typing freely.

## Features

- Voice dictation in any modern browser (Chrome, Edge, Safari)
- Typed input as a fallback — no microphone required
- Spoken **next point** to split into bullets
- Spoken **undo** with many natural phrasings
- Spoken **table creation and filling** — full hands-free table entry
- Spoken **numbers** automatically converted to digits ("twenty-five" → 25)
- One-tap export to **PDF**, **.doc** (Word), or **.txt** — tables included
- Big buttons, large fonts, sky-blue palette designed for older eyes
- Installable as a Progressive Web App on Android and iPhone
- Works offline once installed
- No account, no tracking, no servers — your notes stay on your device

## How to run it locally

Browsers block microphone access on raw `file://` URLs, so serve it locally:

```bash
git clone https://github.com/<your-username>/SCAMslayer.git
cd SCAMslayer
python3 -m http.server 8000
# then open http://localhost:8000
```

## How to ship it to someone's phone

1. Drag the project folder onto **[app.netlify.com/drop](https://app.netlify.com/drop)** — free, no signup, gives you an `https://` URL in seconds.
2. Send the URL on WhatsApp.
3. The recipient taps the link, then chooses **"Add to Home Screen"** (Safari Share menu on iPhone, three-dot menu on Android Chrome). The app installs like a native app.

For an actual `.apk` to attach in WhatsApp: paste the Netlify URL into **[pwabuilder.com](https://www.pwabuilder.com)**, click *Package For Stores → Android*, and download the signed APK. (APKs are Android-only.)

## Tech stack

- **React 18** (loaded from CDN, no build step)
- **Babel Standalone** for in-browser JSX
- **Web Speech API** (`SpeechRecognition`) for voice-to-text
- **jsPDF** + **jspdf-autotable** for PDF generation
- HTML/Word XML for `.doc` export, plain-text Blob with ASCII tables for `.txt`
- Service worker + Web App Manifest for PWA installability and offline use

Everything is a single static folder — no Node, no bundler, no backend.

## Project structure

```
PaperPad/
├── index.html             # the whole app (UI + logic in one file)
├── manifest.webmanifest   # PWA metadata
├── sw.js                  # service worker for offline caching
├── icon-192.png           # home-screen icon (small)
├── icon-512.png           # home-screen icon (large)
├── icon-maskable-512.png  # adaptive icon for Android
└── README.md              # you are here
```

## License

MIT — do whatever you want with it.
