# Snagzo Services - Netlify Deployment Guide 🚀

This repository is pre-configured to be deployed directly to **Netlify** with zero manual code modifications. The `netlify.toml` file automatically directs Netlify to host the high-fidelity web pages stored in the `app/src/main/assets` folder.

---

## ⚡ Deployment Methods

### Option A: Direct Git Deployment (Recommended)
1. **Push your code to GitHub**, GitLab, or Bitbucket.
2. Log in to [Netlify](https://www.netlify.com/).
3. Click **Add new site** > **Import an existing project** from your Git provider.
4. Select this repository.
5. Netlify will automatically detect the `netlify.toml` file from the root folder. You do not need to fill in any build command or publish directory.
6. Click **Deploy Snagzo**!

---

## 🛡️ Critical Firebase Configuration (For Authentication & Live Data)
Since the app uses Firebase (for Carts, Wishlists, Registering, SMS Verification, and Google Login), you must authorize your Netlify domain in the Firebase Console:

1. Copy your live Netlify URL (e.g., `https://your-app-name.netlify.app`).
2. Go to the [Firebase Console](https://console.firebase.google.com/).
3. Select your project.
4. Navigate to **Authentication** > **Settings** (Authorized Domains tab).
5. Click **Add Domain** and paste your Netlify URL (e.g. `your-app-name.netlify.app`).
6. Click **Save**.

Your Google Sign-In and Phone Verification systems will now function perfectly in production! 🎉
