# Task Track proposal

## 1. Task and domains

- **Authors / GitHub handles (required):** Xin Yu (@LucasXinYu)
- **Short task title (required):** Adapt a saved solo ride when a child joins
- **Primary domain (required):** Fitness & wellbeing
- **Secondary domains (optional):** None

## 2. User persona and prior history

✍️ **Your answer (required):** A software engineer reads technical mountain-bike ride reports and keeps a collection of solo training routes. On family rides, their eight-year-old daughter rides her own bike. An earlier family ride log records her six-kilometre outing and the parent's instructions for their next ride together: up to eight kilometres, paved throughout, separated from motor traffic, with a lake view if available. These limits belong to this fictional family.

## 3. Story outline

✍️ **Your answer (required):** On Thursday the parent asks the assistant to save a technical route for Saturday. On Friday the daughter joins. The parent asks for an update without repeating the family constraints. On Saturday a trail bulletin may change one segment. The assistant must check it, update the saved outing and tell the parent what is actually saved. If a detour compromises the family's requirements, another qualifying route is welcome. If none remains, the parent has authorized postponing. A matched control keeps Saturday a solo ride. The solo collection should survive all edits.

## 4. What makes this distinct and personal

✍️ **Your answer (required):** The same browsing history is relevant to the same rider on both days. What changes is whose needs the route must meet. A short route marketed as a family lake loop includes a mixed-traffic connector. Another lake route exceeds the family's distance limit. When a lakeside path qualifies, the daughter's preference decides the choice. When it closes or gains a detour, the parent still wants the other constraints respected. Selecting a suitable route for this outing and retaining the parent's solo preferences are separately observable outcomes.

## 5. Construction plan and effort

✍️ **Work breakdown (required):**

| Workstream | Planned work and scale | Deliverable / quality check | Effort (person-days) |
| --- | --- | --- | --- |
| Persona, history and workspace | Author a synthetic browser history, family ride log, two saved-route lists and six route cards with segment evidence. | Each decision can be traced to a user record, route detail or dated bulletin. Check for identifying information. | 0.5–1 |
| User rollout and scenario script | Sessions: 3. Simulated world time span: about 48 hours. Estimated total tokens: 4,000–8,000 per scenario including dialogue, retrieved history, route details and tool output. Cross two riding parties with three bulletin states. | Release the party update and bulletin at their scheduled times. Carry saved routes across sessions. Script responses to clarification and preserve equivalent choices. | 1 |
| Environment integration | Map route lookup, bulletin lookup and edits to a saved outing and solo collection onto the PALE interfaces. | Fresh reset, controlled replay, and visible confirmation of persisted edits. Recheck adapter availability at infrastructure release. | 1–2 |
| Rubrics, reference and hints | Score initial solo plan (20), party update (25), current saved route (30), accurate final response (15) and preserved solo collection (10). Full success requires all five. | Accept multiple routes that satisfy the same constraints. Check a no-op and misleading route labels. Use a fixed hint pointing to the scope of past ride records and the date of the bulletin. | 1 |
| Agent rollouts and analysis | Freeze the task, scenario schedule, designated model versions, settings and budget. Plan at least one fresh unhinted run and one separate fixed-hint run per designated GPT, Claude and Gemini model. | Report every trace, score, budget and failure. Each model must have zero unhinted full passes and a mean below 50% for the standard tier. Each hinted run must pass all gates and earn 100%. | 1–2 |

- **Milestones, owners and dependencies (required):** Xin Yu would own fixture development, grading and failure analysis. After design approval, finalize source records, integrate the environment, independently reproduce the reference and then evaluate the three models in this PR. Estimated duration is one to two working weeks after interfaces and evaluation access are available.
- **Resources and total effort (required):** Estimated 4.5–7 person-days. Synthetic data generation, reset, reference runs and deterministic grading use a CPU. The local pilot used no model calls. Formal model access and cost are TBD. Confirm an approved access route with maintainers, then estimate token costs from the designated roster and frozen run budget.
- **Scope boundary and open questions (required):** One synthetic household, one local route catalogue and one saved Saturday outing. Please advise which route catalogue and saved-list interfaces to target. The CPU pilot consumes structured route facts and emits structured trip status. Interpretation of narrative source documents, natural-language replies and human-independent reproduction remain for implementation review.

**CPU pilot evidence.** Two deterministic reference policies each earned 100/100 in all six worlds, including two different qualifying detours. Six scripted controls exercised known errors. The history-only and family-label policies each passed the three solo worlds and failed all three family worlds. Ignoring the latest bulletin passed four of six. Always choosing a family route and taking no action each passed zero. Erasing the solo collection failed all three family worlds. Two fresh Python processes produced byte-identical traces for the 48 policy/world combinations. These results establish feasibility and grader behavior. Designated GPT, Claude and Gemini results are pending.
