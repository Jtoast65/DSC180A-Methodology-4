---
layout: default
---

# Joey Sandoval

**Email:** [jrs004@ucsd.edu](mailto:jrs004@ucsd.edu)

**Section:** D04

**Mentor:** Biwei Huang

---

**1. What is the most interesting topic covered in your domain this quarter?**

The topic I found most interesting was leakage, and how much harder it is to prevent than it first sounds. Going in, I assumed that keeping a forecasting agent honest just meant hiding any document dated after the simulated time. Working on WorldReset showed me that the date on a record is often the wrong date. A Treasury rate or an EIA price has an observation date, but what matters is the moment the number was actually published, and for some releases that moment is a scheduled time on a provider's calendar page. Revisions complicate it further, since a value can change after its first print, and a question has to settle on the version that existed at the time. Leakage can also slip through indirectly, through search rankings, result counts or snippets that hint at what happened later. Learning to think about "when did this become public" as its own variable changed how I look at almost any time series dataset.

**2. Describe a potential investigation you would like to pursue for your Quarter 2 Project.**

I'd like to use the energy and rates sources I built to test whether LLM forecasting agents can actually beat simple baselines on numeric questions. The setup would be quant questions about values like weekly gasoline prices, crude prices or the 10-year Treasury yield, asked at a fixed As-of time with a few horizons out. The agent would only see records that were public at that time, through the environment's search and read tools, and would submit quantiles for each horizon. I would compare it against a random walk, a seasonal naive forecast and, for the EIA series, EIA's own Short-Term Energy Outlook, scoring everything with CRPS and pinball loss. The question I care about is whether retrieving the news and releases around a value helps the agent's distribution, or whether it mostly adds noise compared to just extending the trend.

**3. What is a potential change you'd make to the approach taken in your current Quarter 1 Project?**

I would build the question side in parallel with the sources instead of after them. This quarter we focused almost entirely on getting Sources right: adapters, release-time evidence, gaps and tests that confirm nothing is visible early. That work is solid, but it meant we chose and split sources without knowing exactly which questions they would need to resolve. If I did it again, I'd draft a small question set first and let it decide which series, horizons and release versions each adapter has to cover. I would also try to collect release-time evidence once per provider instead of once per source, since my eight sources came from only three providers and the six EIA ones already share helper code.

**4. What other techniques would you be interested in using in your project?**

On the forecasting side I'd like to try quantile regression and gradient-boosted quantile models as stronger baselines than a random walk, so the agent has something real to beat. Conformal prediction also interests me as a way to check whether an agent's intervals hold their stated coverage. For retrieval, I want to compare exact BM25 with the hybrid BM25 plus dense embeddings setup the environment supports for news, and see whether it changes which records the agent reads and how good its forecasts are. Given my mentor's work on causal discovery, I'd also like to look at causal methods for time series, for example testing whether crude price movements help explain later gasoline prices beyond what gasoline's own history predicts.
