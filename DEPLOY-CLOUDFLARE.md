# Snagzo Services - Cloudflare Pages Deployment Guide ⚡

This project is pre-configured to be deployed directly on **Cloudflare Pages** with optimal static asset performance.

---

## 🇧🇩 বাংলা নির্দেশাবলী (Bengali Instructions)

আপনার Snagzo ওয়েবসাইটটি Netlify এর বদলে **Cloudflare Pages** এ হোস্ট করার জন্য নিচের সহজ পদ্ধতিগুলো অনুসরণ করুন:

### পদ্ধতি ১: গিটহাব ইন্টিগ্রেশন (সবচেয়ে সহজ এবং রেকমেন্ডেড)

1. প্রথমত, এই কোডটি আপনার **GitHub** বা অন্য কোনো গিটের রিপোজিটরিতে পুশ (Push) করুন।
2. আপনার [Cloudflare Dashboard](https://dash.cloudflare.com/)-এ লগইন করুন।
3. বামদিকের সাইডবার থেকে **Workers & Pages** এ যান এবং **Create** বাটনে ক্লিক করুন।
4. **Pages** ট্যাবটি সিলেক্ট করে **Connect to Git** বাটনে ক্লিক করুন এবং আপনার GitHub অ্যাকাউন্ট কানেক্ট করে আপনার রিপোজিটরি সিলেক্ট করুন।
5. **Set up builds and deployments** পেজে সেটিংসগুলো এভাবে কনফিগার করুন:
   - **Project Name:** `snagzo` (অথবা আপনার পছন্দমতো)
   - **Production branch:** `main` (অথবা আপনার ডিফল্ট ব্রাঞ্চ)
   - **Framework preset:** `None` (যেহেতু এটি একটি প্লেইন স্ট্যাটিক সাইট)
   - **Build command:** *খালি রাখুন (কিছু লেখার প্রয়োজন নেই)*
   - **Build output directory:** `app/src/main/assets` (এটি সবচেয়ে গুরুত্বপূর্ণ! এই ডিরেক্টরি থেকেই ক্লাউডফ্লেয়ার ফাইলগুলো দেখাবে)
6. **Save and Deploy** বাটনে ক্লিক করুন! আপনার সাইট ১-২ মিনিটের মধ্যে লাইভ হয়ে যাবে।

---

### পদ্ধতি ২: Wrangler CLI এর মাধ্যমে ডিরেক্ট ডেপ্লয়

আপনি যদি কোনো গিটহাব রিপোজিটরি ছাড়া সরাসরি আপনার লোকাল পিসি থেকে ডেপ্লয় করতে চান:

1. আপনার কুয়েরি টার্মিনাল বা কমান্ড প্রম্পটে নুড প্যাকেজ ম্যানেজার (`npm`) এর সাহায্যে নিচের কমান্ডটি রান করুন:
   ```bash
   npx wrangler pages deploy app/src/main/assets --project-name snagzo
   ```
2. স্ক্রিনে আসা নির্দেশাবলী অনুসরণ করে আপনার ক্লাউডফ্লেয়ার অ্যাকাউন্টে লগইন অথোরাইজেশন করুন।
3. ব্যস! ক্লাউডফ্লেয়ার সরাসরি আপনার ডিরেক্টরি আপলোড করে লাইভ লিঙ্ক জেনারেট করে দেবে।

---

## 🇬🇧 English Instructions

Follow these simple steps to deploy your Snagzo web assets to **Cloudflare Pages**:

### Method 1: Git Integration (Recommended)

1. **Push your code to GitHub** (or GitLab/Bitbucket).
2. Log in to your [Cloudflare Dashboard](https://dash.cloudflare.com/).
3. Navigate to **Workers & Pages** > **Create** > **Pages** (Connect to Git).
4. Authorize your account and select this repository.
5. In the **Build configuration** page, specify the following parameters:
   - **Framework preset:** `None`
   - **Build command:** *Leave this empty*
   - **Build output directory:** `app/src/main/assets`
6. Click **Save and Deploy**!

---

### Method 2: Direct local deployment via Wrangler CLI

If you wish to deploy directly from your local system without setting up Git hooks:

1. Run the following command in your terminal:
   ```bash
   npx wrangler pages deploy app/src/main/assets --project-name snagzo
   ```
2. Authenticate using your web browser, and Cloudflare will instantly publish the files.

---

## 🛡️ Critical Firebase Domain Authorization (অবশ্যই করতে হবে!)
যেহেতু Snagzo ওয়েবসাইটটি Firebase অথেন্টিকেশন (Google Login, Phone Number OTP Verification, Real-Time Database Sync) ব্যবহার করে, তাই নতুন ক্লাউডফ্লেয়ার ডোমিনটিকে আপনার Firebase কনসোলে অথোরাইজ করতে হবে:

1. আপনার সাকসেসফুল ডেপ্লয়মেন্টের পর ক্লাউডফ্লেয়ার একটি লাইভ লিঙ্ক দেবে (যেমন: `https://snagzo.pages.dev`).
2. [Firebase Console](https://console.firebase.google.com/)-এ যান।
3. আপনার প্রোজেক্টটি ওপেন করুন এবং **Authentication** > **Settings** (Authorized Domains ট্যাব) এ যান।
4. **Add Domain** ক্লিক করে আপনার নতুন ক্লাউডফ্লেয়ার ডোমেইনটি যুক্ত করুন (যেমন: `snagzo.pages.dev`).
5. **Save** এ ক্লিক করুন।

আপনার কাস্টম কুপন সিস্টেম, ডেলিভারি কন্ট্রোল টাওয়ার, ও লাইভ পেমেন্ট গেটওয়ে সমস্ত ডিভাইসে নিরবচ্ছিন্নভাবে লাইভ কাজ করবে! 🎉
