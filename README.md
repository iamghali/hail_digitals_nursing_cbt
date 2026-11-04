# HAIL DIGITALS Ghana Nursing CBT Practice Centre — V6 Commercial Test Build

This build adds candidate accounts, package checkout simulation, access-code redemption, server-side exam scoring and administration reports to the V5 project.

## IMPORTANT: TEST MODE ONLY
- The checkout screen is a simulator. It does **not** contact Paystack, Hubtel, a bank or Mobile Money provider.
- No real money is collected. A successful simulated transaction grants access; a declined simulated transaction does not.
- Do not publish this build for paid public use yet. Real payment-provider integration, production database, HTTPS deployment, privacy/terms review, stronger administrator authentication and security testing are still required.

## Run on Windows
1. Extract the ZIP file.
2. Open the extracted `NMC 5` folder.
3. Click the File Explorer address bar, type `cmd`, and press Enter.
4. Run `npm install` (once) and then `npm start`.
5. Open `http://localhost:3000` in your browser.
6. Admin page: `http://localhost:3000/admin.html`.

Keep the command window open while using the site. Press Ctrl+C to stop the server.

## Candidate test workflow
1. Create an account using an email address and a password of at least 8 characters.
2. Choose one of the clearly labelled TEST MODE packages and click **Test purchase**. This simulates a successful payment and grants access; no charge is made.
3. Start a practice or mock examination. The server checks access and consumes one examination credit for single-exam packages. Time subscriptions permit multiple examinations until expiry.
4. Submit the examination. Correct answers and scoring are held server-side; the browser does not receive the answer key.
5. Sign out and sign in again to verify the account persists. Login sessions reset when the server restarts.

## Test access codes
- Sign in to `/admin.html` using the development admin key `change-this-admin-key` on a local test machine.
- Generate codes for a package and copy one.
- Sign in as a candidate and redeem it in the candidate access panel.
- A code can be redeemed once only. Codes are linked to the candidate account.

## Data files
The `data` folder stores questions, attempts, users, payment test records and access codes as JSON. Back up this folder. This simple JSON storage is intended for local testing, not concurrent production use.

## Environment variables
- `PORT` — server port (default 3000)
- `ADMIN_KEY` — administrator key (must be replaced before any deployment)

## Before production launch
Integrate a real provider (for example Paystack or Hubtel) using server-side transaction initialization and verified signed webhooks; never trust a browser success redirect. Move data to a managed database, use secure sessions/cookies, rate limiting, CSRF protections, password reset, audit logs, backups, HTTPS, and a properly protected administrator login. Review applicable Ghana data-protection and consumer requirements.
