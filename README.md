# Verity

AI-assisted pre-submission review for project materials.

[Live demo](https://cyrilla-mist.github.io/verity/) · [Portfolio](https://cyrilla-mist.github.io/portfolio/)

## Overview

Verity helps project teams inspect materials before submission or presentation. It first builds a structured understanding of the project, then checks evidence coverage, likely reviewer concerns, scoring dimensions, and revision priorities.

The product is designed to make AI review more inspectable than a single free-form score or generic paragraph of feedback.

## Core Flow

```text
Submit material
  → Build project understanding
  → Inspect evidence coverage
  → Simulate structured review
  → Generate prioritized revision actions
```

## Features

- **Material input** — enter a project summary directly or upload DOCX / TXT files.
- **Browser-side parsing** — extracts DOCX / TXT text before analysis.
- **Project understanding** — summarizes the problem, target users, solution, technical route, current evidence, and major gaps.
- **Evidence coverage** — separates recognized evidence from missing information.
- **Five review dimensions** — evaluates innovation, user value, technical credibility, business or adoption value, and presentation completeness.
- **Evidence-risk analysis** — flags unsupported numbers, weak sourcing, absolute claims, and missing outcome evidence.
- **Likely reviewer questions** — surfaces questions a team should be prepared to answer.
- **S / A / B action list** — groups revision work by priority.
- **Example rewrites** — improves wording without intentionally adding unsupported facts.
- **Report copy** — exports the structured result as copyable text.
- **Responsive UI** — supports desktop, mobile, light, and dark themes.

> Current file support: **DOCX and TXT**. PDF is not supported in this release.

## Consistency Rules

Verity does not rely only on model-generated summary numbers. Several output constraints are normalized in code:

- the overall score is derived from the five dimension scores;
- score bands follow fixed mappings;
- risk, question, and action counts are derived from actual returned items;
- evidence coverage is calculated from covered and missing evidence categories;
- dimension scores are restricted to fixed ranges;
- prompt rules prohibit unsupported additions such as fabricated data, results, algorithms, partnerships, business models, or product features.

These rules do not make the review objective, but they reduce avoidable inconsistency between the narrative and displayed report structure.

## Technology

- HTML
- CSS
- JavaScript
- Cloudflare Worker
- DeepSeek API
- GitHub Pages

The frontend prepares the material and sends it through a Cloudflare Worker. API credentials remain on the server-side boundary rather than in the public frontend.

## Repository Structure

```text
index.html              Page structure
css/style.css           Styling and responsive layout
js/app.js               Input, file parsing, requests, and report normalization
js/data.js              Demo data
js/render.js            Report rendering
js/vendor/              DOCX parsing dependency
worker/index.js         Worker request and response normalization
worker/prompt.js        Review rules, schema, and factual-safety constraints
```

## Usage

1. Choose the project type and enter a project name.
2. Upload DOCX / TXT material or enter the project summary manually.
3. Add optional context such as users, solution, innovation, results, technical route, or evidence.
4. Run the review.
5. Inspect the project summary, evidence coverage, risks, reviewer questions, and prioritized actions.
6. Verify all consequential facts and decide which recommendations to adopt.

## Limitations

Verity is a review aid, not an authoritative scoring system. It cannot predict a real competition result or replace expert review.

AI-generated interpretation remains probabilistic. Facts, data, claimed outcomes, and other consequential statements should be checked against the source material before use.

Do not upload personal identifiers, confidential research data, or other sensitive information.

## Version

Current public code version: **v0.4.7**

## Author

Cyrilla

© 2026 Cyrilla
