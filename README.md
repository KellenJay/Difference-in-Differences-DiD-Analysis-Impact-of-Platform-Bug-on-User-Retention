## Experiment: Measuring the Impact of a Suspected Platform Bug Using Difference-in-Differences (DiD)

Designed to assess whether a platform bug in April 2020 disrupted onboarding and early engagement behavior.

---

### 1. Goal & Funnel

**Problem:** A suspected platform bug allowed lessons to be completed unrealistically fast (<5 seconds), possibly confusing learners.

**Objective:** Use Difference-in-Differences (DiD) to evaluate whether the bug negatively affected user retention and engagement.

**User Funnel:**
`First Lesson → Time to Next Lesson → Return Activity → Course Continuation`

A disruption early in this funnel may break learner momentum and reduce retention.

---

### 2. Define Metrics

**Primary Metric:**
- *Average weekly active learning days per user* — reflects early engagement consistency.

**Secondary Metrics:**
- *Average time between first and second lessons* — proxy for user motivation and return intent.
- *Active user count in subsequent weeks* — early retention indicator.

**Guardrail Metrics:**
- *Number of completions under 5 seconds* — system anomaly proxy.
- *Support ticket volume or flagged events* — friction or confusion indicator.

---

### 3. Experimental Design (DiD)

**Why DiD?**
This wasn’t a randomized experiment — the bug naturally affected users starting in April. DiD allows us to estimate the impact by comparing before/after differences between affected and unaffected groups.

**Setup:**
- **Treatment Group**: Users who began their first lesson in *April 2020*
- **Control Group**: Users who began their first lesson in *March 2020*
- **Pre-period**: March
- **Post-period**: April

**DiD Formula:**

\[
\text{Effect} = (\text{Post}_{Treatment} - \text{Pre}_{Treatment}) - (\text{Post}_{Control} - \text{Pre}_{Control})
\]

**Assumptions:**
- Engagement trends were **parallel pre-bug** across cohorts.
- No other significant product or marketing changes occurred in April.

---

### 4. Results Summary

- The DiD interaction term was **statistically significant and negative**.
- **Treatment group engagement dropped sharply** post-bug compared to the control.
- April users had **~1.8 fewer active learning days per week** vs what we'd expect without the bug.

| Group      | Period | Avg Active Days |
|------------|--------|------------------|
| Control    | Pre    | 1.33             |
| Control    | Post   | 1.35             |
| Treatment  | Pre    | 3.78             |
| Treatment  | Post   | 1.96             |

---

### 5. ⚖Discuss Trade-offs

#### Pros:
- Uses **real-world platform behavior** — no artificial constraints.
- Enables **causal inference** without randomized testing.
- Supports **strategic response planning** post-crash.

#### Risks:
- Relies on **parallel trend assumption** — bias possible if pre-bug behaviors differ.
- Vulnerable to **external confounders** (seasonality, marketing).
- Possible **measurement noise** due to bugs or tracking issues.

#### 🛠Mitigations:
- Validate with **multiple behavioral metrics**.
- Monitor **guardrail signals** like flagged completions.
- Run **segment analysis** across professions and platforms.

---

### Final Recommendation

If DiD findings hold, the team should:

- Investigate **April 2020 platform logs**
- Patch lessons or flows impacted by the bug
- Launch **onboarding recovery nudges** for affected users
- Integrate **automated regression tests** for future feature releases


