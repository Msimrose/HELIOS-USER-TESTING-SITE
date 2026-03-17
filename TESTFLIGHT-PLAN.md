# Helios — TestFlight Testing Plan

## Overview

This document outlines how to set up, distribute, and run remote user testing for the Helios app via Apple TestFlight. Share this with anyone helping coordinate testing.

---

## For You (Setting Up TestFlight)

### 1. Create a Testing Branch in Xcode

```bash
# Navigate to your Helios Xcode project directory
cd ~/path-to/Helios

# Create and switch to a testing branch
git checkout -b testflight/user-testing-v1

# Push the branch
git push -u origin testflight/user-testing-v1
```

**Why a separate branch?** This isolates your testing build from ongoing development. Any quick fixes for testers go here without affecting your main branch.

### 2. Archive & Upload to App Store Connect

1. In Xcode, select **Product → Archive** (make sure you're targeting "Any iOS Device")
2. Once archived, click **Distribute App → App Store Connect → Upload**
3. Wait for the build to process in App Store Connect (usually 10–30 minutes)
4. You'll get an email when it's ready

### 3. Set Up TestFlight in App Store Connect

1. Go to [appstoreconnect.apple.com](https://appstoreconnect.apple.com) → **My Apps** → **Helios**
2. Click the **TestFlight** tab
3. Under the new build, add **Test Information**:
   - What to test: "Please follow the guided testing link provided to you. It includes consent, tasks, and a feedback questionnaire."
   - App description, feedback email (micahsimrose@gmail.com)

### 4. Create an External Testing Group

For distributing to people outside your dev team:

1. In TestFlight tab → **External Testing** → click **+** to create a group
2. Name it: **Helios User Testing — March 2026**
3. Add the build to this group
4. **Enable Public Link** — this generates a shareable URL anyone can use to join
5. Copy the public link — this is your TestFlight invite link

> **The public link is easiest.** Anyone with an iPhone can tap it, install TestFlight if needed, and get your app. No need to collect Apple IDs.

### 5. Distribute

Share with testers:
- The **TestFlight public link** (for app install)
- The **testing flow page link** (your hosted HTML page — for consent + questionnaire)

---

## For Testers (Send This Section)

### What You Need
- An iPhone running iOS 16 or later
- About 15 minutes

### Steps

1. **Open the testing link** I sent you (the webpage, not the app link)
2. The page will guide you through everything in order:
   - ✅ Read and sign the consent form
   - 📲 Install the Helios app via TestFlight
   - 🧪 Complete 5 quick testing tasks in the app
   - 📝 Fill out the feedback questionnaire
   - ✉️ Submit your responses
3. That's it! Everything is on one page, in order.

---

## Hosting the Testing Flow Page

The `helios-testing-flow.html` file needs to be hosted online so testers can access it. Here are your quickest free options:

### Option A: GitHub Pages (Recommended)
1. Push the HTML file to a GitHub repo
2. Go to repo **Settings → Pages** → enable from main branch
3. Your page will be live at `https://yourusername.github.io/repo-name/helios-testing-flow.html`

### Option B: Netlify Drop
1. Go to [app.netlify.com/drop](https://app.netlify.com/drop)
2. Drag the HTML file onto the page
3. Get an instant live URL

### Option C: Vercel
1. Create a free Vercel account
2. Drag and deploy the file
3. Get a live URL

---

## Data Collection

When testers submit the questionnaire, two things happen:

1. A **JSON file downloads** to their device with all their responses
2. They see an option to **email the responses** directly to you

For collecting the JSON files: ask testers to share them with you via iMessage, email, or AirDrop. Each file is named with a timestamp so you can track them.

---

## Timeline (Today)

| Time | Action |
|------|--------|
| Now | Create testing branch, archive & upload build |
| +30 min | Build processes in App Store Connect |
| +45 min | Set up TestFlight group, enable public link |
| +1 hr | Host the HTML testing page |
| +1 hr | Share Instagram story + links with testers |
| +1–2 hrs | Responses start coming in |

---

## Quick Troubleshooting

**"I can't install from TestFlight"** → Make sure they're on iOS 16+. If the public link doesn't work, add their Apple ID email manually in App Store Connect.

**"The app crashes on launch"** → Check your build target in Xcode. Make sure minimum deployment target matches your testers' iOS versions.

**"Build stuck processing"** → Normal if it's your first upload. Can take up to an hour. Check App Store Connect for status.
