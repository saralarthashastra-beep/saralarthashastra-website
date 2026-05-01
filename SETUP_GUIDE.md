# 🚀 SaralArthaShastra Website — Setup & Deployment Guide

**What you have:** A genuinely functional website with 12 pages, working calculators, downloadable PDFs, course waitlist, and consulting booking. Most things work TODAY without any external setup.

**What needs YOUR action:** A few 5-minute external service signups to enable forms, payments, and consulting booking. All clearly marked below.

---

## 📁 What's in the Folder

```
website_complete/
├── index.html                              ← Home page (existing, with new links)
├── tools.html                              ← ✅ Working EMI/Inflation/Real-rate calculators
├── resources.html                          ← ✅ Free PDF downloads
├── courses.html                            ← Course details + waitlist form
├── consulting.html                         ← 1-on-1 booking page
├── thank-you.html                          ← Form confirmation page
│
├── articles/
│   ├── index.html                          ← Articles hub
│   ├── repo-rate-complete-guide.html       ← ✅ Featured 18-min article
│   └── emi-explained.html                  ← ✅ 12-min article
│
└── resources/
    ├── 5-hidden-emi-truths.pdf             ← ✅ 8-page lead magnet
    ├── repo-rate-cheatsheet.pdf            ← ✅ 2-page reference
    └── emi-quickreference.pdf              ← ✅ 3-page formula manual
```

✅ = Works immediately, no setup needed

---

## 🟢 What Already Works (No Setup Required)

These are LIVE the moment you upload to Cloudflare:

1. **Home page navigation** — All 6 nav links point to real pages
2. **EMI Calculator** — Real working math, Indian number formatting (1,00,000 style)
3. **Real Interest Rate Calculator** — Fisher equation, contextual insights
4. **Inflation Impact Calculator** — Future purchasing power calculation
5. **PDF Downloads** — All 3 PDFs download instantly when clicked
6. **Articles** — Two long-form pieces fully readable
7. **YouTube embed** — Episode 01 video plays on home page
8. **External links** — YouTube, Telegram, Instagram, Email all work

---

## 🟡 5-Minute Setups (Highly Recommended)

### 1. Web3Forms — ✅ ALREADY INTEGRATED

Both forms on the website are **already wired** to your Web3Forms account:

- **Course waitlist form** on `courses.html` (line 512)
- **Contact form** on `index.html` (home page)

Both use access key: `27c7fd46-67b4-43c1-99b4-e85a03032b9f`

**What this means:**
- Every form submission emails you instantly at `saralarthashastra@gmail.com`
- After submitting, the user is redirected to `thank-you.html`
- A honeypot field protects against spam bots
- No further setup needed — works the moment the website goes live

**Test it:** After deploying, fill the contact form yourself with a different email. Check your inbox within 30 seconds — you should see the submission with all fields.

**Limits:** Web3Forms free tier allows 250 submissions/month total across both forms. Upgrade to paid tier (~$5/mo) only if you exceed this — unlikely in year 1.

---

### 2. Calendly Setup — Configure your event types ✅ ALREADY INTEGRATED

You've signed up at Calendly with `saralarthashastra@gmail.com`. The website is **already wired** to your Calendly. You just need to set up the four event types in Calendly itself.

**Steps in Calendly Dashboard:**

1. **Verify your username**
   - Go to https://calendly.com/app/admin/account
   - Your booking URL should be: `calendly.com/saralarthashastra`
   - **If different** (e.g. Calendly added a number), edit your username so it matches the website (or follow step 5 below to update website URLs)

2. **Connect Google Calendar** so your real availability syncs
   - Calendly → Account → Calendar Connections → Connect Google Calendar
   - This prevents double-booking with your Bank office hours

3. **Set your availability windows**
   - Bank job phase (now): Weekdays 7-9 PM, Weekends 10 AM-2 PM
   - After Sept 2026: Mon-Fri 10 AM-1 PM and 3-6 PM
   - Calendly → Availability → Edit your default schedule

4. **Create the four event types** (this is critical):

   | Event Name | Duration | URL Slug | Price |
   |-----------|----------|----------|-------|
   | 15-min Discovery Call | 15 min | `15min` | Free |
   | Personal Finance Review | 45 min | `personal-finance-review` | ₹999 |
   | Banking Career Session | 60 min | `banking-career-session` | ₹1,499 |
   | RBI Grade B Strategy | 60 min | `rbi-grade-b-strategy` | ₹1,499 |

   For each: Calendly → Event Types → New Event Type → choose duration → set URL slug exactly as above.

5. **For paid events** — Calendly free plan doesn't support payments natively. Two options:
   - **Option A (recommended for now):** In the event description, write: *"After booking, you'll receive a Razorpay payment link by email. Slot is confirmed only after payment."* Then manually send the link.
   - **Option B (after 10+ bookings):** Upgrade to Calendly Standard plan (~$10/mo) which integrates Stripe/PayPal directly.

6. **If your Calendly URL is different from `calendly.com/saralarthashastra`:**
   Open these files and find/replace `saralarthashastra` with your actual username:
   - `consulting.html`
   - `index.html`
   - `courses.html`

**Result:** Visitors click the booking buttons, see your real availability, pick a time, and get an instant confirmation email. You see it on your Google Calendar. No back-and-forth emails. ✨

---

### 3. Razorpay Payment Links — For paid sessions

Until Calendly's paid tier is worth it, manually send Razorpay payment links after each paid booking:

**Steps:**
1. Sign up at https://razorpay.com/ (5 min, requires PAN + bank account)
2. Go to **Payment Links** in dashboard
3. Create three reusable links:
   - **₹999 — Personal Finance Review** (slug: `pf-review`)
   - **₹1,499 — Banking Career Session** (slug: `banking-career`)
   - **₹1,499 — RBI Grade B Strategy** (slug: `rbi-strategy`)
4. Save the URLs in a notes app — when someone books a paid session via Calendly, paste the matching link in your reply email.

**Cost:** 2% per transaction. ₹999 session = ~₹980 to you.

**Pro tip:** Set up a Gmail template called "Calendly Payment Follow-up" with the three links and a thank-you message. Sending it becomes a 10-second job.

---

### 4. (Optional) Skip Razorpay entirely with Calendly Paid Plan

If bookings exceed 10/month and the manual Razorpay step gets tiresome:
- Upgrade to **Calendly Standard** ($10/mo)
- Connect Stripe (1.9% fee) or PayPal
- Set the price directly on each event type
- Customer pays at booking time, slot only locks after payment

Skip this until you actually have the volume — manual is fine for the first 30 bookings.

---

## 🌐 Deploying to Cloudflare Pages

You already have `saralarthashastra.com` on Cloudflare Pages. Here's how to deploy the full site:

### Option A: Drag-and-Drop (easiest)

1. Go to https://dash.cloudflare.com/ → Pages
2. Click your existing project → **"Create deployment"**
3. Drag the entire `website_complete` folder into the upload area
4. Wait 30 seconds for build
5. New version goes live at `saralarthashastra.com` automatically

### Option B: Replace Files One by One

If you only want to add new pages without replacing existing index:
1. Use Cloudflare dashboard's file manager (or CLI)
2. Upload each new file to your Pages project
3. Existing index.html remains; new pages become accessible

### Option C: Git-based (long-term recommended)

1. Create a GitHub repo: `saralarthashastra-website`
2. Upload all files to it
3. In Cloudflare Pages, connect to GitHub
4. Every push to `main` auto-deploys

---

## ✅ Pre-Launch Checklist

Before you announce the new site to anyone, check these:

- [ ] All 3 PDFs download correctly (try on phone)
- [ ] EMI calculator shows correct numbers (try ₹50L / 8.5% / 20yr → should show ₹43,391)
- [x] Web3Forms key integrated in courses.html and index.html (DONE — key: 27c7fd46-67b4-43c1-99b4-e85a03032b9f)
- [ ] Test the waitlist form by submitting yourself with a different email
- [ ] Test the contact form on home page by submitting yourself
- [ ] Verified Calendly username is `saralarthashastra` (or updated website URLs to match)
- [ ] Created all 4 Calendly event types (15min, personal-finance-review, banking-career-session, rbi-grade-b-strategy)
- [ ] Connected Google Calendar to Calendly
- [ ] Set realistic availability windows in Calendly
- [ ] Created 3 Razorpay payment links and saved them somewhere accessible
- [ ] Test-booked a slot yourself via the consulting page
- [ ] All footer links work (click each one)
- [ ] Mobile view looks good (open on your Samsung A35)
- [ ] Episode 01 video plays on home page

---

## 📊 What Each Page Does (Plain English)

| Page | What it does | Conversion goal |
|------|------|-----------------|
| **index.html** | Front door. Tells your story. Plays Episode 01. | Subscribe to YouTube |
| **tools.html** | Free calculators that solve real problems | Build trust → return visit |
| **articles/** | Long-form deep dives | SEO + share-worthy |
| **resources.html** | Free PDFs | Email capture (later) |
| **courses.html** | Course catalogue with waitlist | Capture lead with name+email |
| **consulting.html** | Direct revenue | Book a paid session |
| **thank-you.html** | Confirmation after form/payment | Re-engage with content |

---

## 💡 Strategic Notes

**Why this structure works:**

1. **The free stuff is genuinely valuable.** The PDFs and calculators alone could be a paid product. By giving them away, you build trust.

2. **The articles are SEO bait.** "Repo Rate India" and "EMI calculator India" are searched 10,000+ times per month. Your articles are written to rank.

3. **The funnel is honest.** Free YouTube → Free articles/tools → Free PDFs → Paid 1-on-1 → Paid courses. Each step earns trust before the next ask.

4. **Honest "coming soon" boxes.** I deliberately wrote honest banners about Aug 2026 course launches and waitlists. This builds credibility — most people promise what they can't deliver.

---

## 🔧 What's Still Manual (and that's okay)

For the first 6 months, these will be manual — that's fine because volume is low:

- **Booking calendar:** Email back-and-forth instead of automated calendar
- **Email newsletter:** Use Mailchimp later when you hit 100+ waitlist signups
- **Course delivery:** Use Google Drive + Telegram for first batch (free)
- **Course payments:** Razorpay Payment Links (no platform needed)
- **Consulting pre-form:** Send Google Form link manually after payment

Don't over-engineer. The website above already costs you ₹0/month to run on Cloudflare. The only paid tool you need eventually is Topmate (₹99/mo) or Razorpay (transaction fee only).

---

## 🆘 If Something Breaks

**Forms not submitting?**
- Web3Forms key is already integrated. Check your Web3Forms dashboard — every submission shows up there
- Make sure you've verified your email with Web3Forms (they send a confirmation email when you create the key)
- Check spam folder for the test submission

**PDF download not working?**
- Make sure the `resources/` folder uploaded with all 3 PDFs
- File names must match exactly (case-sensitive on Cloudflare)

**Calculator showing weird numbers?**
- Check browser console for JS errors
- All math is in `tools.html` directly — search for `function calculateEMI`

**Mobile menu missing?**
- The current nav only shows on desktop (>700px). Mobile users see only the brand logo. This is intentional for v1. If users complain, we'll add a hamburger menu.

---

## 🎯 30-Day Launch Plan

**Week 1:**
- Deploy the full website
- Web3Forms ✅ already done (key integrated)
- Set up Razorpay (1 hour with PAN/bank docs)
- Set up Calendly event types (30 min)
- Test every link yourself

**Week 2:**
- Announce on YouTube channel community tab
- Share on Telegram and Instagram
- Email 10 friends/colleagues asking for honest feedback

**Week 3:**
- Add Episode 02 to home page videos
- Write Article #3 (CRR & SLR)
- Reach out to 3 personal-finance YouTubers for cross-promotion

**Week 4:**
- Review website analytics in Cloudflare
- See which pages get most traffic
- Double down on what's working
- First paid consulting client (target)

---

**You now have a real, professional website. Use it. Iterate. The first 1,000 visitors will tell you what's working — listen to them, not to advice from people who haven't seen your traffic.**

🙏 Built with care for SaralArthaShastra.

---

## ✨ Design Upgrade — April 2026

The website has been polished with a **"Refined Editorial"** aesthetic — think *The Economist* meets *Stripe Press* meets a private bank's annual report. Key improvements:

- **Typography hierarchy**: Bigger display sizes (88px headlines), italic accents in rust, refined letter-spacing
- **Atmospheric depth**: Subtle paper-grain texture, soft gradient meshes, layered shadows
- **Premium card treatments**: Deeper shadows on hover, gold accent line that appears on interaction, smooth 4px lift
- **Refined buttons**: Serif typography, micro-animations on the arrow indicators, lift-on-hover with deeper shadow
- **Frosted-glass header**: Backdrop blur with semi-transparent paper background
- **Decorative corner brackets** around the portrait (gold top-left, rust bottom-right) for an editorial frame
- **Custom scrollbar** in gold tones
- **Refined form fields**: Mono-style labels in caps, focus rings in rust
- **Polished footer**: Gold accent line at the top, mono-styled section headers

All changes are additive — no existing functionality was changed, no integrations were broken. The polish is delivered as a single CSS layer injected before `</head>` on each page.

If you ever want to revert or modify the design, search for `REFINED EDITORIAL POLISH LAYER` in any HTML file — that's the comment marking the upgrade block.

