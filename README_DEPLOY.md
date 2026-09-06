# Binatna Shop — Final deployment package

This version is prepared to use **Supabase** as the production backend and database.

## What is now ready
- Public storefront (`index.html`).
- Private admin dashboard (`admin-panel.html`).
- Central product catalog in PostgreSQL.
- Central orders database.
- Atomic order creation with stock validation/decrement.
- Admin email/password authentication through Supabase Auth.
- Row Level Security: public can read active products; only registered admins can manage products/orders.
- Initial six products seeded by `supabase/schema.sql`.
- Customer cart/favorites remain local to each customer's device.

## One-time connection steps
1. Create a Supabase project.
2. Open SQL Editor and run **all** of `supabase/schema.sql`.
3. In Supabase Authentication, create an admin user with email/password.
4. Copy that user's UUID.
5. In SQL Editor run:
   `insert into public.admins(user_id) values ('YOUR-ADMIN-UUID');`
6. Open Project Settings → API and copy the Project URL and anon/publishable key.
7. Put them in `supabase-config.js`:
   - `BINATNA_SUPABASE_URL`
   - `BINATNA_SUPABASE_ANON_KEY`
8. Upload the folder to a static host (Netlify, Cloudflare Pages, or another static host).
9. Open `admin-panel.html` and sign in with the Supabase admin user.

## Important
Do NOT put the Supabase `service_role` key in this website. Only use the browser-safe anon/publishable key with the RLS policies from the SQL file.
