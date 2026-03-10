# 🚀 Chatbot Demo Deployment Guide
## From zero to live demo in 3 hours

---

## FOLDER STRUCTURE
```
chatbot-demos/
├── bella-italia/
│   └── index.html          ← Complete restaurant website + chatbot
├── fitcore-gym/
│   └── index.html          ← Complete gym website + chatbot
└── n8n-workflows/
    ├── bella-italia-workflow.json   ← Import into n8n
    └── fitcore-gym-workflow.json    ← Import into n8n
```

---

## STEP 1 — Set Up n8n (15 minutes)

### Option A: n8n Cloud (Recommended — no install needed)
1. Go to https://n8n.io and click "Start for free"
2. Create account — free tier gives you 5 workflows
3. You'll get a URL like: https://your-name.n8n.cloud

### Option B: Run locally
```bash
npx n8n
# Opens at http://localhost:5678
```

---

## STEP 2 — Add OpenAI API Key to n8n (5 minutes)

1. Go to https://platform.openai.com/api-keys
2. Create a new API key (new accounts get $5 free credits — enough for 200+ demo conversations)
3. In n8n: Click your name → Credentials → New Credential → OpenAI API
4. Paste your API key and save

---

## STEP 3 — Import Workflows (5 minutes)

### For Bella Italia:
1. In n8n, click "+ New workflow"
2. Click the 3-dot menu → Import from file
3. Select: `n8n-workflows/bella-italia-workflow.json`
4. Click "Activate workflow" toggle (top right)
5. Copy the webhook URL — it looks like:
   `https://your-name.n8n.cloud/webhook/bella-italia-chat`

### For FitCore Gym:
1. Repeat above with `n8n-workflows/fitcore-gym-workflow.json`
2. Webhook URL: `https://your-name.n8n.cloud/webhook/fitcore-chat`

---

## STEP 4 — Connect Webhooks to UI (2 minutes)

### In bella-italia/index.html:
Find line:
```javascript
const N8N_WEBHOOK_URL = 'YOUR_N8N_WEBHOOK_URL_HERE';
const USE_DEMO_MODE = true;
```

Replace with:
```javascript
const N8N_WEBHOOK_URL = 'https://your-name.n8n.cloud/webhook/bella-italia-chat';
const USE_DEMO_MODE = false;
```

### In fitcore-gym/index.html:
Find the same lines and replace with your FitCore webhook URL.

---

## STEP 5 — Deploy to Vercel (10 minutes)

### Deploy Bella Italia:
```bash
# Install Vercel CLI
npm install -g vercel

# Deploy
cd bella-italia
vercel

# Follow prompts:
# Project name: bella-italia-demo
# Directory: ./
# Override settings: No
```

You'll get a live URL like: `https://bella-italia-demo.vercel.app`

### Deploy FitCore Gym:
```bash
cd ../fitcore-gym
vercel
# Project name: fitcore-gym-demo
```

Live URL: `https://fitcore-gym-demo.vercel.app`

### Alternative: Use Netlify (also free)
1. Go to https://netlify.com
2. Drag and drop the bella-italia folder onto the Netlify dashboard
3. Instant live URL — no CLI needed

---

## STEP 6 — Test Your Chatbots

Open your live URLs and test these questions:

### Bella Italia — test questions:
- "What time do you close on Fridays?"
- "Do you have vegetarian options?"
- "Can I book a table for 4 people this Saturday?"
- "What's on your menu?"
- "How much does a pasta dish cost?"
- "Where are you located?"

### FitCore Gym — test questions:
- "What are your membership prices?"
- "What classes do you offer?"
- "Do you have a free trial?"
- "What are your opening hours?"
- "I want to lose weight — which plan should I get?"
- "Can I cancel anytime?"

---

## STEP 7 — Record Your Fiverr Demo Video

### Screen recording tools (all free):
- **OBS Studio**: https://obsproject.com (best quality)
- **Loom**: https://loom.com (easiest, instant share link)
- **Windows**: Win + G (Game Bar)
- **Mac**: Cmd + Shift + 5

### Recording script (60–90 seconds):

**[0–5 sec]** Open Bella Italia website. Show the full page. Type overlay: "AI Chatbot for Small Businesses"

**[5–8 sec]** Click the chat button. Chat window pops up. Sofia says hello.

**[8–25 sec]** Type these 3 questions live (slowly, so viewers can read):
1. "What time do you close on Sundays?"
2. "Do you have vegetarian pasta options?"
3. "I'd like to book a table for 4 this Saturday at 7pm"

**[25–30 sec]** Text overlay: "Works for ANY business — watch this"

**[30–35 sec]** Switch to FitCore Gym tab

**[35–55 sec]** Type 2 questions:
1. "What's included in the Pro plan?"
2. "How do I start a free trial?"

**[55–65 sec]** Switch to n8n tab. Show the workflow for 5 seconds. Text overlay: "Powered by AI — no manual replies needed"

**[65–80 sec]** Back to Bella Italia. Text overlay: "Delivered in 3 days. Order on my Fiverr profile."

### Video editing (free):
- **CapCut** (desktop): Best for text overlays and cuts
- **DaVinci Resolve**: Professional quality, free
- Export at 1080p, MP4 format

---

## CUSTOMISING FOR A REAL CLIENT

When you get an actual order, here's what to change:

### In the HTML file:
1. Business name (search and replace "Bella Italia" with client's name)
2. Colors (change CSS variables at top of file)
3. Logo/avatar emoji in chat header
4. Quick reply buttons (change to client's common questions)
5. Footer text

### In the n8n workflow:
1. Open the OpenAI node
2. Replace the entire system prompt with client's business info:
   - Business name and description
   - Products/services and prices
   - Opening hours
   - Location and contact
   - Common FAQs
3. That's it — the chatbot is now trained on their business

**Time to customise for a new client: 45 minutes maximum**

---

## DEMO MODE vs LIVE MODE

Both chatbots have a built-in demo mode that works WITHOUT n8n or OpenAI:

```javascript
const USE_DEMO_MODE = true;   // Uses pre-written responses — no API needed
const USE_DEMO_MODE = false;  // Uses real n8n + OpenAI responses
```

**Use demo mode for:**
- Recording your Fiverr gig video (no API costs)
- Showing prospects before they've paid
- Portfolio screenshots

**Use live mode for:**
- Actual client delivery
- When you have n8n webhook set up

---

## COSTS BREAKDOWN

| Service | Free Tier | Paid |
|---------|-----------|------|
| n8n Cloud | 5 workflows, 5 executions/month | $20/month for unlimited |
| n8n Self-hosted | Unlimited (run on your laptop) | Free forever |
| OpenAI API | $5 credit on new accounts | ~$0.002 per conversation |
| Vercel | Unlimited static sites | Free |
| Netlify | Unlimited static sites | Free |

**For your demos: $0 total**
**For a client's live chatbot: ~$3–5/month in OpenAI costs at 500 conversations/day**

---

## WHAT TO TELL CLIENTS ABOUT COSTS

When a client asks "what does it cost to run?":

> "The chatbot runs on your website with no monthly platform fees. You only pay for the AI conversations — roughly $3–8/month for a typical small business doing 300–500 customer chats per month. That's less than one hour of staff time."

This makes the ROI obvious and removes price objections.

---

## FIVERR GIG ASSETS CHECKLIST

After completing this setup, you should have:

- [ ] Bella Italia demo live at a Vercel URL
- [ ] FitCore Gym demo live at a Vercel URL
- [ ] 60–90 second Fiverr gig video recorded
- [ ] 4 screenshots for Fiverr gig images:
  - [ ] Bella Italia chat open on restaurant page
  - [ ] FitCore Gym chat open on gym page
  - [ ] n8n workflow screenshot
  - [ ] Mobile view of one chatbot
- [ ] Instagram Reel version (30–45 seconds, faster cuts)

**You are now ready to publish your Fiverr gig. Go do it.**
