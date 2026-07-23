# Week 2 — Task 2: Think Step-by-Step — Chain-of-Thought & Persona Prompting

**Aila Nasir · Generative AI & Prompt Engineering Intern · NeuroFive Solutions**

## Objective
To compare a plain, direct prompt against a Chain-of-Thought (CoT) prompt combined with a persona, on the same business decision scenario, and evaluate whether reasoning quality and accuracy improve even when the final recommendation stays the same.

## Scenario
A startup has $60,000 to spend this quarter. Option A: hire 2 ML engineers to reduce monthly churn from 8% to 6.8% (current user base: 2,000). Option B: spend on marketing at $120 CAC to acquire 500 new users, with average customer LTV of $300. Which option maximizes revenue impact over 6 months?

## Prompt Used — Run 1 (Plain, No Reasoning Instruction)
A startup has $60,000 to spend this quarter. Option A: hire 2 ML engineers to reduce monthly churn from 8% to 6.8% (current user base: 2,000). Option B: spend on marketing at $120 CAC to acquire 500 new users, with average customer LTV of $300. Which option should they choose to maximize revenue impact over 6 months?

## Output — Run 1
Option A (Reduce Churn): Extra users retained per month ≈ 24 (2,000 × 1.2%). Using a month-by-month linear approximation over 6 months, total additional user-months ≈ 139. At an LTV of $300, revenue impact ≈ $41,700. Net impact against the $60,000 spend ≈ −$18,300 within 6 months.

Option B (Marketing): 500 new users at $120 CAC ($60,000 total spend). Revenue = 500 × $300 = $150,000. Net value created = $150,000 − $60,000 = $90,000. ROI = 2.5×.

Recommendation: Option B (Marketing) — generates approximately $150,000 in LTV versus an estimated $41,700 from churn reduction over six months. Caveat noted: if the company operates well beyond six months, churn reduction could become the stronger long-term choice since retention improvements compound over time.

## Prompt Used — Run 2 (Chain-of-Thought + Persona)
You are a senior startup growth strategist with 15 years of experience advising early-stage companies on resource allocation. Think step by step before giving your final answer.

A startup has $60,000 to spend this quarter. Option A: hire 2 ML engineers to reduce monthly churn from 8% to 6.8% (current user base: 2,000). Option B: spend on marketing at $120 CAC to acquire 500 new users, with average customer LTV of $300.

Walk through the math for both options, compare their financial impact over 6 months, then give your final recommendation.

## Output — Run 2
Option A (Reduce Churn) — Step 1: Monthly users lost at 8% = 160; at 6.8% = 136; difference = 24 additional users retained per month. Step 2: Applied compound retention over 6 months using (1 − churn rate)^6. Current retention: 0.92^6 ≈ 0.606 → ~1,212 users remain. Improved retention: 0.932^6 ≈ 0.655 → ~1,310 users remain. Difference ≈ 98 more active customers after 6 months. Step 3: Revenue impact = 98 × $300 ≈ $29,400.

Option B (Marketing): 500 users acquired at $120 CAC ($60,000 spend). Revenue = 500 × $300 = $150,000. Net value = $150,000 − $60,000 = $90,000.

Recommendation: Option B (Marketing) is the stronger financial choice over a 6-month horizon, producing $90,000 in net value versus a shortfall from Option A within the same window. Strategic caveat noted: if churn reduction is permanent and compounds over multiple years, or improves expansion revenue and referrals, hiring engineers could become the higher-return investment long-term. Under the stated 6-month horizon and given numbers, Option B remains the recommended choice.

## Comparison

| Metric | Plain Prompt (Run 1) | CoT + Persona Prompt (Run 2) | Notes |
|---|---|---|---|
| Reasoning method | Simple linear decline (month-by-month approximation) | Compound decay formula: (1 − churn rate)^6 | Run 2 used the mathematically correct approach |
| Extra users retained (6 months) | ~139 (overestimated) | ~98 (accurate) | Significant gap in accuracy |
| Revenue impact estimate (Option A) | $41,700 | $29,400 | Run 1 overstated Option A's value |
| Explicit step labeling | No — jumps straight to a table | Yes — "Step 1", "Step 2", "Step 3" | Improves auditability of the reasoning |
| Final recommendation | Option B (Marketing) | Option B (Marketing) | Same conclusion, different rigor getting there |

## Analysis
Both the plain prompt and the CoT + persona prompt arrived at the same final recommendation (Option B: marketing). However, the underlying math differed significantly. The plain prompt approximated churn reduction using a simple linear decline across 6 months, overestimating the benefit at $41,700. The CoT + persona prompt applied the correct compound retention formula (1 − churn rate)^6, producing a more conservative and mathematically accurate estimate of $29,400. In a real business decision, this gap matters: even when the final recommendation doesn't change, a decision-maker needs the more defensible number to justify the choice to stakeholders, and CoT prompting delivered that rigor by explicitly working through the math step by step rather than approximating.

## Submission Links

**GitHub Repo:** https://github.com/ailanasirai/neurofive-genai-internship

**Full Doc (Google Docs):** https://docs.google.com/document/d/1TvD_0hbMeyU82-ltFWSl-pV7AWJkhe7VDWbRNhPj-qE/edit?usp=sharing

**LinkedIn Profile:** https://www.linkedin.com/in/aila-nasir/
