# VidioCraft AI — Complete Starter

Includes:
- Flutter Android/iOS app
- Registration + secure password hashing
- JWT login/session
- AI video generation endpoint with mock mode and generic provider adapter
- Credits wallet + automatic deduction/refund on provider failure
- Paystack initialization + verification
- My Videos
- Admin API + static Admin panel
- Prisma + SQLite for easy local development

## Run backend
cd backend
cp .env.example .env
npm install
npx prisma generate
npx prisma db push
node src/create-admin.js
npm start

Admin defaults come from `.env`: admin@vidiocraft.local / ChangeMe123! — change these before use.

## Run mobile
cd mobile
flutter pub get
flutter run

Android emulator uses `http://10.0.2.2:4000/api`. For a physical phone, change `Api.base` to your computer's LAN IP.

## AI provider
Set `AI_PROVIDER` to something other than `mock`, and configure `AI_PROVIDER_URL` and `AI_PROVIDER_KEY`. The adapter expects a JSON response containing an id and optionally a video URL. For production, adapt it to your provider's async job/status API.

## Paystack
Set `PAYSTACK_SECRET_KEY` and a public HTTPS callback/webhook flow for production. Never put the secret key in Flutter. Amounts are currently calculated as 1000 kobo per credit (₦10/credit); change the formula to your pricing.

## Production checklist
Use PostgreSQL, HTTPS, Paystack webhook signature verification, rate limiting, stronger request validation, secure admin setup, cloud video storage/CDN, async job queue, and a provider-specific AI adapter.
