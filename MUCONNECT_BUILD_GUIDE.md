# MUCONNECT — Pilot Build Pack

This pack contains the current front-end prototype and a starter Supabase schema.

## Important status
The HTML prototype is not a live multi-user platform. Seller records, feedback, reviews and points previews are browser-local demo data. The SQL establishes a database foundation but does not implement the complete backend, payment provider, notifications or production authentication flow.

## Recommended fast path
1. Create a Supabase project and run `muconnect_supabase_schema.sql` in a **test project first** after review.
2. Add the initial university record(s) to `public.universities`.
3. Configure Supabase Auth and email templates.
4. Configure Storage buckets and access policies for business logos and product photos.
5. Test policies with separate buyer, seller, university-admin and founder accounts.
6. Integrate the HTML with Supabase Auth, approved business/product queries, seller-owned CRUD and Storage uploads.
7. Implement trusted Edge Functions for order creation, stock reservation, commission calculations, payment-provider webhook verification, refunds and points awards.
8. Pilot with 5–10 invited sellers at Mulungushi University before wider launch.

## Security rules
- Never put the Supabase `service_role` key in browser code.
- A hidden button or client-side passphrase is not authentication.
- Founder/admin privileges must be assigned through a trusted process.
- Payment success must be confirmed by a verified server-side provider webhook, not a browser click.
- Do not let the browser write its own points awards or payment status.

## Before accepting real orders
- Choose a payment provider that supports your business and Zambia.
- Agree seller commission terms in writing.
- Publish privacy, customer and seller terms and a support contact.
- Test failed payments, duplicate callbacks, stock conflicts, refunds and cancellations.
- Test mobile usability on slower connections.

This is a development starter, not a claim that production accounts or live payments are already connected.
