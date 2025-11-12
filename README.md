# Task Manager — Frontend

This is the React frontend for a Task Manager application. It provides user authentication (signup/login) and task CRUD functionality. The app communicates with a backend API (default: http://localhost:5000) for authentication and task operations.

## Tech Stack

- Framework: React 18 (Create React App)
- Styling: Tailwind CSS
- State: React Context API
- HTTP client: Axios
- Routing: React Router DOM
- Notifications: React Toastify

## Features

- User authentication (Signup / Login)
- Task create / read / update / delete
- Protected routes
- Responsive UI and loading states

## Installation (local)

1. Clone the repository (or open the folder if you already have it locally):

```powershell
git clone <repository-url>
cd task-manager-frontend-main
```

2. Install dependencies:

```powershell
npm install
```

3. Environment variables

Create a `.env` file in the project root (optional). The frontend reads `REACT_APP_API_URL` to determine the backend base URL. If not set it defaults to `http://localhost:5000`.

Example `.env`:

```env
REACT_APP_API_URL=http://localhost:5000
```

4. Start the development server:

```powershell
npm start
```

App will open at http://localhost:3000 by default.

## Project structure

```
task-manager-frontend-main/
├── public/
│   └── index.html
├── src/
│   ├── components/      # React components (Login, Signup, TaskList, TaskForm...)
│   ├── context/         # AuthContext.js, TasksContext.js
│   ├── services/        # api.js (axios instance)
│   ├── App.js
│   └── index.js
├── package.json
└── tailwind.config.js
```

## API endpoints (expected)

The frontend calls endpoints under the backend base URL, for example:

- POST /api/auth/signup
- POST /api/auth/login
- GET/POST/PUT/DELETE /api/tasks

Adjust `REACT_APP_API_URL` if your backend runs on a different host/port.

## Troubleshooting — Signup validation errors

- If you see backend validation errors referencing `username` or `email`, open `src/context/AuthContext.js`. The frontend sends a `username` field constructed from the first and last name. Some backends validate `username` to ensure it contains only certain characters or has length constraints.
- If the backend returns "Validation errors" for `username`, you can:
	- Check the Console (DevTools) — this project logs the signup payload (`Signup payload: {...}`) before sending. Verify the `username` value.
	- Update the username generation in `src/context/AuthContext.js` to match your backend's rules, or send a user-entered username field.
	- Ensure `REACT_APP_API_URL` points to your backend and that the backend is running.

## Scripts

- `npm start` — start dev server
- `npm run build` — build production bundle
- `npm test` — run tests (if configured)

## Notes

- The default backend base URL is `http://localhost:5000` — change via `REACT_APP_API_URL` if needed.
- If you control the backend, check the signup route's validation rules to know the exact `username` format required.

---

If you'd like, I can also update the project README further (add screenshots, run/debug steps, or PR-ready instructions).
