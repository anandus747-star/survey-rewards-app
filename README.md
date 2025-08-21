
# Survey Rewards App (Custom, Subdomain-ready)

A minimal full-stack app for email-verified survey submissions, reward point calculation (points = questions answered), unique reward code generation, automated email notifications, and a simple redeem page for hospital staff.

## Quick Start (Local)

1) Install Node.js 18+
2) Unzip this project and open a terminal in the folder
3) Copy env and install deps:
   ```bash
   cp .env.example .env
   npm install
   ```
4) (Recommended) Start MailHog to capture emails locally:
   ```bash
   docker compose up -d mailhog
   ```
   Then open http://localhost:8025 to see emails.
5) Start the app:
   ```bash
   npm start
   ```
6) Open http://localhost:3000 and test the flow:
   - Enter an email on the home page
   - Click the verification link from MailHog
   - Fill the survey (any answers)
   - See the thank-you page and the code
   - Try redeeming the code on /redeem

## Deploying to a Subdomain

- Point `survey.clientdomain.com` to your server.
- Set `APP_BASE_URL=https://survey.clientdomain.com` in `.env`.
- Use a real SMTP provider (update SMTP_* env vars).
- Run the app with a process manager or container (Dockerfile included).

## Notes

- One submission per email is enforced.
- Questions are defined in `src/routes/survey.js` (QUESTIONS array).
- Rewards and answers are stored in SQLite (`DATABASE_FILE`).

MIT License
