# P0-U01 Research Reflection: Researcher Mindset and Scientific Workflow

**Related assessment:** P0-A01

## 1. What did I think research was before this unit?

Before this unit, I thought AI research mainly involved identifying a problem, finding a solution, implementing it, and evaluating how well it worked. When a model performed poorly, I assumed the next step was to improve its architecture, adjust its parameters, or try another technique.

I understood that experiments mattered, but I had not fully appreciated the work that comes before an intervention: questioning the result, considering possible explanations, and deciding what evidence to seek.

## 2. What changed?

I now see research as a process of asking clear, testable questions and using evidence to reduce uncertainty. Improving performance can be useful, but I also need to explain what the result supports and what remains unknown.

This unit also helped me distinguish experimentation from research. Running an experiment produces a result; connecting that result to a research question, examining alternative explanations, and communicating its limitations helps build knowledge that others can examine and challenge.

## 3. What mistake in the lab taught me the most?

The mistake that taught me the most was moving too quickly from an observed performance difference to an explanation or proposed solution. In the P0-U01 lab scenario, the chest X-ray classifier had an AUROC of 0.94 on Hospital A's internal test set and 0.73 on Hospital B's external test set. My initial instinct was to improve the model before investigating the difference.

The gap described an observation. It did not establish its cause. Differences in image acquisition, preprocessing, patient populations, labels, or hospital-specific non-clinical features were possible explanations to investigate.

I learned that choosing an explanation too early can narrow my investigation around an assumption I have not tested. I need to consider competing explanations and ask what evidence would help distinguish them before deciding what to change.

## 4. What did the AUROC issue teach me about metrics?

The AUROC issue taught me to understand a metric before interpreting its value. I learned to describe AUROC in terms of discrimination or ranking: how well the model ranks positive examples above negative examples. The lab's two values showed a difference in measured discrimination across the evaluated datasets, but they did not explain why it occurred.

Before using a metric to guide my reasoning, I need to ask what it measures, what it leaves out, and which conclusions it can support. A proposed explanation must be compatible with what the metric measures, and it needs further evidence before I can treat it as an established cause.

## 5. What research habit am I taking forward?

I want to make a habit of understanding the metric and stating the observation clearly before proposing explanations. For each result, I want to ask:

- What do I know from the evidence?
- What remains uncertain?
- What competing hypotheses could explain the observation?
- What is the simplest diagnostic check that could distinguish them?
- What result would support or weaken each hypothesis?

Using these questions consistently should help me troubleshoot more independently and choose my next step with a clear reason. I want to carry this habit into reliable AI research, especially when investigating model behaviour across different settings.

## 6. What do I still need to improve?

I still need practice separating observation from interpretation, especially when an explanation feels intuitively convincing. I also want to become more confident in writing specific, falsifiable hypotheses and choosing informative experiments without unnecessary complexity.

I need to become more comfortable with uncertainty and negative results. When a result does not support my hypothesis, I want to examine what the test actually tells me, revise my confidence in the explanation, and use that evidence to decide what to investigate next.
