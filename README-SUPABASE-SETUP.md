# Makarios & Maival wedding invitation — updated

## Changes
- Updated the ceremony time from 6 PM to **4 PM** in the invitation and countdown.
- Added **Archangel Michael Church, Sheraton** to the church ticket.
- Reworked guest wishes to use a shared Supabase table, so wishes can be saved centrally and opened after the wedding instead of being stored only in each guest's browser.

## Required setup for shared wishes
The shared wish book will not work until you connect a Supabase project.

1. Create a project at https://supabase.com/
2. Open **SQL Editor** in the Supabase dashboard.
3. Open `supabase-wishes-setup.sql`, copy its contents into a new SQL query, and run it.
4. In Supabase, open **Project Settings → API** (or **Data API**, depending on dashboard layout).
5. Copy the **Project URL** and the **anon/public key**.
6. In `index.html`, find:
   - `PASTE_SUPABASE_PROJECT_URL_HERE`
   - `PASTE_SUPABASE_ANON_KEY_HERE`
7. Replace them with your Project URL and anon/public key.
8. Save, then run:
   ```bash
   git add .
   git commit -m "Connect shared guest wishes and update wedding time"
   git push origin main
   ```
9. Vercel should redeploy automatically after the GitHub push.

## Security note
Only use the Supabase **anon/public** key in `index.html`. Never put the `service_role` key in a public website. The SQL policy allows submissions before the wedding and allows reading message contents only after 7 Nov 2026 at 4:00 PM Egypt time (UTC+02:00).

## Important
Test by submitting a wish from one device/browser and opening the site on another. Before the wedding, the public page should not reveal the message contents. After the wedding time, it should load and show the saved messages.
