# LinkedIn launch post

Comment-gated. The GitHub link goes in the DM, never in the post body. No hashtag spam, no link in body, strong first line, short lines.

Pick one variant. Post natively (paste the text, don't link out). Reply to every "SKILLS" comment with the repo link by DM.

---

## Variant A (the "syntax is cheap" angle: recommended)

AI can write Shopify Liquid. It can't tell when the Liquid is wrong.

That gap is the whole job now.

So I built 8 Claude skills that close it.

They make Claude write Shopify themes the way a senior dev would, and catch the mistakes the junior version ships:

- prices through the money filter, never raw cents
- images through image_url, never a 3000px file on a phone
- custom data in metafields, never parsed out of the product title
- no inline styles that get stripped on theme push
- variant logic left to Shopify, not rebuilt in JS

Plus skills for CRO, Core Web Vitals, SEO structured data, accessibility, and one that audits AI-generated Liquid before it ships.

Every Liquid example is validated against the official Shopify docs. If a filter isn't real, it isn't in there. (Ask me about the time I shipped a lesson teaching a filter that doesn't exist.)

It's free. MIT. Install in about a minute.

Comment SKILLS and I'll send you the repo.

---

## Variant B (the "I kept fixing the same mistakes" angle)

I reviewed enough AI-written Shopify code to spot the pattern.

It's always the same five mistakes:

raw prices that ship "1999" instead of "$19.99"
data parsed out of the product title instead of a metafield
inline styles that vanish on theme push
variant logic rebuilt in JavaScript for no reason
a filter that looks real and doesn't exist

So I stopped fixing them by hand and taught Claude not to make them.

8 skills. Production Shopify themes, CRO, performance, SEO, accessibility, plus one that reviews AI-generated Liquid and flags exactly those five things.

Every example validated against the Shopify docs. Free, MIT, installs in a minute.

Comment SKILLS and I'll send you the repo.

---

## Reply-by-DM template (for each "SKILLS" comment)

> Here you go: [GitHub repo link]
>
> Drop the skill folders into ~/.claude/skills/ and Claude picks the right one automatically. The README has the one-line install.
>
> If you want the wider path (how to actually become a Shopify dev now that AI writes the syntax), I put a free starter kit here: learnshopify.dev/starter-kit. No spam, one email.

---

## Notes on why it's built this way

- **First line is the hook and stands alone.** LinkedIn truncates after ~3 lines; the first line has to earn the "see more".
- **No link in the body.** LinkedIn suppresses reach on posts with outbound links. The comment gate also turns every requester into a comment, which compounds reach.
- **The repo link is DM-only.** The starter-kit mention in the DM is the one soft cross-promote; keep it to one line so the DM still feels like a hand-off, not a funnel.
- **No hashtags, no emoji.** Specificity carries it. The five concrete mistakes are the proof you actually did the work.
