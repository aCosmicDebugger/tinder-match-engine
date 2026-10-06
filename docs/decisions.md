# Project decisions

## Adult-person visual preference as the initial domain

Date: 2026-10-06

The first experiment ranks images of adult people according to explicit individual feedback. Use frozen pretrained embeddings, a positive-preference centroid and random ranking as initial benchmarks. Build a local gallery and evaluate on unseen identities with independently collected labels.

The source and checkpoint remain pending selection in data foundations. Actual image use must follow the selected source's terms. Synthetic portraits are a possible fallback, with explicitly limited transfer claims.

The modeled outcome is preference for an image. It does not imply mutual interest or compatibility. Automation is a later separate extension.