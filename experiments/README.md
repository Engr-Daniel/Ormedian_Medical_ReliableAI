# Experiment records

Store experiment definitions, configuration, metadata, and lightweight execution records here. Use stable IDs such as `P0-EXP-001` and link the related unit ID. A small standard-library activity is enough for Phase 0; training a model is not required.

Follow the record fields in [AGENTS.md, Section 9](../AGENTS.md): question, hypothesis, baseline, variables, controls, configuration, data and split if applicable, seeds, software/hardware, metrics, result, interpretation, limitations, and next experiment. Include the date and the command or steps needed to rerun the activity. Mark inapplicable fields explicitly.

Separate planned experiments from completed runs and retain distinguishing run identifiers when repeating an experiment. Link small derived tables in [results/](../results/README.md), visualizations in [figures/](../figures/README.md), and reasoning in [research-notes/](../research-notes/README.md). Do not duplicate outputs or place datasets, checkpoints, or large raw logs here.

The experiment template and first activity will be developed during Phase 0; no results are asserted by this scaffold.
