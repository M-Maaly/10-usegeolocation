# 🌍 Geolocation Tracker App

A simple and fun React app that fetches your current GPS location and shows it on **OpenStreetMap** 🗺️. It also tracks how many times you've requested your position!

---

## 🚀 Features

✅ Get current location using the **Geolocation API**  
✅ Live preview on **OpenStreetMap**  
✅ Smart loading & error handling  
✅ Click counter for how many times you've checked your location  

---

## 🛠️ Custom Hook: ```useGeolocation```
**Create a file useGeolocation.js with a custom hook that returns:**
- 📌 lat: latitude
- 📌 lng: longitude
- 🔄 isLoading: loading state
- ⚠️ error: any error message
- 🧭 getPosition(): function to fetch position

---

## 🧠 How It Works

```jsx
import { useState } from "react";
import { useGeolocation } from "./useGeolocation";

export default function App() {
  const [countClicks, setCountClicks] = useState(0);
  const { lat, lng, isLoading, error, getPosition } = useGeolocation();

  function handleClick() {
    getPosition();
    setCountClicks((count) => count + 1);
  }

  return (
    <div>
      <button onClick={handleClick} disabled={isLoading}>
        📍 Get my position
      </button>

      {isLoading && <p>⏳ Loading position...</p>}
      {error && <p>❌ {error}</p>}
      {!isLoading && !error && lat && lng && (
        <p>
          🌐 Your GPS position:{" "}
          <a
            target="_blank"
            rel="noreferrer"
            href={`https://www.openstreetmap.org/#map=16/${lat}/${lng}`}
          >
            {lat}, {lng}
          </a>
        </p>
      )}

      <p>🧮 You requested position <strong>{countClicks}</strong> times</p>
    </div>
  );
}
```
# 👨🏼‍🚀 Author
**Made with ❤️ by @M-Maaly**
