SAMAANZO FULL STARTER — SETUP GUIDE

Files:
1) index.html — responsive storefront with signup/login, seller application, approval UI,
   seller product upload/listing, cart, customer orders, COD checkout and admin view.
2) supabase_setup.sql — database tables and Row Level Security policies.

IMPORTANT LIMITATIONS / SECURITY:
- This is a working starter, not a production-certified marketplace.
- Online payment is intentionally NOT enabled. COD is the only checkout method.
  Razorpay requires a trusted backend/Edge Function and webhook signature verification.
- Never put Supabase service_role key or payment secret keys in index.html.
- Product images currently use public image URLs; configure Supabase Storage separately
  before accepting seller uploads of image files.
- Order item prices are captured in the browser in this starter. Before real sales,
  move order creation and price/stock validation into a Postgres RPC or Edge Function.

SETUP:
1. Open Supabase > SQL Editor and run supabase_setup.sql.
2. Open index.html in a text editor.
3. Replace PASTE_YOUR_SUPABASE_PROJECT_URL with Project URL from Supabase > Settings > API.
4. Replace PASTE_YOUR_SUPABASE_ANON_KEY with the anon/public key from Settings > API.
   Do NOT use service_role.
5. Save index.html and upload/commit it to the same Cloudflare Pages/GitHub project,
   replacing the old index.html. Keep the filename exactly index.html.
6. In Supabase Authentication settings, configure your site URL and allowed redirect URLs.
7. Create your own account through the website. Verify email if confirmation is enabled.
8. To grant admin access, use Supabase Dashboard > Authentication > Users, open your user,
   edit app_metadata (not user_metadata) and set {"role":"admin"}. Save, then log out/in.
   If the dashboard does not offer app_metadata editing, use a secure server-side admin
   process; never allow the browser to assign admin role.
9. Test with a separate customer account and seller account before public launch.

CURRENT FUNCTIONALITY:
- Customer email/password signup and login via Supabase Auth.
- Seller application defaults to pending; only admin can approve/reject.
- Approved sellers can create products.
- Product listing, search, category filter, cart, customer order history.
- Cash on Delivery order submission.
- Admin dashboard for seller applications and orders.

NOT INCLUDED YET:
- Razorpay/UPI/card payment, shipping integrations, refunds, coupons, tax invoices,
  seller payouts, product image upload UI, stock reservation, advanced order management.
