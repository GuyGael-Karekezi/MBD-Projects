# Project 3 Write-Up

## Overview
Project 3 extends the extremism-detection work from Assignment 2 into a multi-part moderation pipeline:
- Part A: violent extremism versus non-violent extremism classification
- Part B: prompt-based severity scoring using zero-shot and chain-of-thought prompting
- Part C: persona-driven counter-narrative generation and evaluation

## Part A Insights
### Balanced VE/NVE file
The final submission file `ve_nve_classifications.csv` was intentionally balanced:
- 50 VE examples
- 50 NVE examples

### Extremism subtype distribution
Among the VE rows in the final file:
- Political VE: 26
- Ideological VE: 20
- Religious VE: 4

Political VE was therefore the most common subtype in the final sample.

### Target-group patterns
The most common extracted target label was `Unclear`, which indicates that many posts did not name one explicit target cleanly enough for reliable extraction. Among clearly identified targets, Muslims appeared most often, followed by doctors, immigrants, Black people, and refugees.

### Model behavior
The fallback Part A model was conservative when assigning VE labels. In the larger candidate pool, it labeled far more examples as NVE than VE, which is why a larger scan pool was needed to assemble the final balanced file.

## Part B Insights
### Prompt agreement
Prompt agreement improved when temperature was reduced:
- Zero-Shot vs CoT agreement at temperature 1.0: 63%
- Zero-Shot vs CoT agreement at temperature 0.4: 77%

This suggests that lower temperature made severity predictions more stable and less sensitive to prompt-style differences.

### Explanation length
CoT prompting generated longer explanations than Zero-Shot prompting:
- Zero-Shot average explanation length: 50.52 words
- CoT average explanation length: 60.39 words
- Difference: about 9.88 words (+19.5%)

This is consistent with CoT encouraging more explicit reasoning steps.

### Temperature effect on verbosity
Temperature had a smaller effect on explanation length than prompt style:
- Temperature 1.0 average: 54.39 words
- Temperature 0.4 average: 56.52 words

So the main driver of explanation length was CoT prompting, not temperature alone.

### Part B conclusion
The best tradeoff in Part B was CoT with lower temperature, because it improved agreement while keeping explanations detailed and interpretable.

## Part C Insights
### Important model-run note
Although four models were configured, the final saved comparison set contained successful generations only from:
- `gpt4_mini_rlhf`
- `claude_haiku_budget`

Therefore, the final quantitative comparison in Part C is based on these two successful models.

### Verbosity patterns
Verbosity varied strongly by both model and persona:
- `claude_haiku_budget` average length: 199.38 words
- `gpt4_mini_rlhf` average length: 101.89 words

Across both models, the longest responses usually came from the Compassionate NGO and Educator personas, while Vanilla produced the shortest outputs.

### Clarity scoring
The assignment originally specified `gpt-4o-mini` for LLM clarity scoring, but that judge model was unavailable through the gateway during this run. The notebook therefore used the fallback judge:
- `openai/gpt-4.1-mini`

All 645 saved counter-narratives in the final analysis set were scored successfully.

### Clarity comparison
The mean LLM clarity scores were:
- `gpt4_mini_rlhf`: 4.216
- `claude_haiku_budget`: 3.885

This means `gpt4_mini_rlhf` produced clearer outputs overall for the target 8th-grade audience.

### Readability vs clarity disagreement
Traditional readability metrics and LLM clarity disagreed often:
- correlation between Flesch-based readability and LLM clarity: 0.121
- examples with a gap of at least 2 points: 611

This shows that surface-level readability formulas do not fully capture whether a counter-narrative is actually understandable and useful.

### Verbosity vs readability relationship
The relationship between length and quality depended on the metric:
- word count vs Flesch Reading Ease: weak positive correlation (r = 0.180)
- word count vs LLM clarity: moderate negative correlation (r = -0.502)

In practice, much longer responses were often judged less immediately clear by the LLM evaluator.

### Task 3 conclusion
Between the best available successful models from Task 1 and Task 2, `gpt4_mini_rlhf` was the strongest overall performer because it achieved the highest LLM clarity while remaining much more concise than `claude_haiku_budget`.

## Final Takeaway
This assignment shows that extremist-content analysis benefits from combining multiple methods:
- structured classification for VE/NVE and subtype detection
- prompt-based severity labeling for richer moderation analysis
- counter-narrative generation evaluated with both conventional and LLM-based metrics

A key lesson from the results is that semantic clarity matters more than formulaic readability when evaluating counter-narratives. Concise, focused responses were often more effective than longer, more elaborate ones.
