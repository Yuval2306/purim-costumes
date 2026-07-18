<div align="center">

# 🎭 Purim AI — Costume Idea Generator

**Pick a Purim costume, upload a photo, and get personalized AI recommendations for your look, makeup, and accessories.**

An interactive, single-page web app with a Hebrew (RTL) interface, powered by Google Gemini.

![HTML5](https://img.shields.io/badge/HTML5-E34F26?style=flat&logo=html5&logoColor=white)
![CSS3](https://img.shields.io/badge/CSS3-1572B6?style=flat&logo=css3&logoColor=white)
![JavaScript](https://img.shields.io/badge/JavaScript-F7DF1E?style=flat&logo=javascript&logoColor=black)
![Gemini](https://img.shields.io/badge/Google_Gemini-8E75B2?style=flat&logo=googlegemini&logoColor=white)
![Cloudflare Workers](https://img.shields.io/badge/Cloudflare_Workers-F38020?style=flat&logo=cloudflare&logoColor=white)
![No Build](https://img.shields.io/badge/build-none-brightgreen?style=flat)

</div>

---

## ✨ Features

- 🎨 **Costume picker** — choose from a wide range of ready-made costumes.
- 📸 **Photo upload** — select a file or drag & drop, with an instant preview before sending.
- 🛡️ **File guardrails** — 10 MB size limit and image-type validation on the client.
- 🤖 **AI recommendations** — Gemini analyzes your photo and returns tailored suggestions in Hebrew.
- 💫 **Festive UI** — responsive RTL layout with Purim-themed animations, confetti, and a typing effect for results.

## 🧰 Tech Stack

| Layer | Technology |
| --- | --- |
| Markup | HTML5 |
| Styling | CSS3 (custom properties, animations) |
| Logic | Vanilla JavaScript — no frameworks |
| Fonts | Google Fonts — *Heebo* & *Secular One* |
| AI | Google Gemini via a Cloudflare Worker |

The whole project is a **single static page** — no build step and no dependencies to install.

## 🚀 Run Locally

No dependencies required. After cloning the project, open a terminal in the project folder and run:

```bash
python -m http.server 8000
```

Then open in your browser:

```text
http://127.0.0.1:8000/purim-costumes.html
```

> You can also open `purim-costumes.html` directly in your browser, but a local server is recommended to avoid browser restrictions on network requests.

## 🔍 How It Works

1. The user selects a costume.
2. The user uploads an image in a supported format.
3. The browser converts the image to Base64.
4. The image, its MIME type, and a text prompt are sent to a Cloudflare Worker.
5. The Worker calls Gemini and returns an analysis with recommendations in Hebrew.
6. The result is displayed on the site with a typing animation.

The Worker URL is defined by the `WORKER_URL` constant inside the `analyzeImage` function in `purim-costumes.html`:

```js
const WORKER_URL = "https://purim-gemini.yuvalboker588.workers.dev";
```

To use a different Worker, replace this value accordingly.

## 📁 Project Structure

```text
purim-costumes/
├── purim-costumes.html   # Page structure, styling, and all logic
└── README.md             # Project documentation
```

## 🌐 Deployment

Since this is a static site, you can deploy it on services such as:

- GitHub Pages
- Cloudflare Pages
- Netlify
- Vercel

Make sure the Cloudflare Worker allows CORS requests from the domain where the site is hosted.

## 🔒 Privacy & Security

- Images are sent to an external service for analysis — they are **not** processed only in the browser.
- Never put an API key directly in the HTML or client-side JavaScript.
- Store your Gemini key as a **Secret** in the Cloudflare Worker.
- Before public use, consider adding a privacy policy, request rate limiting, and server-side file validation.

## 🎨 Customization

The costume list lives in the `COSTUMES` array inside the HTML file. Each entry can define:

```js
{
  emoji: "🦸",
  name: "סופרמן",
  nameEn: "Superman",
  desc: "Costume description"
}
```

You can also change the core colors via the CSS variables defined under `:root`.

## 📄 License

No license has been defined for this project. All rights reserved by the project owner unless an explicit license file is added.

## 👤 Author

Built by **Yuval Boker**.
