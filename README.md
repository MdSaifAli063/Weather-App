# ⛅ Weather App

![HTML5](https://img.shields.io/badge/HTML5-E34F26?style=for-the-badge&logo=html5&logoColor=white)
![CSS3](https://img.shields.io/badge/CSS3-1572B6?style=for-the-badge&logo=css3&logoColor=white)
![JavaScript](https://img.shields.io/badge/JavaScript-F7DF1E?style=for-the-badge&logo=javascript&logoColor=black)
![OpenWeatherMap](https://img.shields.io/badge/API-OpenWeatherMap-orange?style=for-the-badge)
![License](https://img.shields.io/badge/License-MIT-green?style=for-the-badge)
![Deployment](https://img.shields.io/badge/Static%20Hosting-Ready-blue?style=for-the-badge)

A lightweight, responsive weather application using **OpenWeatherMap** that supports geolocation, light/dark themes, Celsius/Fahrenheit units, a 5-day forecast, and removable recent searches. No build tools needed — just static HTML/CSS/JS.

---

## 🚀 Demo

- Open `index.html` locally or serve via a static server (recommended for geolocation).
- ![Weather App Screenshot](https://github.com/Mdsaif4363/Weather-App/blob/593e8c71e6d5fb3bf79b95de5d1eaa0de74d5f95/Screenshot%202025-08-25%20155511.png)

---

## ✨ Features

- 🔍 Search weather by city
- 📍 Use My Location via browser geolocation (HTTPS or localhost required)
- 🌡️ Unit toggle: Celsius ↔ Fahrenheit (persists in `localStorage`)
- 🌓 Theme toggle: Light ↔ Dark (persists in `localStorage`)
- 📊 Current weather details:
  - Temperature
  - Description
  - Feels like
  - Humidity
  - Wind
  - Sunrise/Sunset
- 📅 5-day forecast with daily min/max and icons
- 🕘 Recent searches:
  - Click to search again
  - Remove individual chips (×)
  - Clear all
- ⏳ Loading spinner and friendly error messages
- 📱 Responsive, accessible UI (keyboard navigation + ARIA labels)

---

## 🛠️ Tech Stack

| Tool | Description |
|------|-------------|
| 🧱 HTML5 | Markup |
| 🎨 CSS3 | Styling (themes, responsiveness) |
| ⚙️ JavaScript | App logic, API calls |
| 🌐 OpenWeatherMap API | Weather data |

---


## 📁 Project Structure

. ├── index.html       # App markup ├── style.css        # Styles (themes, responsive) └── script.js        # App logic, API requests, UI updates

---

## 🔑 Prerequisites

- Get a free API key from [OpenWeatherMap](https://openweathermap.org/)
- For geolocation to work: serve over HTTPS or use `localhost`

---

## ⚙️ Setup

1. Get your API key from OpenWeatherMap.
2. Open `script.js` and set your key:

```js
const API_KEY = "YOUR_OPENWEATHER_API_KEY";
```
💡 Tip: Since this is a client-side app, your key is visible. Restrict it to your domain(s) in your OpenWeather account to prevent abuse.

## 🧪 Usage

- Type a city (e.g., “London”, “Paris”) and click Get Weather or press Enter
- Click Use My Location to fetch weather via geolocation
- Toggle units with Switch to °F/°C
- Toggle theme with Dark Mode/Light Mode

Recent Searches:
Click a chip to search again
Click × on a chip to remove it
Click “Clear All” to remove the entire history

Keyboard shortcuts:

In the city input: Enter submits the search.
On a recent search chip: Enter/Space triggers search; the × button is clickable/focusable to remove.

API Details

Base URL: https://api.openweathermap.org/data/2.5

Endpoints used:

Current weather: /weather?q={city}&appid={API_KEY}&units={metric|imperial}
Forecast (3-hourly): /forecast?q={city}&appid={API_KEY}&units={metric|imperial}

Notes:

Units: metric = °C and m/s, imperial = °F and mph
Icons: https://openweathermap.org/img/wn/{iconCode}@2x.png
Forecast is reduced to one representative entry per day (closest to 12:00) and daily min/max computed from all entries of that day.

Persistence

localStorage keys:
units (“metric” | “imperial”)
theme (“light” | “dark”)
history (JSON array of city names)
lastCity (last successful city name)

Accessibility

Buttons and interactive elements include aria-labels.
History chips are keyboard-focusable; Enter/Space activates search.
Live regions:
Loading uses role="status" and aria-live="polite".
Errors use role="alert".

Troubleshooting

“Please set your OpenWeatherMap API key”:
Make sure you replaced YOUR_OPENWEATHER_API_KEY in script.js.
Geolocation denied/not working:
Ensure you’re on HTTPS or http://localhost.
Browser settings may block geolocation—allow location access when prompted.
404 City not found:
Check spelling; try “City, CountryCode” (e.g., “Paris, FR”).
Rate limits:
Free OpenWeather plans have limits (e.g., 60 requests/min). Avoid rapid toggling and repeated queries.

Customization

Colors and themes: modify CSS variables in style.css:
Dark theme defaults in :root
Light theme overrides in body.light
Maximum history items: adjust the cap (8) in script.js in persistCity.
Forecast length: change pickDaily(byDate, 5) to show more/less days.

Security Note

This is a client-side demo. API keys in the browser are public. For production, consider a small proxy backend to keep your key secret and add rate limiting.

Roadmap Ideas

Air quality and precipitation probability
Hourly forecast chart (e.g., Chart.js)
Favorite cities pinning and reordering
Multi-language support
PWA/offline caching

License

MIT — feel free to use and modify. Add your name/company to the LICENSE file if needed.
