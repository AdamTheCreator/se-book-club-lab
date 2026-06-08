# Scenario B — The Embedded Analytics Pivot

**Hand this to the pair. The technical steps in the worksheet are the same for everyone — this scenario shapes how you frame your demo.**

---

**Customer:** Healthcare technology vendor, ~250 employees, SaaS platform for medical practices, Series B.

**Their stack:**
- Postgres (operational), Snowflake (analytics, ~6 months in)
- Custom in-house dashboards built into their product (React + a charting library)
- No real BI tool — engineering builds every dashboard request
- One data engineer, two backend engineers, no analytics engineers
- GitHub Enterprise, basic CI

**Their problem:** Customer-facing dashboards are eating engineering capacity. They want to ship analytics features faster but the team is at capacity. They've heard about embedded analytics but don't know what it means in practice.

**Your champion:** Marcus, VP Engineering. Allergic to anything that adds a vendor dependency or compromises their security model.

**His concern, in his words:**
> "How do I trust your auth model? What does this look like when my customer logs into my product and sees a dashboard? Show me the actual flow."

---

**For your demo, be ready to answer:**
- This is an engineering buyer, not an analyst. How does your framing change?
- Auth is his real question — and it's Module 4 material you haven't covered yet. The honest move: acknowledge it's the key question, sketch what you'd need to answer it, and don't bluff. How do you do that without losing credibility?
- Where does treating analytics-as-code help an engineering team that ships dashboards as a product feature?

**What this tests:** Speaking to an engineer-buyer, and the discipline to flag what you don't yet know instead of hand-waving.
