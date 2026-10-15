# MUCONNECT live pilot build

This package preserves the existing MUCONNECT interface and adds an initial Supabase-backed seller registration/listing flow.

## Included
- `index.html` — existing interface with Supabase JS client, email/password signup, business/product writes and shared live listing reads.
- `muconnect_live_setup.sql` — schema additions, Mulungushi and other campus seed records, profile signup trigger and pilot RLS policies.

## Setup steps
1. In Supabase, open **SQL Editor** and review/run `muconnect_live_setup.sql` in your existing project. It is written as an additive migration for the supplied starter schema; do not run if your tables differ without reviewing them.
2. In **Authentication → Providers**, enable Email. If email confirmation is enabled, sellers must click the confirmation email before the store submission can complete; they can then return and submit again.
3. In **Authentication → URL Configuration**, set the Site URL and allowed redirect URL to your Render URL (`https://mu-connect-k2rb.onrender.com`).
4. Replace the `index.html` in your GitHub repository with this one and commit it. Render should redeploy from the connected repository.
5. Test in a private/incognito browser: create a seller account, submit a business with a product, then open the marketplace on a second device/browser.

## Important limitations
- This is a first live pilot integration, not a claim that the current Render site has already changed. You must deploy these files and run the SQL.
- The UI's sample businesses remain as sample cards. The live businesses fetched from Supabase are labelled `LIVE LISTING`; sample cards are not real businesses.
- Image file inputs currently preview images only; logos/product photos are not uploaded to Supabase Storage yet. Text, contact, brand colours, products and prices are saved.
- A duplicate business with the same campus + slug is blocked by the database unique constraint. If a business already exists, the code tries to update the same-name business owned by the signed-in user.
- No orders, checkout, payments, verified reviews, points administration or secure founder console are enabled. Do not accept money through this prototype.
- The starter schema includes a commission default; no commission is charged or calculated by this frontend.
- Never place a service-role/secret key in frontend code. The provided publishable key is used as a browser client key; keep RLS enabled.
