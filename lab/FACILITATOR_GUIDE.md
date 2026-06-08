# Facilitator Guide — SE Lab

**Duration:** 4 hours (half-day) · **Cohort:** 8–12 SEs · **Timing:** end of Module 3 (CLI, Git, SDLC complete; APIs/auth comes after)

The participant-facing steps are in [LAB_WORKSHEET.md](./LAB_WORKSHEET.md). This guide is the block-by-block plan for you.

---

## Before the day

- Send the pre-work note (laptop with admin rights, Python check, GitHub account, editor installed). Don't have them install dbt in advance — setup happens in the room.
- Confirm the repo is pushed and the URL is ready to share.
- Have the three scenario briefs printed or ready to paste (in `scenarios/`).
- Source 3 anonymized customer architecture diagrams for Block 3 (PMM, your SE team, or reconstructed from public case studies).
- Test the full flow yourself once on a clean machine.

---

## Block 1 · Opening + Setup (30 min)

**Frame (5 min):** Workshop, not lecture. Three rules: hands on keyboards, no waiting for permission to try, questions louder than confusion. Deliverable: each person leaves with one customer they'll apply this to.

**Room poll (5 min):** Hands up — who's been in a customer's terminal in the last 30 days? Looked at a customer's Git repo? Been on a call where CI/CD came up? Calibrates the room, sets the bar.

**Setup together (20 min):** Walk the whole room through `brew install python` → clone → venv → `pip install -r requirements.txt` → `dbt --version`. Do it together so nobody falls behind. Pair anyone who errors with someone who succeeded before moving on. Optional jq warm-up if time allows.

---

## Block 2 · Guided Sprint (90 min)

Pairs work through Parts 1–5 of the worksheet. Mixed pairing (tenured + newer) where possible. Everyone does the same technical steps; the assigned scenario shapes their demo framing.

- **Part 1 (15):** Run `dbt build`, explore docs/lineage
- **Part 2 (20):** Branch, edit `customers.sql`, rebuild, commit, push
- **Part 3 (15):** Open PR, swap, review each other's PR
- **Part 4 (10):** Watch CI run; break it on purpose, watch it go red
- **Part 5 (15):** Demo prep
- **Demo round-robin (15):** Each pair, 90 seconds. Customer context, what they built, one defensible decision. No deep critique — exposure, not judgment.

**Your job during the sprint:** circulate. Don't solve problems for people — ask the question that helps them solve it. Note who's flying and who's struggling for your 1:1 follow-ups. Capture good customer examples people mention — raw material for later.

---

## Block 3 · Architecture Walk (60 min)

Project 3 anonymized customer architecture diagrams. For each, 20 min:
- 5 min: you walk the stack — what's there, who built it
- 10 min: open discussion — where would an analytics platform fit? Who's the buyer? What objections surface? What would you demo first?
- 5 min: one SE summarizes the play in 60 seconds as if pitching a peer

This is the section the survey feedback asked for most. Let it breathe. If discussion is hot at the 55-min mark, steal time from the close, not from here.

---

## Block 4 · Commitment Round (30 min)

**Solo writing (10 min):** Each SE writes:
1. One customer in their current pipeline where this applies
2. The specific conversation they'll have differently
3. One question they still can't answer

**Share-out (20 min):** Round the room, ~90 sec each. Group reacts with suggestions or related experience. The fact that everyone hears each other's commitments creates follow-through pressure.

---

## Block 5 · Close + Lunch (10 min)

- Recap the 2-3 patterns the room kept hitting (you've been taking notes)
- Confirm Module 4 (APIs & auth) launches next; post-program survey at the end
- Lunch is part of the lab — keep them around for the casual conversation

---

## After the day

- Post a thread recap in `#se-book-club` with the customer examples that came up
- Add anyone's strong "I'll apply this to deal X" commitments to your behavioral-evidence log
- Note what dragged and what landed — feeds your one-pager and the next cohort
