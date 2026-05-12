# PRODUCT.md — claude-crounde

## Register

`brand` — a single landing page that IS the product. There is no app to use after; the page itself delivers the value (a generated cron line). Design carries the credibility.

## What this is

A free, no-signup, no-tracking tool that takes a developer's daily work start/end time and emits a cron line. The cron line "primes" the Claude Code rate-limit window before the workday starts, so the 5-hour reset falls inside working hours instead of after them.

It exists because Anthropic's Claude Code has a rolling 5-hour usage window that begins on the first message of the day. For devs who hit the limit, the placement of that window matters more than the size. Shifting the reset into your workday gives you two or three fresh quotas instead of one.

The whole tool is one HTML file. No backend. No database. No analytics. The math is deterministic (`warmup = start − 4h`) and runs entirely client-side.

## Users

**Primary:** Power users of Claude Code — independent developers, technical founders, and freelancers who hit the 5-hour rate limit regularly. They run things in WSL2, on a mini PC, on a VPS. They have a crontab. They know what a rolling window is.

They're skeptical of "AI productivity hacks." They've seen too many landing pages that promise 10× and deliver 1.1×. They want to see the math, copy a line, and leave.

**Secondary:** Devs who don't yet hit the limit but find the link in a Reddit thread or HN comment and want to understand what the trick is. The page has to teach them in under 90 seconds without condescension.

## Tone & voice

- Direct. No "Welcome to..." or "Have you ever wondered...".
- Numeric. Numbers carry the argument. "Up to 3 windows" > "more productivity".
- Honest about tradeoffs. Mention the weekly cap. Don't oversell.
- Slight technical confidence. The voice of a senior dev showing a colleague a trick.

## Anti-references

What this should **not** look like:

- ❌ SaaS landing template: hero with gradient, three "Features" cards, "Loved by 10,000+ developers", testimonial section.
- ❌ Generic dark-mode + purple-accent palette that every Tailwind starter uses (which is exactly what the current version is).
- ❌ Hype copy. "Unlock", "Supercharge", "Take your X to the next level", "Game-changer".
- ❌ Floating glass cards. Drop shadows on dark backgrounds. Gradient text. Decorative blurs.
- ❌ Hero-metric template (big number + small label + supporting stats).
- ❌ Visible reliance on a UI framework's defaults.

What it can resemble (positive references):

- A well-set numerical table in a print magazine (FT, MIT Tech Review).
- The aesthetic of CLI documentation pages that take typography seriously (e.g., redbean, fly.io, sourcehut, fasterthanli.me).
- A scientific diagram from a physics paper showing wave windows and overlap.
- Berkshire Hathaway shareholder letters — confident, plain, numerate.

## Strategic principles

1. **The cron line is the hero.** Not the headline, not the timeline viz, not the explanation. The user is here to get a line of text. Make sure they can get it within 3 seconds of landing if they want to.

2. **Math earns trust.** Show the algorithm. Show the windows. A developer who understands *why* will copy with confidence; one who's just told to trust the output will close the tab.

3. **Restraint over flourish.** Every visual element should answer "what does this tell me about the cron line I'm getting?". No decorations. No bonus illustrations.

4. **The page is the proof.** If the page looks credible, the cron line is credible. The footer link to a real human (ramonmatos.com.br + the open-source repo) closes the deal — anyone can fork and verify the math.

## Practical constraints

- Single `index.html`. No build step. Inline CSS + JS.
- Google Fonts allowed (one or two faces, max).
- pt-BR copy. Numbers and code stay universal.
- Deploy: Vercel (already wired). DNS: Cloudflare (already wired).
- License: MIT (already in repo).
- Existing JS logic is correct — preserve all calculation behavior, only change presentation and bindings.
