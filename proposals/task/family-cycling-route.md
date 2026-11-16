# Task Track proposal

## 1. Task and domains

- **Authors / GitHub handles (required):** Xin Yu (@LucasXinYu)
- **Short task title (required):** Rerank a mountain biker's reading list when his daughter joins
- **Primary domain (required):** Fitness & wellbeing
- **Secondary domains (optional):** Shopping & groceries

## 2. User persona and prior history

✍️ **Your answer (required):** A software engineer and experienced mountain biker spends weekends on demanding singletrack. His bookmarks cover steep descents and bike setup. He recently bought a full-face helmet for himself. There is also a youth helmet on a receipt in his name. His eight-year-old daughter can ride independently, has a bike that fits and owns a water bottle. Her family's notes describe a short recreational ride with a stop and easy terrain away from motor traffic.

## 3. Story outline

✍️ **Your answer (required):** On Thursday he wants five posts to read for solo training. On Friday his daughter joins the ride and he asks for an updated shortlist from the same 24 posts. A family message explains that the youth helmet was a gift for his niece and his daughter has outgrown hers. Reading about beginner kit, family ride planning and comparing children's helmets is now useful. A matched alternative changes only the receipt follow-up: the same helmet was for his daughter and already fits. She is still coming. Recommending replacements now wastes slots that could help them prepare. Each response ranks five distinct post IDs with one short reason per post. The task ends with the reading list.

## 4. What makes this distinct and personal

✍️ **Your answer (required):** Whose ride is being planned and who received a purchase can reverse the relevance of the same post. An expert descent guide belongs near the top for the father alone. A youth race post contains both “youth” and “downhill” but helps neither weekend. A real lakeside write-up describes a full 42 km intermediate circuit. A model-comparison article rises when a helmet is missing and falls when the daughter already has one that fits. The father still likes technical riding. Only the list for this outing changes.

## 5. Construction plan and effort

✍️ **Work breakdown (required):**

| Workstream | Planned work and scale | Deliverable / quality check | Effort (person-days) |
| --- | --- | --- | --- |
| Persona, history and workspace | Freeze 24 linked candidate cards with original short descriptions. Use one synthetic father, a dated ride brief, saved posts, purchase receipts and family messages. | Separate agent-visible records from private judgments. Check sources, duplicates, intended recipients and reuse terms. | 1–2 |
| User rollout and scenario script | Two sessions over about 24 simulated hours. A Thursday solo request precedes Friday's family update. Replay the Friday turn from the same starting snapshot with one changed receipt follow-up. Estimate 2k–5k tokens across a path including records, retrieved cards and replies; measure actual use during integration. | Keep the pool and request wording fixed; allow different retrieval orders and tied recommendations. A targeted question can clarify missing fit information. Shopping suggestions remain conditional on fit. | 1 |
| Environment integration | Expose search/read over the frozen feed and personal records, plus a saved top-five list. Reset both history and shortlist between independent trials. | CPU replay checks unique IDs, saved order and isolation of labels. Candidate-order permutations will test position shortcuts. | 1–2 |
| Rubrics, reference and hints | Privately label each card 0–3 for each context. Have two independent readers judge shuffled cards with the persona and task, blinded to model outputs; adjudicate disagreements before freezing labels. | Score tied relevance with nDCG@5. Also check coverage of outstanding needs, high-ranked mismatches and grounded one-line reasons. Preserve alternative valid lists. A fixed hint may direct attention to who is riding and who received the purchases. | 1–2 |
| Agent rollouts and analysis | Freeze cases, budget, models and grading. Run at least one unhinted and a separate hinted trial for each designated GPT, Claude and Gemini model. Record all trials. | Compare with a history-only ranker and a BM25 ranker using all context. Submit traces, costs, reason checks, official rubric scores and per-model pass rates. | 1–2 |

- **Milestones, owners and dependencies (required):** Xin Yu would own the corpus, scorer and failure analysis. Recruit two judges, freeze judgments, integrate the PALE runner after design approval and then run official validation. Estimated implementation time is one to two working weeks once judges, interfaces and model access are available.
- **Resources and total effort (required):** 5–9 person-days. Corpus construction and ranking metrics run on a CPU. Official model access and costs are TBD pending the designated roster, runner and token budget.
- **Scope boundary and open questions (required):** One contribution with paired contexts. Public articles and product pages provide candidate reading material; the family and transactions are synthetic. Does the released runner support private graded judgments and saving a ranked list of IDs? What evaluation access is available to contributors?

**Pilot evidence and proposed thresholds.** The CPU pilot used 24 distinct public sources. In the family-needs-helmet condition, history-only BM25 scored 0.000 nDCG@5, full-context BM25 scored 0.600, and the 95th percentile of 20,000 uniform random lists was 0.660. Judgments are an authoring draft. No designated model has run. A provisional local quality target is nDCG@5 of at least 0.80 plus required topic coverage. The proposed full rubric gives 70 points for normalized ranking quality, 20 for context-specific coverage and 10 for grounded reasons. A full pass also requires valid IDs and no critical top-three mismatch. The target and labels will be calibrated on development data and frozen before testing. PALE's official unhinted and hinted qualification rules apply separately.

For a future study over independently sampled families, pre-register the mean within-family nDCG@5 difference versus a frozen full-context baseline. Average repeated variants within family. Use a paired randomization test, a family-level 95% bootstrap interval and a predeclared minimum useful gain of 0.05. The current one-family pilot establishes no population-level significance.

Example sources: [family ride planning](https://www.cyclinguk.org/guide/family-bike-rides), [children's helmet options](https://www.giro.com/kids/cycling/helmets/), [technical cornering](https://www.rei.com/learn/expert-advice/cornering-techniques.html), [full Lakeside Way circuit](https://www.forestryengland.uk/kielder-forest/lakeside-way-kielder-forest).
