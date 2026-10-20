# D&D Calendar

Web app to coordinate Dungeons & Dragons sessions. Players mark when they are free, the Master finds the common slots.

## Features
- **Weekly mode**: hour grid for the next week, with multi-day copy.
- **Monthly mode**: day calendar with time ranges and a "every same weekday" shortcut.
- Share availability as a **link or text code**; no server or account needed.
- **Master view**: overlap computation with time-zone conversion, partial matches and PNG export.
- Week code converter to reuse old codes.

## Usage
Open `index.html` in a browser (or serve the repository with GitHub Pages).
The Master view is unlocked by tapping the title 7 times, pressing `Ctrl+Shift+M`, or opening a shared link.

## Privacy
Everything runs in the browser. Data is stored only in `localStorage` and travels only inside the codes/links players share.

## Tech
Single-file HTML/CSS/JavaScript, [html2canvas](https://html2canvas.hertzen.com/) loaded from cdnjs for image export.