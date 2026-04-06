
# TimeBleed 🩸
### Anime Countdown Engine

> *"Where time bleeds — and every second has a soul."*

A single-file anime-themed countdown visualizer built in pure HTML, CSS, and JavaScript. No frameworks, no dependencies, no install. Open in any browser and run.

---

## What It Does

TimeBleed lets you set a date range (start → end) and visualize how much time has passed vs. how much remains — with 6 different animated visual styles and 5 full anime theme skins.

---

## Features

### 5 Anime Themes
Switch between full color-graded themes at the top of the app. Each changes fonts, colors, glows, and even the bot's personality.

| Theme | Palette | Font | Vibe |
|---|---|---|---|
| ⚓ One Piece | Gold / Crimson | Pirata One | Grand voyage, pirate treasure |
| 🍃 Naruto | Orange / Deep Purple | Orbitron | Ninja energy, Dattebayo |
| ⚡ Dragon Ball Z | Electric Yellow / Orange | Orbitron | Power level, ki blast |
| 🌸 Demon Slayer | Crimson / Violet | Cinzel Decorative | Taisho era, breathing forms |
| ⚔️ Attack on Titan | Earthy Tan / Brown | Cinzel Serif | Military grit, dedicate your heart |

### 6 Visualization Modes

**Week Blocks** — Your entire time range rendered as a grid of small squares. Red = weeks already gone. Dim = weeks remaining. Gold pulsing block = the current week. Blocks animate in one by one with tick sounds.

**Hourglass** — Canvas-drawn sand clock. Sand fills from the top chamber down through the neck into the bottom as time passes. Live animated drip with falling grain. Sand sounds loop while running.

**Ring Chart** — Two concentric animated rings. Outer ring shows % elapsed with a gradient sweep. Inner ring shows weeks remaining. Rotating dot markers orbit the outside. Rings animate with theme colors.

**Calendar** — Current month calendar view. Days within your range are colored: red for gone, faint for remaining, bold gold for today. Clean day-level overview.

**Timeline** — Horizontal progress bar with a glowing pulsing dot at today's position. Three breakdown bars below showing weeks, days, and hours elapsed simultaneously.

**Seconds** — Live real-time second drain. A ring drains as each second passes, the counter updates every second. For when you need to feel the urgency.

### Nakama Bot 🧭
Floating assistant button (bottom right). Tap to open. Bot's name, avatar, and greeting change per anime theme. Supports quick-tap question chips and free text input. Answers questions about how the app works, what modes do, what % elapsed means, and more.

### Musical Sound Effects
Every action has a distinct musical tone — not robotic beeps. Invoke plays a 5-note ascending chord. Blocks tick with clean sine pulses. Sand mode uses layered soft tones. Ring mode chimes. Seconds mode taps 440 Hz. Toggle sound on/off in the Visualization Style card.

### Living Background
Animated star field with parallax drift and radial nebula glows that shift color with each theme switch.

---

## How to Use

1. Open `TimeBleed.html` in any modern browser (Chrome, Firefox, Safari, Edge).
2. Pick an **anime theme** from the pills at the top.
3. Set your **Start Date** and **End Date** using the date pickers.
4. Select a **Visualization Style** from the 6 mode cards.
5. Toggle **Sound** on or off.
6. Hit **▶ VISUALIZE**.
7. Tap the 🧭 bot button (bottom right) if you have questions.

---

## File Structure

```
TimeBleed.html    ← The entire app. One file. That's it.
README.md         ← This file.
```

No build step. No npm install. No server needed. Just open the HTML file.

---

## Tech Stack

| Layer | What's Used |
|---|---|
| Structure | HTML5 |
| Styling | CSS3 (custom properties for theming, keyframe animations) |
| Logic | Vanilla JavaScript (ES6+) |
| Fonts | Google Fonts (Pirata One, Cinzel, Orbitron, Rajdhani, Cinzel Decorative, Share Tech Mono) |
| Graphics | HTML5 Canvas (hourglass, ring chart, seconds ring, star field) |
| Audio | Web Audio API (oscillator-based musical tones) |
| Storage | None — fully stateless, no cookies, no localStorage |

---

## Browser Support

Works in any browser that supports the Web Audio API and Canvas 2D — which is every modern browser released after 2016.

| Browser | Status |
|---|---|
| Chrome / Edge | ✅ Full support |
| Firefox | ✅ Full support |
| Safari (iOS + macOS) | ✅ Full support |
| Samsung Internet | ✅ Full support |

**Note:** Sound requires a user interaction (tap/click) before it can play — this is a browser security rule for Web Audio, not a bug.

---

## Running as a Mobile App (Android)

Since TimeBleed is a single HTML file, you have two options for Android:

**Option A — PWA (easiest):** Open the file on your Android device in Chrome, tap the menu (⋮), and select "Add to Home Screen". It will behave like a native app with its own icon.

**Option B — WebView APK:** Wrap the HTML file in an Android Studio project using a WebView. The file is fully self-contained and needs no internet connection once loaded.

---

## Customization

All theme colors are CSS custom properties on `body`. To add a new theme:

1. Add a new CSS class block on `body` with your color variables (follow the pattern of `.naruto`, `.dbz`, etc.)
2. Add an entry to the `themeData` object in the JavaScript with `name`, `av` (emoji), `bot` (bot name), and `greet` (opening message)
3. Add a theme pill in the HTML `#themeRow` div

To add a new visualization mode: add a button in `#modeGrid`, then add a `renderYourMode(el, stats)` function and register it in the `goVisualize` dispatch object.

---

## Stats Explained

| Stat | Meaning |
|---|---|
| **Days Gone** | Full days elapsed from start date to today |
| **Days Left** | Days remaining from today to end date |
| **% Elapsed** | `(days gone / total days) × 100` |
| **Weeks Left** | Full 7-day weeks remaining |
| **Seconds Remaining** | Live countdown in seconds (updates every second in Seconds mode) |

---

## Known Limitations

- The hourglass and ring animations run as `requestAnimationFrame` loops — they stop if the tab is in the background (browser optimization) and resume when you return.
- The Seconds counter is calculated from system clock — it won't drift, but it requires the page to remain open.
- Google Fonts are loaded from CDN — themes will still work offline but custom fonts will fall back to system serif/sans-serif.

---

## License

Free to use, modify, and distribute for personal and commercial projects. No attribution required, but appreciated.

---

*Built with one file, five worlds, and zero regrets.*
