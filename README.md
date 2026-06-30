# PropScribe — AI Property Listing Generator

AI-powered listing generator for Nigerian real estate agents. Built with Node.js, Express, SQLite, and Groq AI (Llama 3.3).

---

## Setup (5 minutes)

### 1. Install dependencies
```bash
npm install
```

### 2. Create your .env file
```bash
cp .env.example .env
```

Edit `.env` and fill in:
```
GROQ_API_KEY=gsk_your-key-here
JWT_SECRET=any-long-random-string-here
PORT=3000
ADMIN_EMAIL=your@email.com
ADMIN_PASSWORD=your-admin-password
ALLOWED_ORIGINS=http://localhost:3000
```

Get your Groq API key at: https://console.groq.com/keys

`JWT_SECRET` must be at least 32 characters long. You can generate one with:
```bash
node -e "console.log(require('crypto').randomBytes(32).toString('hex'))"
```

### 3. Run
```bash
npm start
```

Open http://localhost:3000

---

## How it works

- Users sign up → get free plan (5 generations/month)
- They use PropScribe → generates listing copy for all platforms
- When they hit limit → upgrade prompt shown
- You manually upgrade their plan via Admin panel
- They pay you via bank transfer / whatever works

---

## Plans & Pricing

| Plan     | Generations/month | Price      |
|----------|-------------------|------------|
| Free     | 5                 | ₦0         |
| Starter  | 50                | ₦5,000/mo  |
| Pro      | 200               | ₦12,000/mo |
| Agency   | 999               | ₦25,000/mo |

---

## Admin Panel

Log in with your ADMIN_EMAIL/ADMIN_PASSWORD.
You'll be redirected to the admin dashboard automatically.

From there you can:
- See all users and their usage
- Change any user's plan (when they pay)
- Track total generations this week

---

## Deploy to Production

### Cheapest option: Railway.app
1. Push code to GitHub
2. Connect repo on railway.app
3. Add environment variables (GROQ_API_KEY, JWT_SECRET, ADMIN_EMAIL, ADMIN_PASSWORD, ALLOWED_ORIGINS — set this to your live URL, e.g. `https://yourapp.up.railway.app`)
4. Deploy — Railway gives you a free URL

Note: the SQLite database file lives on the local filesystem. On Railway's free tier this isn't guaranteed to persist across redeploys — fine for a demo/class project, but if you need data to survive restarts, add a persistent volume or migrate to a hosted database later.

### Or: Render.com, Fly.io, DigitalOcean App Platform
All work the same way.

### Domain
Buy a .com.ng domain on Qservers.net (~₦3,000/year)
Point it to your Railway/Render URL.

---

## Cost to run

- Hosting: ~$0–5/month (Railway free tier works fine to start)
- Claude API: ~$0.01–0.03 per generation
- 100 users on Pro plan = ~₦1.2M revenue, ~₦15,000 in API costs

**Profit margin is enormous.**
