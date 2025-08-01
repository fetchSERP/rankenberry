# ![rankenberry-logo](https://github.com/user-attachments/assets/7222a62b-52e2-4474-afa7-653362a0dfa1) Rankenberry: SEO Rank Tracker

[![License: AGPL v3](https://img.shields.io/badge/License-AGPL%20v3-blue.svg)](https://www.gnu.org/licenses/agpl-3.0)

"A simple rank tracking application leveraging a 3rd party API with advanced data features."

## Project Overview

This SEO Rank Tracker is a web application that allows users to track search engine rankings for specified keywords across different projects. It supports multiple SERP data providers – [SpaceSERP](https://appsumo.8odi.net/nLaMra) *or* [FetchSERP](https://fetchserp.com) – which you can switch between with an environment variable. Search-volume information is sourced from Grepwords. Together these services power the advanced analysis and visualisation features of the app.

### Key Features

- Project-based keyword tracking
- SERP data fetching and storage
- Rank tracking over time
- Search volume tracking with 30-day update intervals (via Grepwords)
- Advanced data filtering and visualization
- Keyword tagging system
- Historical data viewing and exporting
- User-friendly interface built with Vue.js
- Google Search Console integration
- Business impact estimation based on rank changes

## Tech Stack

- Frontend: Vue.js 3 with Vite
- Backend: Python with FastAPI
- Database: SQLite
- API Integrations: 
  - [SpaceSERP](https://appsumo.8odi.net/nLaMra) for SERP data (lifetime deal on AppSumo)
  - [FetchSERP](https://fetchserp.com) for SERP data (alternative provider – set `SERP_PROVIDER=fetchserp`)
  - Grepwords for search volume data
  - Google Search Console API for additional search data

## Installation

1. **Clone the repository:**
   ```bash
   git clone https://github.com/your-username/seo-rank-tracker.git
   cd seo-rank-tracker
   ```

2. **Set up the backend:**
   ```bash
   cd backend
   python -m venv venv
   source venv/bin/activate  # On Windows use `venv\Scripts\activate`
   pip install -r requirements.txt
   ```

3. **Set up the frontend:**
   ```bash
   cd ../frontend/rankenberry-frontent
   npm install
   ```

4. **Install additional JavaScript libraries:**
   ```bash
   npm install axios pinia v-calendar plotly.js-dist-min
   ```

5. **Create a `.env` file in the backend directory and add your API keys:**
   ```env
   # --- SERP providers -------------------------------------------------------
   # Choose one of the two providers below and set `SERP_PROVIDER` accordingly.
   # Default provider is `spaceserp` if this variable is omitted.

   # SpaceSERP (https://spaceserp.com)
   SPACESERP_API_KEY=your_spaceserp_api_key_here

   # FetchSERP (https://fetchserp.com)
   FETCHSERP_API_KEY=your_fetchserp_api_key_here

   # Select provider: "spaceserp" (default) or "fetchserp"
   SERP_PROVIDER=spaceserp

   # --- Other services -------------------------------------------------------
   GREPWORDS_API_KEY=your_grepwords_api_key_here
   GOOGLE_CLIENT_ID=your_google_client_id_here
   GOOGLE_CLIENT_SECRET=your_google_client_secret_here
   ```

   To obtain your Google Search Console API credentials:
   1. Go to the [Google Cloud Console](https://console.cloud.google.com/).
   2. Create a new project or select an existing one.
   3. Enable the Google Search Console API for your project.
   4. Go to the "Credentials" section and create a new OAuth 2.0 Client ID.
   5. Choose "Web application" as the application type.
   6. Add authorized redirect URIs (e.g., http://localhost:5000/oauth2callback for local development).
   7. After creating, you'll receive a Client ID and Client Secret. Use these in your `.env` file.

### Additional JavaScript Libraries

- **axios**: Promise-based HTTP client for making API requests.
- **pinia**: State management library for Vue.js applications.
- **v-calendar**: Calendar and date picker component for Vue.js.
- **plotly.js-dist-min**: JavaScript graphing library for creating interactive charts.

These libraries are essential for the functionality of the frontend application. They handle API communication, state management, date selection, and data visualization respectively.

## Getting Started

### Prerequisites

- **Node.js** (v14 or later)
- **Python** (v3.8 or later)
- **pip** (Python package manager)

### Running the Application

1. **Start the backend server:**
   ```bash
   cd backend
   uvicorn app:app --reload
   ```

2. **In a new terminal, start the frontend development server:**
   ```bash
   cd frontend/rankenberry-frontent
   npm run dev
   ```

3. **Open your browser and navigate to** [`http://localhost:5173`](http://localhost:5173) **to use the application.**

## Usage

1. **Add a new project with a domain.**
2. **Add keywords to track for each project.**
3. **Fetch SERP data for your keywords.**
4. **View and analyze ranking data over time.**
5. **Use the tagging system to organize and filter keywords.**
6. **View historical data for individual keywords.**
7. **Export keyword history data as needed.**

## New Features

- **Search Volume Tracking:** The application now fetches and stores search volume data for keywords, updating every 30 days.
- **Keyword Tagging:** Users can add tags to keywords for better organization and filtering.
- **Historical Data Viewing:** A new modal allows users to view and export historical data for individual keywords.
- **Improved Data Visualization:** The rank table includes more detailed metrics and allows for advanced filtering.
- **Async Scheduler Integration:** Utilizes `AsyncIOScheduler` for asynchronous job scheduling, ensuring that scheduled tasks are properly awaited and executed without issues.
- **Resilient Scheduling System:** Enhanced error handling and logging for scheduled tasks to ensure reliability and easier debugging.
- **Google Search Console Integration:** Fetches additional search data to complement SERP information.
- **Business Impact Estimation:** Calculates potential business impact based on rank changes, considering factors such as:
  - Current and previous keyword rankings
  - Search volume for the keyword
  - Click-through rates (CTR) for different ranking positions according to yoour GSC data (and fallback to industry standard CTRs if not available)
  - User-defined conversion rates and conversion values
  This feature helps users understand the potential traffic and revenue implications of ranking changes, providing valuable insights for SEO strategy.

## Contributing

Contributions are welcome! Please feel free to submit a Pull Request.

## Acknowledgments

- Thanks to [SpaceSERP](https://appsumo.8odi.net/nLaMra) and [FetchSERP](https://fetchserp.com) for providing SERP data APIs
- Thanks to Grepwords for providing the search volume data API
- Vue.js and FastAPI communities for their excellent documentation and tools

## TODO

For a list of planned features and improvements, please see our [TODO list](https://github.com/pshapiro/rankenberry/blob/main/TODO.md).

---

*Note: The SpaceSERP link is an affiliate link, which means I may receive commission if you sign up from those links.*