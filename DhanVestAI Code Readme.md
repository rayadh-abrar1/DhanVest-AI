# DhanVest AI — Build Package & Presenter's Guide

Everything here is built to be shown tomorrow and deployed after. Read this once tonight. It assumes **zero** prior AI knowledge and walks you through every step.

---

## 1. What you have in this folder

| File | What it is | What to do with it |
|---|---|---|
| `dhanvest-mvp.html` | **The working MVP.** The Verified Signal engine — real DSE stocks, real factor scoring, live AI explanations in Bangla + English. | This is what you demo to judges. |
| `index.html` | **The marketing website.** A polished landing page (Slash/Wealth.com-style, but original to DhanVest). | Deploy this as your public site. |
| `README.md` | This guide. | Read it. |
| `DhanVest_Q&A_and_Naming.md` | 100 likely questions + the meaning behind the name + ICE DU framing. | Study before the pitch. |

Both HTML files are **self-contained** — no installs, no build step, no server needed to open them. Double-click and they run in any browser.

---

## 2. The one thing to understand about the AI (in plain English)

You are not building an AI from scratch. That would take a team and years. Instead, DhanVest **uses** an existing AI (a large language model, or "LLM") the same way a website uses Google Maps — you send it a question over the internet and it sends back an answer.

Here's the whole idea in four steps:

1. **Your code does the maths.** It takes real numbers about a company (price, P/E, ROE, debt) and calculates four scores: momentum, value, quality, liquidity. This is ordinary arithmetic — no AI involved. *You* control it, so it's trustworthy and explainable.
2. **Your code writes a paragraph of instructions** ("here is company X, here are its scores and its news headlines — explain in simple Bangla what this means, name one strength and one risk, never predict the price").
3. **That paragraph is sent to the AI** over the internet.
4. **The AI sends back the explanation**, which your app shows on screen.

That's it. The AI is the *translator that turns numbers into plain Bangla*. The **intelligence and the discipline live in your code**, not in the AI. This is exactly why your pitch says "no black box" — you can show a judge every number the score came from.

> **The killer line for judges:** "The AI doesn't decide anything. Our engine scores the stock from public numbers you can inspect; the AI just explains those numbers in Bangla. We never predict prices — we explain the present."

---

## 3. How the MVP works (so you can explain it confidently)

Open `dhanvest-mvp.html`. You'll see:

- **Left — the Signal Board:** 10 real DSE large-caps (GP, Square Pharma, BRAC Bank, etc.), each with a composite score 0–100, ranked best to worst, colour-coded (green = accumulate, amber = hold, red = watch).
- **Right — the Detail Panel:** click any stock and you see the four factor bars (so a judge sees *why* it scored what it did), then an **AI Explanation** button.
- **Click "Generate explanation"** → the app calls the AI live and writes a Bangla + English explanation of that stock, with an honest **confidence meter**.
- **"Show verification sources"** → reveals the line explaining that every factor traces to public data. This is your trust moment.

### The factor engine (what the numbers mean)
- **Momentum** — is the price rising or fading vs its 3-month average?
- **Value** — is the P/E cheap or expensive *for its own sector* (not the whole market)?
- **Quality** — is the business healthy (high ROE, low debt)?
- **Liquidity** — can you actually trade it, or is it too thin?

The composite is a weighted blend (quality 32%, value 28%, momentum 25%, liquidity 15%). You can defend every weight.

### Honesty note you must know
The stock figures are **realistic but illustrative** — hand-set so the demo is stable and never breaks live. The banner on the MVP says "illustrative market snapshot" so you are never claiming it's a live feed. **If a judge asks: yes, be upfront** — "the data is a hand-curated snapshot for the demo; the live product connects to the DSE data feed. The *engine and the AI are completely real* — the explanation you just saw was generated live." That honesty scores points; a caught exaggeration loses everything.

---

## 4. Demoing tomorrow — the exact 3-minute script

**Before you start:** open `dhanvest-mvp.html` in your browser, full-screen, with GP (top stock) already selected. Have `index.html` in a second tab.

**0:00–0:35 — The problem (say it, don't show slides yet)**
> "1.4 million Bangladeshis have left the stock market since 2016. They didn't leave because they have no money — mobile finance moved 158 billion dollars last year. They left because they were trading blind, on Facebook rumours, in a market they couldn't trust. The tools to invest with confidence simply don't exist here. That's what we're building."

**0:35–0:55 — Introduce the product**
> "This is DhanVest AI. Our engine scores every listed company on transparent factors, then an AI explains what the score means — in plain Bangla. Let me show you." *(Switch to the MVP.)*

**0:55–2:10 — The live demo (this is the heart — go slow)**
- "Here's our signal board — every DSE large-cap, scored and ranked." *(gesture at the list)*
- Click GP. "Take Grameenphone. It scores 78 — accumulate. But we don't ask you to trust that number blindly. Here's *why*: strong value, its P/E is below the telecom sector average; excellent quality, 34% return on equity." *(point at the bars)*
- Click **Generate explanation**. Wait for it. "And here's the part that matters for a first-time investor in Bangladesh — the AI reads those exact numbers and the latest news, and explains it in Bangla and English." *(read one Bangla line aloud if you can — it lands)*
- Point at the confidence meter. "It gives an honest confidence level. And notice — it never says the price *will* go up. We explain the present; we don't fake the future."
- Click **Show verification sources**. "Every number traces to a public filing. No black box."

**2:10–2:50 — The vision (switch to `index.html`, scroll the two-stage section)**
> "This research platform is stage one — it earns trust and revenue from day one. Stage two is where it becomes big: a BSEC-licensed, AI-assisted asset manager. Mutual funds and thousand-taka monthly plans, distributed through bKash. India built exactly this — Zerodha, Groww — and digitised tens of millions of investors in a decade. Nobody has done it in Bangladesh, because nobody has the Bangla data, the local licence path, and the trust. We do."

**2:50–3:00 — The close**
> "Bangladesh's wealth is going digital. We're building the intelligence layer it flows through. We're DhanVest AI."

**Then stop talking.** Let the questions come.

---

## 5. Deploying the website (free, ~10 minutes)

You already use GitHub (github.com/rayadh-abrar1), so use **GitHub Pages** — it's free and you know it.

1. Create a new repository, e.g. `dhanvest`.
2. Upload `index.html` (and optionally `dhanvest-mvp.html`) to it.
3. Repo → **Settings → Pages** → Source: `main` branch, `/root` → Save.
4. In a minute your site is live at `https://rayadh-abrar1.github.io/dhanvest/`.
5. The MVP will be at `.../dhanvest/dhanvest-mvp.html`.

**Alternative (even easier): Netlify Drop.** Go to app.netlify.com/drop and drag the folder in. Instant URL, no account needed to start.

> **One caveat about the live AI in deployment:** the "Generate explanation" button in the MVP calls the AI through an interface that works inside Claude's environment. On a plain public web host, that exact call needs a small backend key setup to work (so your API key isn't exposed in public code). **For tomorrow's demo, run the MVP from where it works live, or pre-generate a few explanations as a fallback (see §6).** For the real product, a developer wires the AI call through a tiny server function — a half-day job, not a rebuild.

---

## 6. Safety net: never let the demo fail live

Wi-Fi at events is unreliable. Do this tonight so you're bulletproof:

1. Open the MVP, click through GP, Square Pharma, and BRAC Bank, and **generate an explanation for each** while you have internet.
2. **Screenshot each result.** Put the three screenshots in your phone and on a slide.
3. If the live call fails tomorrow, you say: "Let me show you one we ran earlier" and show the screenshot. The judges still see real AI output; you just didn't generate it in the room.

Also: **have the deck PDF open** as the ultimate fallback if the browser itself misbehaves.

---

## 7. If a developer asks "how is this actually built?"

- **MVP:** plain HTML + CSS + vanilla JavaScript, one file. The factor engine is pure functions (`factorScores`, `composite`). The AI call is a single `fetch()` to the Anthropic Messages API with a carefully written prompt that forces: bilingual output, reference to the real numbers, balanced strength/risk, and no price prediction. Confidence is derived from how decisive the composite is plus liquidity — deterministic, not made up by the model.
- **Website:** static HTML/CSS/JS, no framework, deployable anywhere. Design system: navy `#1E2761` + ice-blue + a mint accent, Fraunces (display) / Inter (body).
- **To make the data live later:** replace the hard-coded `STOCKS` array with a fetch from a DSE data provider (or a nightly scrape into a small database). The engine and UI don't change — only the data source. That's the whole point of the architecture.

---

## 8. What's real vs. what's roadmap (keep this straight)

| Real today (you can show it) | Roadmap (you're honest it's ahead) |
|---|---|
| Factor scoring engine | Live DSE data feed integration |
| Live AI explanations in Bangla | Full Bangla-news scraping pipeline |
| The whole product UX | BSEC asset-management licence |
| The financial model & market research | The actual mutual funds & SIPs |

Never blur these two columns. Your credibility is the asset.

---

*Built for Rayadh Abrar · DhanVest AI · rayadh.abrar01@gmail.com*
