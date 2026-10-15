# privateisnotprivileged_updated
Updated paper I tried submitting to Neurips workshop, below is the feedback received by reviewer (unedited)

Summary

This paper argues that an observed advantage of activation monitors over text monitors does not, by itself, establish a representation-specific advantage. On a binary action-prediction task built from released Diplomacy states, the activation reader beats text observed before deliberation, but loses to the same observer once it receives the deliberation preceding the activation. Text also has lower Brier loss at every tested matched cutoff. A repeated-trajectory experiment finds exceptionally strong late activation prediction, while changing the text readout substantially improves text performance. The authors distinguish decodability, accessibility, and predictive privilege, and argue that channel comparisons require explicit observation boundaries and reader specifications.

Strengths

(Significance) The paper addresses how evidence for hidden-state monitoring should be interpreted, which fits the workshop's focus.

(Quality) Fixing the trajectory, the activation record, and the realised action, and varying only what each observer sees, is a good way to isolate the boundary confound. The source game is used as the sampling unit, and the permutation control that rebuilds reader selection inside the null is a sensible check.

Weaknesses

(Major Weakness - Comparability) The readers differ substantially in supervision, capacity, and inference cost: the activation side uses a fitted probe, while the text side includes prompted observers, a likelihood scorer, and a supervised lexical model. This does not invalidate the controlled exposure and readout comparisons, but it limits what the resulting channel rankings establish. As the authors acknowledge, no matched frontier is estimated. The paper therefore demonstrates sensitivity to particular comparison choices without establishing how the channels compare under similar resource constraints. Separately, the family and scale extensions reuse the same source states and provide robustness checks rather than independent dataset replication.

(Major Weakness - Coverage) The activation analysis selects among layers and a small set of token summaries, but does not evaluate readers over sequences of hidden states across tokens or layers. I would expect some useful predictive structure to lie in how these states evolve, and the selected summaries may miss that structure. The text observer, by contrast, receives the available deliberation as a sequence. The temporal-summary sensitivity analysis is useful, but does not directly address this concern. Thus, matching the observation boundary leaves an asymmetry in how the available evidence is represented, which could contribute to the observed ordering.

(Weakness - Reproducibility) The appendix describes layer selection, temporal summaries, standardisation, and grouped fitting, but does not specify the residual-stream extraction point within each block, the layer-index convention, or the exact token position relative to the delimited choice field. The paper explicitly reports capture before action generation and complete-state holdout. Given the near-zero trajectory prediction loss, exact prompt templates and extraction details are nevertheless important for independently verifying these safeguards and interpreting the signal as late output preparation.

Overall assessment

The question is interesting and suits this workshop. The experiments show that observation boundaries and readout choices matter, but I am not yet convinced that the comparison sufficiently separates representation effects from reader limitations. I would not object to acceptance, but I would prefer the broader framing to be narrowed: the evidence establishes sensitivity to the tested comparison design more clearly than it resolves the underlying question of representational advantage.

Rating: 2: Marginally below acceptance threshold and I have given specific indicators to move the paper above the threshold.
Confidence: 3: The reviewer is confident but not absolutely certain that the evaluation is correct
