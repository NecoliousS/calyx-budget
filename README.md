# Calyx Budget

A personal finance dashboard that runs entirely in the browser. No accounts, no data mining, no subscription fees. Track your balance, bills, savings goals, and free cash in one place.

## Live Demo

https://necoliouss.github.io/calyx-budget/

## What It Does

- Set and edit your account balance with add/subtract/new modes
- Add one-time or recurring bills with flexible due dates
- Create savings goals and contribute from your surplus
- Visual breakdown of where your money goes (bills vs goals vs free cash)
- Built-in calculator and notepad for quick math and notes
- Export everything to CSV

## Tech Stack

- Vanilla JavaScript (ES modules)
- Tailwind CSS via CDN
- Chart.js for the donut chart
- Anime.js for modal animations
- Firebase Auth + Firestore for optional cloud sync
- LocalStorage fallback for offline use

## What I Learned

Managing money in the browser means dealing with floating point math, which gets ugly fast when you're tracking cents. I ended up rounding aggressively and storing everything as raw numbers rather than formatted strings. The flexible date system (month-only, day-only, full date) was trickier than expected because JavaScript's Date constructor behaves differently across browsers when parsing partial dates. I wrote a custom sort function that treats flexible dates as "soonest reasonable guess" rather than forcing users to enter full deadlines.

The Firebase integration was my first time using modular imports from a CDN. I had to expose every function to the window object so onclick handlers in HTML could reach them, which felt hacky but worked. Dark mode theming with Tailwind's data-attribute selector was cleaner than I expected — one attribute flip and the whole UI inverts.

## Features

- Dark/light theme toggle with system preference detection
- Responsive grid layout (collapses to single column on mobile)
- Real-time surplus calculation with color-coded warnings
- Goal progress bars with contribute/withdraw actions
- Bill categorization with emoji-free icon system
