GIFTLIST WEBSITE — SETUP GUIDE
==============================

What is included
- index.html: responsive GiftList website (tablet/mobile/desktop)
- schema.sql: online database table + access security policies
- README.txt: these setup instructions

IMPORTANT
The website UI is built, but online accounts and shared access need a Supabase project and website hosting. This package cannot create accounts or deploy a public website on your behalf without access to your hosting/database accounts. Each person who signs up gets their own private gift records. Sharing the deployed website link lets others use the same app with their own accounts.

PART 1 — CREATE THE ONLINE DATABASE
1. Open https://supabase.com/ in your browser and create/sign in to an account.
2. Create a new project. Save the database password somewhere safe.
3. In your project, open SQL Editor > New query.
4. Open schema.sql from this package, copy all of it, paste it into the SQL Editor, and click Run.
5. Go to Project Settings > API (or Connect, depending on dashboard layout).
6. Copy the Project URL and the anon/public/publishable key. NEVER use a service_role or secret key in a website.

PART 2 — CONNECT THE WEBSITE
1. Open index.html in a code editor (you can use github.dev or an online editor).
2. Find these lines near the bottom:
   const SUPABASE_URL = "YOUR_SUPABASE_PROJECT_URL";
   const SUPABASE_ANON_KEY = "YOUR_SUPABASE_ANON_OR_PUBLISHABLE_KEY";
3. Replace the text inside each quote with your Supabase Project URL and anon/public/publishable key.
4. Save index.html.

PART 3 — PUT IT ONLINE SO YOU CAN SHARE A LINK
Option A: GitHub Pages
1. Sign in to GitHub and create a new repository, e.g. giftlist-website.
2. Upload index.html to the repository root. You may also upload README.txt and schema.sql.
3. Open repository Settings > Pages.
4. Choose Deploy from a branch, select the main branch and /(root), then Save.
5. Wait for GitHub to provide your website URL. Open it on your Android tablet and share that URL.
Note: GitHub Pages is static hosting; Supabase handles login and the database.

Option B: Netlify
1. Sign in to Netlify and create a new site by importing your GitHub repository, or deploy the site files through its supported upload flow.
2. Publish the site and copy the public URL.

PART 4 — ACCOUNT SETTINGS
- In Supabase Authentication settings, choose whether email confirmation is required.
- If confirmation is required, users need to confirm their email before logging in.
- Test Sign Up, Log In, Add Gift, Edit Gift, Delete Gift, search, and Log Out.
- Use a test account first. Do not put private or sensitive information into test records.

SECURITY / BEHAVIOR
- Each user can read, add, edit, and delete only their own gift records. Row Level Security policies in schema.sql enforce this in the database.
- Delete Gift asks for confirmation before deleting.
- Log Out asks for confirmation before signing out.
- Do not share your Supabase secret/service_role key.
- If you want a shared group wishlist where all invited users see and edit the same records, that is a different feature and needs group/owner permissions. This version gives every registered person their own private wishlist.

TROUBLESHOOTING
- "Setup required": the Supabase URL/key have not been entered in index.html.
- "Invalid API key" or connection error: recheck the Project URL and anon/public/publishable key.
- Login does not work: check Supabase Authentication settings and whether email confirmation is enabled.
- Database error: run schema.sql in the correct Supabase project and check the Table Editor for public.gifts.
