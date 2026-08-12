# ABBAHGAMJI — Frontend (static site)

The storefront (`index.html`) and admin dashboard (`admin.html`). Pure static
HTML/CSS/JS — no build step, no framework. Deploys to Vercel as a static site.

## Before you deploy: point it at your backend

Both files call the API through one constant near the top of their `<script>`:

```js
const API_BASE_URL = "https://YOUR-BACKEND-PROJECT.vercel.app";
```

Deploy the `backend/` project first (see its README), copy the URL Vercel
gives you, and paste it in as `API_BASE_URL` in **both**:
- `index.html` (around line 846)
- `admin.html` (around line 231)

Then commit that change before deploying this project (or deploy first and
redeploy after editing — either order works).

## Deploy to Vercel

1. Push this `frontend/` folder to its own GitHub repo (separate from `backend/`).
2. https://vercel.com → **Add New → Project** → import that repo.
3. Framework preset: **Other** (no build command needed — it's static files).
4. Deploy. You'll get a URL like `https://abbahgamji.vercel.app`.
5. Go back to the backend project's Vercel environment variables and set
   `FRONTEND_URL` to this URL, then redeploy the backend — this is what lets
   emailed magic-login and order-tracking links point at the right place.

- Storefront: `https://your-frontend.vercel.app/`
- Admin dashboard: `https://your-frontend.vercel.app/admin.html` — log in
  with the `ADMIN_TOKEN` value you set in the **backend's** environment
  variables (see the backend README for why there's no default admin
  password to hand you).
