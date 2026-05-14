# Context — SEO Monitoring Playbook

This document explains the thinking behind the dashboard so that when you update it in the future, your additions are consistent with the original design intent. Read this before adding or removing anything.

---

## The core problem this dashboard solves

Most SEO dashboards show you data. This one shows you what to **do** with data.

The common failure mode for site owners is: they open Google Search Console, see a metric, don't know if it's good or bad, and close the tab. Or they notice a traffic drop three weeks after it started because they weren't monitoring consistently.

This dashboard solves both problems by giving every metric three layers:

1. **Why monitor** — so you understand the strategic importance, not just what to check
2. **Key signals & thresholds** — so you know exactly when a number becomes a problem
3. **Action playbook** — so you know what to do the moment a signal fires

---

## Why the three-frequency cadence?

**Daily** — The items that can change overnight and cause immediate, compounding damage. Site going down, a new crawl error blocking your homepage, a sudden 30% traffic drop. These need same-day response. Keep this list short enough to complete in under 15 minutes.

**Weekly** — Items that are too noisy to judge daily but show real trends on a 7-day view. Keyword ranking movements, content performance, backlink profile changes. A keyword that fluctuates ±2 positions daily might show a consistent -5 trend weekly — that's the signal worth acting on.

**Monthly** — Items that require dedicated time and strategic thinking. Full technical audits, content gap analysis, E-E-A-T reviews. These can't be squeezed into 15 minutes — block 2–3 hours on the first Monday of each month.

---

## The badge priority system

Every item has exactly one badge, which sets the urgency of the response:

**Critical (`"c"`, red)** — When this signal fires, stop what you're doing and investigate today. These are items where delay causes compounding damage: a crawl error that prevents indexing, a traffic drop that means customers can't find you, a lost high-DA backlink that causes a ranking drop within weeks.

**Watch (`"w"`, amber)** — These items won't hurt you today, but will compound into critical problems within 2–6 weeks if ignored. Consistent attention is how you prevent them from becoming critical.

**Opportunity (`"o"`, green)** — These are potential ranking gains hiding in plain sight. Page 2 keywords, unlinked brand mentions, featured snippet gaps. They don't need urgent action, but regular attention turns them into traffic wins.

**AI-specific (`"a"`, blue)** — Items that are standard SEO best practice but disproportionately important for AI sites specifically. AI Overview citations, crawl budget efficiency with dynamic content, E-E-A-T for AI-generated content, AI content engagement signals. Every AI site has these as elevated priorities relative to a standard blog or e-commerce site.

---

## What makes a metric worth adding?

Before adding a new checklist item, run it through these questions:

**1. Is it actionable?**
If you can't write at least 2–3 concrete action steps for "what to do when this fires," it's a data point, not a metric worth monitoring. Watching a metric you can't act on creates anxiety without outcomes.

**2. Is the frequency right?**
Daily: can it change overnight and cause immediate damage?
Weekly: does it show meaningful trends on a 7-day view?
Monthly: does it require strategic analysis and dedicated time?

**3. Does it have a threshold?**
"Monitor organic traffic" is not a checklist item. "Check if organic sessions dropped >15% day-over-day" is. Every item should have at least one number or condition that defines "this needs attention."

**4. Is it specific to your AI site context?**
Generic SEO advice is everywhere. This dashboard is specifically for an AI-focused site. If the item is equally relevant to a recipe blog, it may not deserve an AI-specific badge — but it may still belong in the checklist if it's a universal signal.

**5. Does it overlap with an existing item?**
Before adding, check whether the new metric is already captured by an existing item. Better to add a signal or action to an existing item than to create two separate items that reference the same data source.

---

## The AI site SEO context

Running an AI-focused site in 2025+ involves specific SEO dynamics that differ from other niches:

**AI Overviews (SGE) impact** — Your core informational queries are among the most likely to trigger AI Overviews. This means your content strategy needs to consider both traditional ranking (for queries where AIO doesn't appear) and AIO citation (for queries where it does).

**E-E-A-T scrutiny** — Google's Quality Raters are specifically trained to evaluate AI-generated or AI-assisted content. Sites that appear to mass-produce undifferentiated AI content are penalized. Every piece of content needs clear expertise signals: author credentials, original perspective, cited sources, or hands-on experience with the tools/models being discussed.

**Content freshness** — AI is the fastest-moving technology sector. An article about a model's capabilities from 6 months ago may be significantly outdated. Your freshness monitoring cadence needs to be more aggressive than a typical site.

**Crawl budget and dynamic content** — If your site includes any AI-powered tools, chat interfaces, or dynamically generated content, you're at risk of Googlebot consuming its crawl budget on low-value generated URLs. Monitoring crawl stats is a higher-priority item for you than for a static content site.

**INP (Interaction to Next Paint)** — AI tool pages that load heavy JavaScript for chat or generation interfaces commonly fail this Core Web Vital. This is your most likely CWV failure point and deserves more attention than LCP or CLS for most AI sites.

---

## The "Why → Signals → Actions" format — writing guidelines

When writing or editing a detail panel entry, follow these guidelines:

**Why (1–3 sentences):** Lead with the business consequence, not the technical explanation. "This is important for SEO" is not a why. "A 2-spot drop from #1 to #3 can cut your traffic on that keyword by 65%" is a why.

**Signals (3–6 bullet points):** Each bullet should be in the format `[condition]: [implication] — [initial response]`. Specific numbers are almost always better than vague qualifiers. "Drop >15%" is better than "significant drop."

**Actions (3–6 bullet points):** Each bullet should be a concrete step, not a general direction. "Check for content changes" is weak. "Check if the page was recently edited → compare your page vs the current #1 ranking competitor" is an action. Where possible, name the specific report or tool to open.

---

## Things intentionally left out

**Traffic acquisition channels beyond organic** — This is an organic SEO dashboard, not a full marketing analytics dashboard. Paid, social, and direct channels are out of scope.

**Conversion rate optimization (CRO)** — While engagement metrics appear where they affect SEO signals (time on page, bounce rate), landing page CRO is a separate discipline with different monitoring cadences.

**Social media performance** — Social can influence brand search volume and drive links, both of which appear in the backlinks and brand search items. But social metrics themselves are out of scope.

**Paid link monitoring** — This dashboard assumes organic, editorial link acquisition. Paid link schemes create legal and Google policy risk and are intentionally not included.

**Real-time monitoring** — Tools like UptimeRobot and Better Uptime handle real-time alerting. The daily check here is a confirmation review, not a real-time monitor. Set up UptimeRobot separately to alert you immediately when your site goes down.

---

## Recommended toolstack

These are the tools referenced throughout the dashboard. You don't need all of them on day one:

**Free tier (start here):**
- Google Search Console — the single most important tool
- Google Analytics 4
- Google Trends
- UptimeRobot (free for 5 monitors with 5-minute checks)
- Google Rich Results Test
- Screaming Frog (free up to 500 URLs)

**Paid, high value:**
- Ahrefs or Semrush — pick one, not both (Ahrefs has better backlink data; Semrush has better keyword research tools)
- Sitebulb — for deeper technical audits than Screaming Frog
- Better Uptime — more reliable than UptimeRobot at scale

**Optional:**
- Brand24 or Mention.com — brand mention monitoring
- AlsoAsked.com — PAA research
- Looker Studio — custom reporting dashboards
- Screaming Frog Log File Analyser — Googlebot crawl analysis
