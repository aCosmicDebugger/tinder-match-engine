# Tinder Match Engine

A visual preference-learning and ranking experiment using images of adults, pretrained image embeddings and explicit user feedback.

**Status:** foundations and architecture planning. Embeddings, ranking experiments and the interactive demo are planned; no performance results are claimed yet.

## Problem

Learn one user's expressed visual preferences from a small labeled collection and rank unseen candidate images. Measure whether the ranking improves over random ordering and how it changes as feedback accumulates.

The system models subjective preference for the displayed image. It does not estimate mutual interest, compatibility or the probability of a real-world match.

## First release scope

- A small, documented collection of adult-person images with permitted use.
- Versioned metadata, identity groups and duplicate checks.
- Frozen pretrained image embeddings and cosine similarity.
- A positive-preference centroid baseline compared against random ranking.
- Explicit like, dislike and skip feedback.
- Evaluation on unseen identities and a local ranked-gallery demo.

The image source and encoder checkpoint are pending selection. CLIP and SigLIP are candidates, not installed dependencies or completed components.

## Evaluation

Use a fixed identity-separated holdout. Report Precision@k and NDCG@k on independently labeled candidates, random-ranking results, label prevalence and uncertainty. The holdout does not update the preference representation. Track the number of training labels needed to achieve useful ranking quality.

## Data and limitations

The first experiment uses a curated source with documented licensing, provenance and permitted demo use. Source selection is part of the data-foundations phase. Synthetic portraits are a fallback with explicitly limited claims about transfer to real photographs.

Raw images and personal feedback remain outside Git. A shared demo must use images permitted for redistribution and synthetic/example preference profiles. Multiple photographs of the same identity must stay in the same evaluation partition.

Preferences can reflect pose, clothing, lighting and backgrounds. Results are user-specific, context-dependent and subject to label inconsistency.

## Development setup

Python 3.11 and uv are required. From the repository root:

```bash
uv sync --locked
uv run --locked ruff check .
uv run --locked pytest
```

These commands validate the current engineering setup; they do not download images or train a ranking model.

## Roadmap

After the baseline: compare use of positive and negative feedback, implement preference learning, investigate active learning and add ranking diagnostics. UI automation and conversational personalization are later, separately evaluated extensions.

See [docs/architecture.md](docs/architecture.md) and [docs/decisions.md](docs/decisions.md).