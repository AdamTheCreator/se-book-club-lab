# Lab Worksheet — From Fundamentals to the Customer Conversation

Follow these steps with your pair partner. Checkpoints (✅) tell you when you've got it right. If you get stuck for more than 2 minutes, raise your hand — don't sit in silence.

**Your toolchain:** dbt + DuckDB + GitHub, built on the dbt Labs jaffle_shop project. All local, no credentials.

---

## Setup (done together as a room)

```bash
# Install Python 3.12 with Homebrew (dbt does not yet support Python 3.13+)
brew install python@3.12

# Clone the lab repo (your facilitator will share the URL), then:
cd se-book-club-lab
python3.12 -m venv venv
source venv/bin/activate
pip install -r requirements.txt
dbt --version
```

✅ `dbt --version` prints a version with the `duckdb` plugin listed.

**Why two tools?** Homebrew installs system-level binaries (Python, git, eventually the Sigma CLI). pip installs Python packages (dbt). Data engineers use both every day — knowing which is which is part of the point.

### Optional 60-second Homebrew warm-up

```bash
brew install jq                       # a JSON processor used constantly in data work
echo '{"deal":"won"}' | jq .deal      # pull one field out of JSON
```

✅ You just used Homebrew to install a real CLI tool and piped JSON through it.

---

## Part 1 — Run the pipeline (15 min)

The jaffle_shop project is already built out. Run the whole thing:

```bash
dbt build
```

This one command loads the seed data, builds every model, and runs all the tests. Watch the output — you'll see seeds, then staging models (views), then the final `customers` and `orders` models (tables), then ~20 tests.

Now explore what you built:

```bash
dbt docs generate
dbt docs serve
```

Open the docs in your browser and find the **lineage graph** (the green icon, bottom right). This is the dependency map of the whole project.

✅ You ran a full transformation pipeline and viewed its lineage. The same `dbt build` a customer's data engineer runs in production — minus the warehouse.

---

## Part 2 — Make a change on a branch (20 min)

Create a feature branch:

```bash
git checkout -b add-customer-region
```

Open `models/customers.sql` in a text editor:

```bash
open -a "Visual Studio Code" models/customers.sql   # VS Code (Mac)
# or just double-click the file in Finder
```

This model rolls up customer-level metrics. Your task: **add a new column** to the `final` CTE, just before the closing parenthesis. Remember to add a comma after the line above your addition (`customer_lifetime_value`) so the SQL is valid.

<details>
<summary>💡 Need a hint? Click to see example columns</summary>

**Option A — customer_status**
```sql
        case
            when customer_orders.number_of_orders > 1 then 'active'
            else 'one-time'
        end as customer_status
```

**Option B — first_order_year**
```sql
        extract(year from customer_orders.first_order) as first_order_year
```

</details>

Make the edit, then rebuild just this model to confirm it works:

```bash
dbt build --select customers
```

If it builds clean, commit and push:

```bash
git add .
git commit -m "Add <your column> to customers model"
git push -u origin add-customer-region
```

✅ You changed a model on a branch and pushed it. You did NOT touch `main` directly — that's the point.

---

## Part 3 — Open and review a PR (15 min)

- On GitHub, open a pull request from your branch into `main`.
- **Swap repos (or branches) with your pair partner.** Review THEIR PR — leave one real comment (a question or suggestion about their SQL).
- Respond to the comment on your own PR.

Notice what happens automatically when you open the PR: the **CI workflow runs** (see Part 4). Don't merge until it's green.

✅ You completed a full code review cycle. This is the PR workflow every data engineering team runs daily.

---

## Part 4 — Watch CI do its job (10 min — follow along)

This repo ships with a GitHub Actions workflow (`.github/workflows/dbt_ci.yml`) that runs `dbt build` on every push and pull request.

- Open the **Actions** tab on GitHub. Find the run triggered by your PR.
- Watch it install dependencies, build the models, and run the tests.
- When it passes (green ✅), merge your PR.

**Now break it on purpose:** on a new branch, edit one of the tests in `models/schema.yml` so it will fail (or change a model so a `not_null` test breaks), push it, and open a PR. Watch the CI turn red ❌ and block the merge.

✅ This is CI/CD for analytics. When a prospect says "we need this in our pipeline," this red/green check is the picture in their head.

---

## Part 5 — Demo prep (15 min)

With your pair, prepare a **90-second demo** for the room:

1. Your assigned customer scenario — who are they, what's their stack, what do they care about?
2. What you changed and how it maps to their workflow
3. One decision you'd defend to that customer

---

## Your customer scenario

Your facilitator assigned you one of three (see `lab/scenarios/`). The technical steps above are identical for everyone — the scenario shapes how you frame your demo.

---

## After the build: Architecture Walk & Commitment

Put the keyboards down. We'll look at real customer architectures together, then each of you commits to one customer in your pipeline where you'll apply this.
