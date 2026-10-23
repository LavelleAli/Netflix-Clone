# Netflix Clone

A Netflix-style streaming UI built with React and Vite. Users sign up or sign in with Firebase Authentication, browse rows of real movie data pulled from The Movie Database (TMDB), and click any title to watch its trailer.

> This is a learning project. It is not affiliated with or endorsed by Netflix, and it does not stream any actual films, only trailers hosted on YouTube.

## Features

- **Authentication**: sign up and sign in with email and password through Firebase Auth. New users are also saved to a Firestore `user` collection.
- **Protected routing**: signed-out visitors are sent to `/login`, and signed-in users land on the home page.
- **Home page**: a hero banner, plus horizontally scrolling rows for Now Playing, Top Rated, Popular and Upcoming movies from TMDB. The mouse wheel scrolls each row sideways.
- **Trailer player**: clicking a card opens `/player/:id`, which looks up the movie's videos on TMDB and embeds the trailer from YouTube along with its name, type and release date.
- **Navbar**: turns solid once you scroll down the page, and has a profile dropdown with a Sign Out option.
- **Feedback**: auth errors appear as toast notifications, and a Netflix-style spinner shows while sign-in is in progress.

## Tech Stack

| Area | Tools |
| --- | --- |
| UI | React 19, plain CSS |
| Build | Vite |
| Routing | React Router 7 |
| Auth and database | Firebase Authentication, Cloud Firestore |
| Movie data | TMDB API |
| Notifications | react-toastify |
| Linting | ESLint |

## Getting Started

### Prerequisites

- Node.js 20 or later, and npm
- A Firebase project with **Email/Password** sign-in and **Cloud Firestore** enabled
- A TMDB account and its **API Read Access Token** (found under Settings → API)

### Installation

```bash
git clone https://github.com/LavelleAli/NetflixClone__LavelleAli.git
cd NetflixClone__LavelleAli
npm install
```

### Configuration

- **Firebase**: replace the `firebaseConfig` object in `src/firebase.js` with the config from your own Firebase project (Project settings → Your apps → Web app).
- **TMDB**: copy the example env file and paste in your read access token.

  ```bash
  cp .env.example .env
  ```

  ```
  VITE_TMDB_TOKEN=your_tmdb_read_access_token_here
  ```

  `.env` is listed in `.gitignore`, so your token stays out of the repo. Restart `npm run dev` after editing it.

> **Note:** Vite bundles any `VITE_` variable into the client-side JavaScript, so the token can still be seen in the browser's network requests. That's acceptable for TMDB's read-only token on a demo project. For a production app, call TMDB from a small backend or serverless function instead.

### Run it

```bash
npm run dev
```

Then open the local URL Vite prints (usually http://localhost:5173).

## Available Scripts

| Command | What it does |
| --- | --- |
| `npm run dev` | Starts the Vite dev server with hot reload |
| `npm run build` | Builds the app for production into `dist/` |
| `npm run preview` | Serves the production build locally |
| `npm run lint` | Runs ESLint across the project |

## Project Structure

```
src/
├── App.jsx                 # Routes and auth-state redirects
├── main.jsx                # App entry point, wraps App in BrowserRouter
├── firebase.js             # Firebase setup plus signup, login and logout helpers
├── components/
│   ├── Navbar/             # Top navigation and profile dropdown
│   ├── TitleCards/         # Scrolling row of movie cards from TMDB
│   └── Footer/             # Social icons and footer links
├── pages/
│   ├── Home/               # Hero banner and movie rows
│   ├── Login/              # Sign in and sign up form
│   └── Player/             # Trailer player for a single movie
└── assets/                 # Images, icons and the loading spinner
```

## Routes

| Path | Page |
| --- | --- |
| `/` | Home |
| `/login` | Sign in and sign up |
| `/player/:id` | Trailer for the TMDB movie with that `id` |

## Acknowledgements

- Movie data and images from [The Movie Database (TMDB)](https://www.themoviedb.org/). This product uses the TMDB API but is not endorsed or certified by TMDB.
- Trailers are embedded from YouTube.

## Author

**Lavelle Ali**, [GitHub](https://github.com/LavelleAli)
