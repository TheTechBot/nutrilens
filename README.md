# NutriLens

**Snap a photo of your meal. Get calories, macros and a per-item breakdown in seconds.**

NutriLens is an AI food tracker built with plain HTML, CSS and JavaScript plus the Claude API. It installs like a native app on Android, iOS and desktop, works offline after first load, and adapts to any screen size without scrolling.

> Rebuilt from scratch after I lost the original project files. Design ideas were borrowed from popular AI calorie apps (daily dashboard, editable portions, confidence score, meal log).

| Phone | | Phone |
|---|---|---|
| ![Today](screenshots/phone-today.png) | ![Result](screenshots/phone-result.png) | ![Settings](screenshots/phone-settings.png) |

![Desktop dark theme](screenshots/desktop-dark.png)
![Desktop light theme](screenshots/desktop-light.png)

## Features
- Log a meal by photo or by typing what you ate
- AI estimate of calories, protein, carbs, fat, with per-item breakdown
- Confidence score on every result
- Portion stepper: change the portion and all numbers rescale
- Daily calorie ring, macro progress bars, 7-day chart, meal log
- Adjustable daily calorie goal
- 5 themes plus a custom accent colour picker
- Responsive fixed layout: phone, tablet, desktop, no page scrolling
- Installable PWA, offline shell, Android APK ready

## Try it
1. Open the live app: `https://YOUR-USERNAME.github.io/nutrilens/`
2. Go to **Settings** and paste your own [Anthropic API key](https://console.anthropic.com/).
3. Tap **+** (or **Scan food**), add a photo, tap **Analyze**.

Your key is saved only in your own browser. It is never in this repository.

## Install as an app
- **Android:** open the live link in Chrome, menu, **Add to Home screen**. Or download the APK from the [Releases](../../releases) page.
- **iPhone:** open the link in Safari, Share, **Add to Home Screen**.
- **Desktop:** click the install icon in the Chrome or Edge address bar.

## How it works
1. The photo is resized in the browser to 1024 px and compressed to JPEG.
2. It is sent with a short prompt to the Claude Messages API, which returns structured JSON (dish, calories, macros, items, confidence, tip).
3. The app validates the response, shows it, and stores your meal log in `localStorage` on your device.

No server. No account. No analytics.

## Project structure
```
index.html              the whole app (HTML, CSS, JS)
manifest.webmanifest    install metadata
sw.js                   service worker (offline shell)
icon-*.png              app icons
screenshots/            README images
```

## Known limitations
- Calorie numbers are **AI estimates from a photo**, not measurements. Not medical or dietary advice.
- The app calls the API directly from the browser, so each user must bring their own API key. A production version needs a small backend to hold the key.
- Meals are stored per device. No sync between devices.
- The Today list shows only the meals that fit the screen.

## Roadmap
- Backend proxy so users do not need their own key
- Barcode and nutrition-label scanning
- Full history screen and weekly insights
- Export meal log to CSV

## Tech
HTML5, CSS custom properties (theming), vanilla JavaScript, Web App Manifest, Service Worker, Claude API.

## License
MIT. See [LICENSE](LICENSE).
