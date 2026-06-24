# Launch + distribution: The Shopify Developer Starter Kit

Two assets, two audiences:

- **The skills repo** (`LAUNCH-LINKEDIN.md`) targets developers who already build and want better AI output. The payoff is the GitHub repo.
- **The Starter Kit** (this file) targets aspiring / junior / career-switching devs who want to get hired. The payoff is `learnshopify.dev/starter-kit` (email-gated), which also contains the skills repo as item 3.

Run them as two separate posts a week or two apart. They feed the same list.

---

## The LinkedIn post

Brand voice: specific over hype, short lines, no em dashes, no hashtag spam, no link in the body. Comment-gated so the link goes out by DM (link in body suppresses LinkedIn reach; the comment gate also turns every requester into an engagement signal and a warm DM).

### Variant A (the "wish I'd had this" angle: recommended)

I wish someone had handed me these 8 Claude skills when I started building Shopify themes.

They'd have caught every mistake I shipped in my first year.

Here's what nobody tells you in 2026: AI writes the Liquid now. The syntax is the cheap part. What gets you hired is knowing when the AI's code is wrong.

That `{{ product.price }}` ships "1999" to the customer.
That the inline style gets stripped on deploy.
That rebuilding variant logic in JS throws away what Shopify gives you for free.

So I built the kit I wish I'd had:

- 8 Claude skills that write and review production Shopify code
- a Liquid cheat sheet, every line checked against the real docs
- a roadmap from "I know some HTML" to getting paid

Free. One email. No drip.

Comment KIT and I'll send it over.

### Variant B (the cheat-sheet / proof angle)

I made a Shopify Liquid cheat sheet and checked every single line against the official docs.

Sounds boring. Here's why I bothered.

AI hands you Liquid that looks perfect and quietly breaks. A filter that's real in Rails and fake in Shopify. A price that renders as raw cents. A route that dies the moment the store adds a second language.

Plausible-but-wrong is the new broken, and it's everywhere.

So the cheat sheet doesn't just list syntax. It shows the production-correct choice right next to the one that ships bugs.

It's part of a free Starter Kit for Shopify devs:

- the cheat sheet
- a roadmap to getting hired in the AI era
- 8 Claude skills that write and review Shopify code the right way

Free. One email. No drip.

Comment KIT and it's yours.

### DM reply template (for each "KIT" comment)

Keep it warm and short. Personalise the first word with their name when you can.

> Hey [name], thanks for the comment. Here's the kit: learnshopify.dev/starter-kit
>
> Pop your email in and it lands in your inbox right away: the roadmap, the Liquid cheat sheet, and the Claude skills repo. One email, that's the whole thing. No drip, no spam.
>
> If you're serious about breaking in, read the 90-day plan in the roadmap first. And just reply to the email if anything's unclear, it comes straight to me.

Then reply to their public comment too (a simple "Sent! 📩" or "Check your DMs") so the thread shows activity, which lifts the post's reach.

---

## Image: nano banana (Gemini) prompt

nano banana struggles with crisp text and code, so let it own the **background / hero visual** and keep any headline as an overlay (add it in the post itself, Canva, or Figma). Generate at 1:1 for the native post.

**Primary prompt (abstract hero, no text, leaves room for an overlay):**

> A premium, minimal abstract hero image for a developer brand. Square 1:1 composition. Deep charcoal-navy background, hex #0f1419. A single large, elegant glowing curly-brace motif "{ }" rendered as soft volumetric teal light (hex #5eead4), floating slightly right of center with gentle bloom and shallow depth-of-field bokeh. A faint dotted grid texture dissolving into the dark. A few thin, out-of-focus ribbons of teal and warm coral (hex #ff9d6c) light flowing through the scene, suggesting streams of code without any readable letters. Cinematic, high-end, sophisticated, in the visual language of Stripe, Linear and Vercel. Generous negative space in the upper-left for a text overlay. Moody tech-editorial lighting. No text, no words, no letters, no logos, no watermark, no UI screenshots. Sharp, clean gradients, high resolution.

**Variant (more literal, a glowing terminal):**

> Same palette and mood as above. A dark, glassy floating terminal/code panel seen at a slight angle, glowing with soft teal edge light against a near-black navy background (#0f1419). Abstract, blurred lines of colourful syntax inside (teal, coral, soft green), intentionally unreadable. Subtle particles and bokeh. Premium, cinematic, Linear/Vercel aesthetic. Strong negative space top-left. No legible text, no logos, no watermark. 1:1, high resolution.

Tip: after generating, drop the headline ("AI writes the Liquid. Knowing when it's wrong is the job.") top-left in Geist or any clean sans, teal on the word "wrong", and you have the full post image.

### If you'd rather not gate

Put `learnshopify.dev/starter-kit` as the **first comment** (not the post body) and end the post with "Free kit in the comments." Lower friction, less reach, no manual DMs. Use this once volume outgrows hand-sending.

---

## How to get users to the post (distribution)

You don't need a big audience. You need to be where Shopify devs already are.

**LinkedIn (the home base)**
- Post from your personal profile, not a company page. People follow people.
- Post mid-morning on a weekday. Reply to every comment within the first hour: early engagement is what the algorithm amplifies.
- Build a cadence around it: 2-3 build-in-public posts a week (a lesson you shipped, a bug AI made, a CRO finding). The kit post converts far better when it lands on a profile that's clearly active.

**Where Shopify devs gather (seed the same content, adapted):**
- Reddit: r/shopify, r/shopifyDev, r/webdev (read each sub's self-promo rules; lead with value, not the link).
- Shopify Partners community + the Shopify devs Discords/Slacks.
- X/Twitter under #shopifydev and the Shopify dev community.
- dev.to and Hashnode: repost the roadmap or cheat sheet as an article with a link back.
- Indie Hackers / Hacker News: the **skills repo** is the better fit here ("Show HN: Claude skills that write production Shopify Liquid"). The repo README links to the kit, so repo traffic funnels in.

**Answer-where-it-helps**
- Find real questions ("how do I show a sale badge", "why is my price showing 1999") on Reddit/Stack Overflow/the forums and answer them properly, linking the cheat sheet only when it genuinely helps. This is slow, compounding, and high-trust.

**The repo is its own engine**
- A genuinely useful MIT repo gets shared, starred, and linked on its own. Every place the repo spreads, the README points back to the kit and the site.

---

## How to get users into the lead magnet right now

Off-site takes time. These convert traffic you already have, today.

1. **Your blog is the biggest lever.** You have ~30 posts and the blog is the SEO surface. Add a "Get the free Starter Kit" callout inside posts (especially the career and how-to ones). That converts current organic readers with zero new traffic. *This is the highest-leverage on-site change and I can build it as a reusable blog block.*
2. **Already live on the homepage**: the "Not ready to start? Take the kit" section and the scroll-triggered slide-in. Confirm they're firing in PostHog.
3. **Email the existing waitlist once.** You have a list and a brand promise of "no spam," so a single "I made you something" note with the kit link is on-brand and will convert your warmest audience instantly.
4. **Add it to the nav or /resources.** A persistent "Free kit" link in the marketing nav or on the resources page catches every visitor who isn't ready to start a lesson.
5. **Link it from the skills repo README** (already done) so anyone who finds the repo enters the kit funnel.
6. **The welcome / onboarding flow**: for visitors who bounce before lesson 1, the kit is a softer second ask than the launch waitlist.

Measure it: PostHog already fires `starter_kit_signup`. Watch that event by source (homepage section vs slide-in vs `/starter-kit` direct vs blog) so you double down on whatever's working.
