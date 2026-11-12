# Velor Board Daily

A daily check-off app for the 22 exercises in *The Complete Velor Board Blueprint*, grouped by body part, built to strengthen knees.

## Features

- **Daily checklist** grouped by body part: Calves, Achilles & Ankles · Hamstrings · Quads & Knees · Hips & Glutes (band)
- **Exercise details**: animated illustration, sets & reps, how to do it, and benefit for every exercise
- **Today's plan**: picks a daily mix based on your goal and rotates it so days don't repeat (the default goal, knee strength, is calf + quad + hamstring)
- **Set tracking**: tap a dot after each set; a 30-second rest timer starts automatically
- **Hold timer** for the timed stretches
- **Knee comfort log**: rate your knees 1–5 each day and add a note, see a 30-day chart, and copy a summary for your doctor or PT
- **Getting stronger**: log your best set; after three sessions in a row at the top of the range, the app suggests the next level
- **Guided workout mode**: one exercise at a time, full screen
- Streaks, a 7-day history strip, and back-filling of missed days

## How it's built

It's one self-contained file, `index.html`, with no build step and no dependencies. The illustrations are drawn in code (SVG).
Progress is saved in the browser (`localStorage`) on each device.

| File | Purpose |
|---|---|
| `index.html` | The whole app |
| `manifest.webmanifest` | Makes it installable as an app (name, icon, colors) |
| `sw.js` | Lets it open offline once installed |
| `icons/` | App icons |

## Run it locally

```bash
npx serve .        # or: python3 -m http.server 8000
```

Then open the address it prints. Opening `index.html` directly also works, but install and offline mode need a web address (`http://localhost` or `https://`).

## Turn it into a phone app

### Option 1: Installable web app (easiest, free)
1. Host the folder on any HTTPS host: GitHub Pages, Netlify, Vercel or Cloudflare Pages.
   *GitHub Pages needs a public repo on a free GitHub plan. This repo is private because the exercise text comes from the Velor book, so Netlify or Vercel (both free, both work with private repos) are the easier choice.*
2. Open the site on your phone:
   - **iPhone (Safari):** Share → **Add to Home Screen**
   - **Android (Chrome):** ⋮ menu → **Install app**
3. It opens full-screen with its own icon and works offline.

### Option 2: Real App Store / Play Store app (Capacitor)
```bash
npm init -y
npm install @capacitor/core @capacitor/cli @capacitor/ios @capacitor/android
npx cap init "Velor Board Daily" com.yourname.velordaily --web-dir www
mkdir www && cp -r index.html manifest.webmanifest sw.js icons www/
npx cap add ios        # needs a Mac with Xcode
npx cap add android    # needs Android Studio
npx cap open ios       # or: npx cap open android
```
Publishing to the stores requires an Apple Developer account ($99/yr) and/or a Google Play developer account ($25 one-time).

## Ideas for later
- Sync progress across devices with an account (e.g. Supabase)
- Daily reminder notifications (available through Capacitor)
- Export history as CSV

## Disclaimer
The Velor Board is for general fitness only and is not a medical device. Consult a healthcare professional before use if you have injuries, medical conditions, or prior surgery.
Exercise descriptions are from *The Complete Velor Board Blueprint* by VelorHealth.
