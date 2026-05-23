# Alternative: Simple Sync Without Firebase

If you prefer not to set up Firebase, here's an even simpler solution:

## Option A: Share Data File (Easiest)

1. **Export on PC:**
   - Open browser console (F12)
   - Paste this and press Enter:
   ```javascript
   console.save(JSON.stringify(localStorage, null, 2), 'dashboard-backup.json')
   ```
   - Or manually copy this:
   ```javascript
   Object.keys(localStorage)
     .filter(k => k.startsWith('goals:'))
     .map(k => ({ [k]: JSON.parse(localStorage[k]) }))
     .reduce((a,b) => ({...a, ...b}), {})
   ```

2. **Upload backup to Vercel or cloud storage**

3. **On Phone:**
   - Download the backup file
   - Open console on phone
   - Paste into localStorage

**Downside:** Manual sync required

## Option B: Use Supabase (Like Firebase, but easier)

If Firebase feels like too much setup, try Supabase instead:

```javascript
// It's nearly identical to Firebase but might be simpler
const { createClient } = supabase
const supabase = createClient(url, key)
```

1. Go to [supabase.com](https://supabase.com)
2. Create account → new project
3. Get credentials and swap them in
4. Same concept as Firebase

## Recommendation

**Firebase is actually the quickest:** Just 5 minutes to set up, then you're done forever. No more manual syncing needed.

Pick Option 1 (Firebase) unless you have a strong preference for something else!

