# Free Fire Esports Manager — Render + Supabase

This version is adapted to use Supabase PostgreSQL instead of the local SQLite `team.db`.

## 1. Supabase connection string
In Supabase, open **Connect** and copy the PostgreSQL URI. Do not publish it or commit it to GitHub. The URI usually resembles:
`postgresql://postgres:[YOUR-PASSWORD]@db.[PROJECT-REF].supabase.co:5432/postgres`
Use the exact URI supplied by Supabase; if your project requires the pooler, use the provided pooler URI and port.

## 2. Deploy to Render
1. Upload this project folder to a private GitHub repository.
2. In Render, choose **New > Web Service** and connect that repository.
3. Build command: `pip install -r requirements.txt`
4. Start command: `gunicorn app:app`
5. Add environment variables:
   - `DATABASE_URL` = your Supabase PostgreSQL URI
   - `SECRET_KEY` = a long random secret (Render can generate one)
   - `SEED_DEMO_USERS` = `1` only if you want the demo accounts created on an empty database.
6. Deploy and check Render logs.

`render.yaml` is also included as a Blueprint starting point; confirm its environment variables in Render before deploying.

## 3. First login
On a completely empty database, if `SEED_DEMO_USERS=1`, initial accounts are:
- Admin username: `admin`, password: `Admin123!`
- Player username: `player1`, password: `Player123!`

**Immediately change/remove demo credentials before sharing the site publicly.** This version does not yet provide an in-app password-change flow. If the database already has users, demo accounts are not added.

## Important limitations
- Profile images are still saved to the app's local `static/uploads` folder. Render's free filesystem is ephemeral, so images may disappear after a restart/redeploy. To make images durable, move uploads to Supabase Storage.
- Supabase Free projects may pause after a period of inactivity. Check current Supabase plan limits.
- This adaptation has not been tested against your live Supabase project because no database credentials were provided. Never send your database password or full connection URI in chat.
- Existing data inside your old `team.db` is not automatically imported. This version creates tables in Supabase; old data migration is a separate step.
