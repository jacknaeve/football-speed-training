# A/B Test Plan: Price of the Speed Assessment

Written November 9, 2026, before any trial was run and before any data was collected. Site: https://jacknaeve.github.io/football-speed-training/

## 1. Page and single element
- **Page:** index.html (home page), in the "Programs and prices" table.
- **Element changed:** the price of the Speed Assessment, one number in one table cell. Nothing else differs.
- **Version A (current):** Speed Assessment, 45 minutes, **$25**
- **Version B:** Speed Assessment, 45 minutes, **$15**
- **Why this element:** the Speed Assessment is the cheapest, first step into the business, and the home page has no call to action, so the price in the table is the main thing a visitor weighs before deciding to try it. A new business with no reviews asks a parent to trust a stranger, and a lower entry price reduces the risk of that first step. Price is also the element a business can change at no design cost, so the result would be useful.

## 2. Hypothesis
Version B ($15) will get a higher "Yes" rate than Version A ($25), by at least 10 percentage points. This prediction fails if B's rate is within 10 points of A's, or lower, which would mean a $10 cut does not move willingness to book. Reasoning: a lower price lowers the cost of trying an unknown business.

## 3. Model, persona, prompt, assignment
- **Model:** Claude (Anthropic), the same model and default settings in every trial. Each trial is a new conversation with memory switched off, so no trial can see an earlier one. The model name and the date are recorded on every row, so a change of model during the test can be seen.
- **Persona:** the parent of a 16-year-old high school football player who ran a 5.1-second 40-yard dash.
- **Exact prompt (identical in every trial except the page text):**

> You are the parent of a 16-year-old high school football player who ran a 5.1-second 40-yard dash and wants him faster before next season. You found the web page below while searching Google. Read it and decide whether you would book a Speed Assessment from this business. Answer with the single word Yes or No on the first line, then one sentence of reasoning.
>
> PAGE:
> [full text of the page]

The prompt does not mention a price, so the only difference between trials is the page text.
- **Page given:** the full page text, pasted in the same position every time (page-a-text.txt or page-b-text.txt).
- **Assignment:** before running anything, I generated a random order of 60 A and 60 B trials with a seeded random shuffle (seed 20261105) and saved it as trial-assignment.csv. Trials follow that order from row 1.
- **Variant page protection:** index-b.html has a noindex tag and is not in sitemap.xml.

## 4. Primary outcome
"Would you book a Speed Assessment from this business?" Each trial is coded 1 for Yes and 0 for No, from the first word of the model's answer. The measure is the percentage of Yes answers in each version, compared with a two-proportion test. Scoring rule, set before seeing any answer: only an answer that starts with "Yes" scores 1. Every other answer, including a hedge such as "Maybe", scores 0. The raw answer stays in the file and no trial is ever rerun.

## 5. Sample size and timing
60 trials per version, 120 in total, above the required 50 per version. I will run all 120 and will not look at results or stop early. Expected completion: November 13, 2026. The test launches before the November 17 deadline. With this many trials, only a gap of roughly 25 points or more is likely to show up as significant, so a smaller true effect may not be detected.

## 6. Comparison and what counts as support
I will compare the yes share in B with the yes share in A (B minus A) using a two-sided two-proportion z test, and report the difference, its 95 percent interval, and the p value. The hypothesis counts as supported only if B's yes share is at least 10 percentage points above A's and p is below .05. Anything else is reported as not supported, and a flat result will be reported as such. If I change anything after launch, I will state the date and the reason in the report.
