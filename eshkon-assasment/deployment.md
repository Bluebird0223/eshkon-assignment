# Deployment Guide: Eshkon on Vercel

Follow these steps to deploy your application to Vercel.

## 1. Prerequisites
- Your code is already pushed to GitHub: [https://github.com/Bluebird0223/eshkon-assignment](https://github.com/Bluebird0223/eshkon-assignment)
- You have a Vercel account.

## 2. Create a New Project on Vercel
1. Go to the [Vercel Dashboard](https://vercel.com/dashboard).
2. Click **"Add New..."** > **"Project"**.
3. Import your repository: `Bluebird0223/eshkon-assignment`.

## 3. Configure Environment Variables
In the **Environment Variables** section, add the following keys from your `.env.local`:

| Variable | Description |
| :--- | :--- |
| `DATABASE_URL` | Your Neon PostgreSQL connection string. |
| `NEXTAUTH_URL` | Set to your Vercel deployment URL (e.g., `https://your-app.vercel.app`). |
| `NEXTAUTH_SECRET` | A random secure string (use `openssl rand -base64 32` or any long random text). |

> [!IMPORTANT]
> Make sure `DATABASE_URL` is copied exactly as it is in your `.env.local`.

## 4. Deploy
1. Click **"Deploy"**.
2. Vercel will build the application. Since we verified the build locally, it should pass without issues.

## 5. Post-Deployment
- Visit your new URL.
- Login with your existing credentials (since the database is already seeded).
- Verify that you can create, edit, and view pages.

## Troubleshooting
- **Build Errors**: Ensure you wrapped any client-side `useSearchParams` in `Suspense` (I've already done this for `/login`).
- **DB Connection**: If the app fails to start, double-check that the `DATABASE_URL` is correctly pasted in Vercel settings and that your Neon project allows connections from Vercel IPs (standard for Neon).
