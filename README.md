# SE Lab — From Fundamentals to the Customer Conversation

A hands-on lab for Commercial Solutions Engineers, built on top of dbt Labs' **jaffle_shop_duckdb** project. You'll work an end-to-end data pipeline using the exact toolchain a data engineer prospect lives in — the command line, Git, pull requests, and CI/CD — so you can hold those conversations with credibility.

This lab is part of the **CLI & Developer Fundamentals SE Book Club**. It's the applied capstone where the modules come together in a real workflow.

> **Built on a real project.** This repo is a fork of [dbt-labs/jaffle_shop_duckdb](https://github.com/dbt-labs/jaffle_shop_duckdb), the canonical dbt demo project. "Jaffle Shop" is a fictional e-commerce store; the dbt project transforms raw app data into `customers` and `orders` models ready for analytics. We use it because it's professionally maintained, recognizable to anyone who's touched dbt, and runs fully locally on DuckDB — no warehouse, no credentials. The original project README is preserved as [UPSTREAM_README.md](./UPSTREAM_README.md).

---

## Why this matters for an SE at Sigma

Sigma's CLI, API actions, and the agent/MCP motion are pulling us into conversations with a new kind of buyer: data engineers and platform leads. They don't live in dashboards; they live in terminals, commit to repos, and review pull requests. They evaluate tools by whether they fit a modern software-development workflow.

We're strong on BI. This is a different muscle. When a prospect's data engineer says *"we version-control our models"* or *"we need this to run in our CI pipeline,"* you need to know exactly what they mean and respond without hand-waving.

This lab builds that fluency through real, hands-on work. Everything maps back to Sigma: workbooks-as-code is the same Git workflow you'll practice here, Sigma CLI is the same command-line muscle, and promoting content through environments is the same SDLC. Learn the pattern here; apply it to Sigma in every deal.

---

## What you'll learn

By the end of this lab you'll be able to:

- **Work the command line** — run a real transformation pipeline (`dbt seed`, `dbt run`, `dbt test`) from the terminal without flinching
- **Use Git like a practitioner** — branch, commit, push, open a pull request, review someone else's code, and merge
- **Understand the dev → production loop** — see how a change moves from a local edit, through review, through automated CI checks, to merge
- **Read CI/CD in the wild** — watch a GitHub Actions workflow run the pipeline automatically and see it pass and fail
- **Translate it to a customer conversation** — map the workflow onto real customer architectures and know which personas care about it (and which don't)

---

## The toolchain

| Tool | What it is | Why it's here |
|------|-----------|---------------|
| **dbt** | Transformation framework data engineers use to build analytics code | Runs from the CLI, version-controlled in Git — the buyer's daily driver |
| **DuckDB** | An in-process database that needs zero setup or credentials | Lets the whole lab run locally on any laptop, no warehouse required |
| **GitHub** | Repo hosting, pull requests, and Actions for CI/CD | Where the version control and CI/CD story lives |

No Sigma products are used in this lab. That's intentional — we learn the buyer's world first. When Sigma CLI ships, the workbook build slots into this exact same Git/CI/CD scaffolding.

**Two package managers, two jobs:** Homebrew installs system-level tools and binaries (Python itself, `git`, `jq`, and eventually the Sigma CLI). pip installs Python packages (dbt and its adapters). Knowing which manager handles what is part of the fluency this lab builds — data engineers use both daily.

---

## Quick start

```bash
# 1. Install Python with Homebrew (skip if you already have Python 3.9+)
brew install python

# 2. Set up an isolated environment and install the project's dependencies
python3 -m venv venv
source venv/bin/activate
pip install -r requirements.txt

# 3. Run the whole pipeline (seed data + build models + run tests) in one command
dbt build

# 4. (Optional) Generate and serve the project docs to see the lineage graph
dbt docs generate
dbt docs serve
```

If `dbt build` succeeds, you've just run a complete analytics pipeline locally — the workflow a data engineer runs every day, minus the warehouse.

> The upstream project pins exact dependency versions in `requirements.txt`, which is why we use a venv + `requirements.txt` install here rather than a bare `pip install dbt-duckdb`. This is itself a teaching point: real data teams pin their dependencies so every environment is reproducible.

---

## The lab

The hands-on session materials live in [`lab/`](./lab):

- **[lab/LAB_WORKSHEET.md](./lab/LAB_WORKSHEET.md)** — the step-by-step guide you follow on lab day
- **[lab/FACILITATOR_GUIDE.md](./lab/FACILITATOR_GUIDE.md)** — block-by-block timing, facilitation notes, and the architecture-walk structure
- **[lab/scenarios/](./lab/scenarios)** — the three customer scenario briefs handed to pairs

---

## Links

- **Upstream project:** [dbt-labs/jaffle_shop_duckdb](https://github.com/dbt-labs/jaffle_shop_duckdb)
- **SE Book Club channel:** `#se-book-club` on Slack
- **Book Club curriculum:** pinned source-of-truth doc in `#se-book-club`

---

## Publishing this repo to GitHub

```bash
# 1. Create a new EMPTY repo on github.com (no README, no .gitignore)
#    e.g. se-book-club-lab

# 2. From inside this folder, point it at your remote and push:
git remote add origin https://github.com/<your-username>/se-book-club-lab.git
git branch -M main
git push -u origin main
```

If you need to correct the commit author first:

```bash
git commit --amend --author="Adam Barlow <your-email@sigmacomputing.com>" --no-edit
```

---

## Attribution

Built on [dbt-labs/jaffle_shop_duckdb](https://github.com/dbt-labs/jaffle_shop_duckdb), licensed under Apache 2.0 (see [LICENSE](./LICENSE)). SE lab materials in `lab/` and the CI workflow are additions for Sigma SE enablement.
