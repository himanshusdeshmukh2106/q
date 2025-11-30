# Supabase Setup Instructions

## Step 1: Create Supabase Tables

Run these SQL commands in your Supabase SQL Editor:

### Waitlist Table
```sql
CREATE TABLE waitlist (
  id UUID DEFAULT gen_random_uuid() PRIMARY KEY,
  first_name TEXT NOT NULL,
  last_name TEXT,
  email TEXT NOT NULL UNIQUE,
  referral TEXT,
  created_at TIMESTAMP WITH TIME ZONE DEFAULT NOW()
);

-- Enable Row Level Security
ALTER TABLE waitlist ENABLE ROW LEVEL SECURITY;

-- Create policy to allow inserts from anonymous users
CREATE POLICY "Allow anonymous inserts" ON waitlist
  FOR INSERT
  WITH CHECK (true);
```

## Step 2: Get Your Supabase Credentials

1. Go to your Supabase project dashboard
2. Click on "Settings" (gear icon) in the sidebar
3. Click on "API" under Project Settings
4. Copy the following:
   - **Project URL** (looks like: `https://xxxxx.supabase.co`)
   - **anon public** key (under "Project API keys")

## Step 3: Create config.js

1. Copy `config.example.js` to `config.js`
2. Replace the placeholders with your actual credentials:

```javascript
export const SUPABASE_URL = 'https://xxxxx.supabase.co';
export const SUPABASE_ANON_KEY = 'your-actual-anon-key-here';
```

**Important:** `config.js` is in `.gitignore` so your credentials won't be committed to Git!

## Step 4: Deploy to Vercel

1. Push your code to GitHub
2. Import the repository in Vercel
3. Deploy!

No environment variables needed since we're using the anon key directly in the browser (which is safe for public operations like inserts).

## Testing

After setup:
1. Visit your waitlist page
2. Fill out the form
3. Check your Supabase dashboard → Table Editor → waitlist table
4. You should see the new entry!

## Security Notes

- The anon key is safe to expose in client-side code
- Row Level Security (RLS) policies control what operations are allowed
- We only allow INSERT operations from anonymous users
- Email field has UNIQUE constraint to prevent duplicate signups
