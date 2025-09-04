#  React URL Shortener Web App
##  Overview

This project is a **client-side only React web app** that allows users to shorten URLs, manage custom shortcodes, and view analytics like click counts and sources.
It follows the given evaluation guidelines with **Material UI**, **React Router**, and a **custom logging middleware** for monitoring app events.


##  Project Structure

```
src/
│── components/
│   ├── URLForm.js         # Form for shortening URLs
│   ├── URLList.js         # Display list of shortened URLs
│   ├── StatsTable.js      # Show analytics for each short URL
│   └── ErrorMessage.js    # Reusable error display
│
│── pages/
│   ├── ShortenerPage.js   # Main page for URL shortening
│   ├── StatsPage.js       # Analytics & statistics
│   └── RedirectPage.js    # Handles /:shortcode → long URL redirection
│
│── utils/
│   ├── storage.js         # Client-side persistence (localStorage)
│   ├── validator.js       # URL & shortcode validation
│   └── logger.js          # Provided logging middleware
│
│── App.js                 # Routes + layout
│── index.js               # Entry point
```

---

##  Features

* ✅ Shorten up to **5 URLs at once**
* ✅ **Custom shortcode** support (unique & validated)
* ✅ **Default expiry = 30 mins** if not provided
* ✅ **LocalStorage persistence** for current session analytics
* ✅ **Click analytics**:

  * Total clicks
  * Timestamp of clicks
  * Source (referrer)
  * Approximate geo-location (via `window.navigator`)
* ✅ **Error handling** with user-friendly messages
* ✅ **Material UI** for consistent design
* ✅ **React Router** for navigation & redirection


##  Tech Stack

* **React 18** – Frontend library
* **Material UI (MUI)** – Styling & UI components
* **React Router** – Client-side routing & redirection
* **LocalStorage** – Client-side persistence
* **Custom Logging Middleware** – For monitoring events


## Key Design Choices

1. **Client-Side Only**:
   All data (short URLs, analytics) are stored in `localStorage`.
   This simulates persistence without a backend.

2. **Routing**:

   * `/` → URL Shortener Page
   * `/stats` → Statistics Page
   * `/:shortcode` → Redirect Page

3. **Data Model (stored in localStorage)**:

   ```json
   {
     "shortcode": {
       "originalUrl": "https://example.com",
       "createdAt": "2025-09-04T12:00:00Z",
       "expiresAt": "2025-09-04T12:30:00Z",
       "clicks": [
         {
           "timestamp": "2025-09-04T12:15:00Z",
           "source": "direct",
           "geo": "India"
         }
       ]
     }
   }
   ```

4. **Error Handling**:

   * Invalid URL → "Please enter a valid URL."
   * Duplicate shortcode → "Shortcode already in use."
   * Expired link → Redirects to error message page.


## Getting Started

### 1. Clone Repo

```bash
git clone https://github.com/your-username/react-url-shortener.git
cd react-url-shortener
```

### 2. Install Dependencies

```bash
npm install
```

### 3. Run App

```bash
npm start
```

App will run on 👉 [http://localhost:3000](http://localhost:3000)


##  Example User Flow

1. User enters up to 5 URLs → clicks **Shorten**
2. Short links are generated (`http://localhost:3000/abc123`)
3. User shares/visits the short link → Redirects to original URL
4. Analytics (clicks, timestamps, sources, geo) update in Stats Page

