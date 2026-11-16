# Task Track proposal

## 1. Task and domains

- **Authors / GitHub handles (required):** Xin Yu (@LucasXinYu)
- **Short task title (required):** Rerank a mountain biker's reading list when his daughter joins
- **Primary domain (required):** Fitness & wellbeing
- **Secondary domains (optional):** Shopping & groceries

## 2. User persona and prior history

✍️ **Your answer (required):** A software engineer and experienced mountain biker spends weekends on demanding singletrack. His bookmarks cover steep descents and bike setup. He recently bought a full-face helmet for himself. There is also a youth helmet on a receipt in his name. His eight-year-old daughter can ride independently, has a bike that fits and owns a water bottle. Her family's notes describe a short recreational ride with a stop and easy terrain away from motor traffic.

## 3. Story outline

✍️ **Your answer (required):** On Thursday the father asks for five posts to read before a solo training ride. On Friday his eight-year-old daughter Nora joins the ride and he asks the assistant for a new top five from the same 24 posts. A kit check says Nora has outgrown her red helmet. A receipt shows the father paid for a blue Tyro. A collection slip records a successful fit on the child who took it home. Only the family chat identifies that child. In one version the chat says Tess, Nora's cousin. In the other it says Nora. When Tess took it home, Nora still needs fit and comparison guides. When Nora took it home, the father can use those slots for ride planning and checking the gear they own. The request asks for a one-sentence reason per post and reserves shopping guides for genuinely missing items.

## 4. What makes this distinct and personal

✍️ **Your answer (required):** Whose ride is being planned and who received a purchase can reverse the relevance of the same post. An expert descent guide belongs near the top for the father alone. A youth race post contains both “youth” and “downhill” but helps neither weekend. A real lakeside write-up describes a full 42 km intermediate circuit. A model-comparison article earns a place when Nora needs a helmet. A routine fit or safety guide can still help when she owns one, but a replacement catalogue would take up a slot she asked to use elsewhere. The father still likes technical riding. Only the list for this outing changes.

## 5. Construction plan and effort

✍️ **Work breakdown (required):**

| Workstream | Planned work and scale | Deliverable / quality check | Effort (person-days) |
| --- | --- | --- | --- |
| Persona, history and workspace | Freeze 24 linked candidate cards with original short descriptions. Use one synthetic father, a dated ride brief, saved posts, purchase receipts and family messages. | Separate agent-visible records from private judgments. Check sources, duplicates, intended recipients and reuse terms. | 1–2 |
| User rollout and scenario script | Two sessions over about 24 simulated hours. A Thursday solo request precedes Friday's family update. Fork the Friday turn from a common Thursday state. Change one recipient name in the family chat, keeping the receipt, collection slip, kit check, card pool and request identical across Friday branches. Estimate 2k–5k tokens across a path including records, retrieved cards and replies. Measure actual use during integration. | Allow different retrieval orders and tied recommendations. A targeted question can clarify missing fit information. Shopping suggestions remain conditional on fit. | 1 |
| Environment integration | Expose search/read over the frozen feed and personal records, plus a saved top-five list. Reset both history and shortlist between independent trials. | CPU replay checks unique IDs, saved order and isolation of labels. Candidate-order permutations will test position shortcuts. | 1–2 |
| Rubrics, reference and hints | Privately label each card 0–3 for each context. Have two independent readers judge shuffled cards with the persona and task, blinded to model outputs. Adjudicate disagreements before freezing labels. | Score tied relevance with nDCG@5. Check family planning and basic kit in both branches. Require fit guidance and a comparison collection or two individual models when a helmet is missing. Exclude replacement-only pages from all five slots when Nora has a fitted helmet. Reject a junior downhill race in the family's top three. Review each reason against the records and the card. Preserve alternative valid lists. A fixed hint may direct attention to who is riding and who received the purchases. | 1–2 |
| Agent rollouts and analysis | Freeze cases, budget, models and grading. Run at least one unhinted and a separate hinted trial for each designated GPT, Claude and Gemini model. Record all trials. | Compare with a history-only ranker and a BM25 ranker using all context. Submit traces, costs, reason checks, official rubric scores and per-model pass rates. | 1–2 |

- **Milestones, owners and dependencies (required):** Xin Yu would own the corpus, scorer and failure analysis. Recruit two judges, freeze judgments, integrate the PALE runner after design approval and then run official validation. Estimated implementation time is one to two working weeks once judges, interfaces and model access are available.
- **Resources and total effort (required):** 5–9 person-days. Corpus construction and ranking metrics run on a CPU. Official model access and costs are TBD pending the designated roster, runner and token budget.
- **Scope boundary and open questions (required):** One contribution with paired contexts. Public articles and product pages provide reading material. The family and transactions are synthetic. Does the released runner support private graded judgments and saving a ranked list of IDs? What evaluation access is available to contributors?

**CPU pilot.** All three reference lists earn 1.000 nDCG@5 and pass the local checks. Among 5,100,480 possible ordered lists, the original rules allowed 36 identical lists to pass both family branches. The revised rules allow zero. Two individual model pages can still satisfy the comparison need, and a general fit check can still pass for a daughter who owns a suitable helmet. In the needs-helmet branch, history-only BM25 scored 0.000 and full-context BM25 scored 0.350 nDCG@5. The 95th percentile of 20,000 uniformly random lists was 0.660. With two shuffled card orders per context and a fresh process each time, Qwen2.5-1.5B-Instruct passed 0/6 local trials and Qwen3-4B-Instruct-2507 passed 0/6. Each model received all records and cards. The local score used the returned IDs.

**Evaluation plan.** The provisional local threshold is nDCG@5 of at least 0.80 with all required ID-level checks. The proposed full rubric allocates 70 points to ranking quality, 20 to need coverage and 10 to grounded reasons. It also requires five valid IDs, the ownership-specific shopping rule and no critical top-three mismatch. Independent judges, a full tool and memory replay, and the designated GPT, Claude and Gemini validations are pending. Freeze the rubric and judgments before the official runs.

For a future study over independently sampled families, pre-register the mean within-family nDCG@5 difference versus a frozen full-context baseline. Average repeated variants within family. Use a paired randomization test, a family-level 95% bootstrap interval and a predeclared minimum useful gain of 0.05. The current one-family pilot establishes no population-level significance.

Example sources: [family ride planning](https://www.cyclinguk.org/guide/family-bike-rides), [children's helmet options](https://www.giro.com/kids/cycling/helmets/), [technical cornering](https://www.rei.com/learn/expert-advice/cornering-techniques.html), [full Lakeside Way circuit](https://www.forestryengland.uk/kielder-forest/lakeside-way-kielder-forest).
