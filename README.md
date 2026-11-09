# EventConnect Kenya

A premium, responsive marketplace frontend for discovering and booking bands, DJs, MCs, photographers, sound and lighting providers and solo musicians across Kenya.

Built with **React 18**, **Vite**, **Tailwind CSS 4** and **Lucide React** icons. There is no backend yet: all data is demo data in `src/data/`, and every interactive feature runs on React state.

## Features

- Sticky navigation with a responsive mobile menu and smooth scrolling
- Hero search (service, location, date) that filters the talent list
- Clickable category cards that filter featured talent
- Provider cards with ratings, genres, location and starting price
- Interactive event package builder with a live estimated total
- Booking request modal and provider registration modal (with loading and success states)
- How It Works, testimonials, footer and demo Log In / Get Started modals

## Project structure

```
eventconnect-kenya/
├── index.html              # HTML shell, SEO meta tags, font links
├── package.json            # Dependencies and scripts
├── vite.config.js          # Vite + React + Tailwind plugin config
├── .nvmrc                  # Node version (20)
├── .gitignore
├── .github/workflows/ci.yml  # Builds the project on every push / PR
├── public/                 # Static files copied as-is to the build
│   ├── favicon.svg
│   ├── robots.txt
│   └── _headers            # Cloudflare security and cache headers
└── src/
    ├── main.jsx            # App entry point
    ├── App.jsx             # Page composition and modal state
    ├── index.css           # Tailwind import + custom animations
    ├── components/         # Reusable UI components
    ├── data/               # Demo data (categories, providers, services, ...)
    └── utils/helpers.js    # Price formatting and smooth scroll helpers
```

## Requirements

- Node.js 20 or newer
- npm (included with Node.js)

## Installation and local development

```bash
npm install
npm run dev
```

Open the URL printed in the terminal (usually http://localhost:5173).

Other commands:

```bash
npm run build     # Production build into dist/
npm run preview   # Serve the production build locally
```

`npm install` creates a `package-lock.json`. Commit it so every build installs identical versions.

## Push to GitHub

1. Create an empty repository on GitHub (for example `eventconnect-kenya`) without a README.
2. In the project folder run:

```bash
git init
git add .
git commit -m "Initial commit: EventConnect Kenya frontend"
git branch -M main
git remote add origin https://github.com/<your-username>/eventconnect-kenya.git
git push -u origin main
```

The included GitHub Actions workflow builds the project on every push and pull request.

## Deploy to Cloudflare Pages

### Option A: connect the GitHub repository (recommended)

1. Log in to the Cloudflare dashboard and go to **Workers & Pages**.
2. Choose **Create application**, then **Pages**, then **Connect to Git**.
3. Select your `eventconnect-kenya` repository.
4. Use these build settings:

| Setting | Value |
| --- | --- |
| Framework preset | Vite (or None) |
| Build command | `npm run build` |
| Build output directory | `dist` |
| Environment variable | `NODE_VERSION` = `20` |

5. Click **Save and Deploy**. Every push to `main` will redeploy automatically.

### Option B: deploy from your computer with Wrangler

```bash
npx wrangler login
npm run deploy:cloudflare
```

This builds the project and uploads `dist/` to a Pages project named `eventconnect-kenya` (change the name in `package.json` if you like).

### Custom domain

In your Pages project open **Custom domains**, add your domain and follow the DNS steps shown.

## Customising

- Add or edit providers in `src/data/providers.js`
- Change package services and prices in `src/data/services.js`
- Edit categories, cities and testimonials in the other files in `src/data/`
- Brand colours and animations live in `src/index.css` and in the Tailwind classes inside the components

## Next steps

Authentication, a database, real provider profiles and live booking requests need a backend. This frontend is structured so those can be connected later without changing the UI.
