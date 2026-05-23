# Firebase Setup Guide - Dashboard Cloud Sync

Your dashboard now supports **real-time cloud sync** across devices! Follow these steps to enable it.

## Quick Setup (5 minutes)

### 1. Create Firebase Project
- Go to [Firebase Console](https://console.firebase.google.com)
- Click **"Add Project"** 
- Name it anything (e.g., "dashboard-sync")
- Click **Create Project**
- Wait for it to finish, then click **Continue**

### 2. Create Realtime Database
- In the left menu, click **"Realtime Database"**
- Click **"Create Database"**
- Choose **Start in test mode** (for easy setup)
- Choose a region close to you
- Click **Enable**

### 3. Get Your Config
- Click the **⚙️ Settings icon** (top-left, next to Project Overview)
- Select **Project Settings**
- Scroll to **"Your apps"** section
- Click **"Add app"** → **"Web"** (icon: `</>`
- Give it a name, click **"Register app"**
- Copy the config that appears in the `firebaseConfig` object

### 4. Update Your Dashboard
- Edit `dashboard.html` and find these lines (around line 970):
```javascript
const firebaseConfig = {
  apiKey: "AIzaSyBd_JvJ0q1K4_0_r8_H5xQ_0kHJR5UvG9A",
  authDomain: "dashboard-goals-sync.firebaseapp.com",
  databaseURL: "https://dashboard-goals-sync-default-rtdb.firebaseio.com",
  projectId: "dashboard-goals-sync",
  storageBucket: "dashboard-goals-sync.firebasestorage.app",
  messagingSenderId: "123456789012",
  appId: "1:123456789012:web:abcdef1234567890"
};
```

- Replace with YOUR config from step 3
- Save and redeploy to Vercel

### 5. Set Database Rules (Security)
- In Firebase Console, go to **Realtime Database**
- Click **"Rules"** tab
- Replace with:
```json
{
  "rules": {
    ".read": true,
    ".write": true
  }
}
```
- Click **Publish**

⚠️ **Warning:** This allows anyone to read/write. It's fine for personal use.

## That's It!

Now your dashboard will:
✅ Sync goals in real-time across PC, phone, tablet  
✅ Maintain local copy for offline access  
✅ Auto-sync when you open the app on any device  

When you add/check/delete a goal on your phone, it **instantly appears on your PC**!

## Troubleshooting

**"Firebase write failed" in console?**
- Check the config is correct
- Make sure database rules allow writes
- Check your internet connection

**Data not syncing?**
- Refresh the page
- Check browser console (F12) for errors
- Make sure both devices are connected to internet

**Want to reset all data?**
- In Firebase Console → Realtime Database → Click data → Delete all

