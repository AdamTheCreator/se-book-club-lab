# Scenario A — The Modern Stack Migration

**Hand this to the pair. The technical steps in the worksheet are the same for everyone — this scenario shapes how you frame your demo.**

---

**Customer:** Mid-market B2B SaaS, ~600 employees, $80M ARR, Series C.

**Their stack:**
- Snowflake (3 years in, mature)
- dbt Cloud for transformations, ~400 models, version-controlled in GitHub
- Looker for BI (current incumbent), aging 5-year-old implementation
- GitHub Actions for analytics CI/CD
- Hightouch for reverse ETL

**Their problem:** Looker renewal is 6 months out. The analytics engineering team (4 people, all dbt-fluent, all terminal-native) is pushing leadership to evaluate alternatives — they want LookML-grade governance but better last-mile interactivity for business users.

**Your champion:** Sarah, Senior Analytics Engineer. First call is a technical evaluation.

**Her concern, in her words:**
> "We spent two years getting our semantic layer right in dbt and LookML. We're not redoing that work. Whatever we adopt has to fit our existing workflow — Git, PRs, dev/staging/prod, all of it."

---

**For your demo, be ready to answer:**
- This team already lives in Git and dbt. How does what you built map onto a workflow they already have?
- What does "fits our existing workflow" actually mean to Sarah, and how do you speak to it credibly?
- Where does an analytics platform add value *on top of* their dbt investment rather than replacing it?

**What this tests:** Git/dbt fluency, credibility with an analytics engineer who knows more than you about their own stack.
