# Project structure and collaboration

This document covers research directories, versions, submissions, and collaboration. The Chinese version is the source for this translation. [中文](PROJECT_STRUCTURE_CN.md) · [Paper formats](PAPER_FORMAT.md)

## 1. Repository root

| File or directory | Readers | Purpose |
| --- | --- | --- |
| README.md and readmeCN.md | People | Motivation, participation, and short startup prompts |
| AGENTS.md and AGENTS_CN.md | Agents | Workflow and delivery instructions |
| BACKGROUND.md and BACKGROUND_CN.md | Both | Definitions, original method, questions, research routes, and priorities |
| PROJECT_STRUCTURE.md | Both | Paper directories, versions, submissions, and collaboration |
| PAPER_FORMAT.md | Both | Research papers, reviews, and shared sections |
| reports/ | Both | Collection of community papers |
| arxiv_v1/ | Both | Source material for the original paper |
| briefs.md and briefsCN.md | Both | Historical setup record |

## 2. Paper collection

Use `reports/` as the collection root. It and its topic directories contain paper directories and more specific topic directories. Each paper and review has its own directory. Collection directories contain the entries themselves and may use an empty `.keep` as a placeholder.

Authors can put a paper directly in `reports/` or in a suitable existing topic. Research-paper authors who believe their paper introduces a new submethod can create a topic directory for that paper. Review authors choose an existing topic or the collection root for their own review directory.

```text
reports/
  paper_<unclassified_method>/
    paper.md
  review_<topic>/
    review.md
  <topic>/
    paper_<identifier>/
      paper.md
      si.md
      figures/
        comparison.svg
      src/
    paper_<identifier>_v_2/
      paper.md
    review_<topic>/
      review.md
    <more_specific_topic>/
```

Use a new directory for each paper and version. Research-paper directories begin with `paper_`, and review directories begin with `review_`. Choose a recognizable identifier and location before the first commit. Write the paper and accompanying descriptions in English. Put figures, SI, code, and other attachments in the paper directory and link them from the manuscript. Keep work notes and temporary experiments in a separate working location.

### Starting topics

| Directory under reports/ | Research direction |
| --- | --- |
| geometric_algorithms/ | Exact algorithms from coordinate geometry, with open-boundary clusters as a priority |
| shared_contractions/ | Reusable open intermediates and contractions shared across graphs |
| equivariant_expansions/ | Equivariant and invariant expansions with exact symmetries |
| separable_kernels/ | Separable kernels, related low-rank representations, and entrywise powers |
| ewald_and_fourier/ | Real-space and reciprocal-space splitting and Fourier methods for periodic and open systems |

Choose a primary home for work that spans topics. Established topic directories retain their names and positions and can receive additional papers and permitted subtopics. Ignore empty `.keep` files when looking for papers.

## 3. Find and organize reviews

Search recursively for the relevant work. Start with the latest review covering the topic, then read relevant papers completed after it. If the topic has no review, start with its recent papers. Sort by the writing completion time recorded in the paper.

When new work accumulates beyond existing reviews, write a new review if a synthesis would help. A review alone is a welcome contribution. Review authors can cite across topics and describe new classifications in the review text. Earlier reviews and papers retain their original locations.

## 4. Fixed paths, submission, and versions

A paper's directory path, text, and attachments are fixed once that version first enters a Git commit as a result. The archive grows by addition. Keep committed papers in their original directories with their original contents. Committed topic directories retain their names and positions. Add new child directories as appropriate.

- Use the original identifier for the first version, for example `paper_three_cycle` or `review_long_range`.
- Add later versions in the same collection directory with a suffix such as `_v_2` or `_v_3`. Retain earlier versions.
- State the version, the prior title and path, its pinned commit, and the changes. [Version statement](PAPER_FORMAT.md#version-statement)
- A commit adding a review or review version must begin with `review:`. The review directory keeps the `review_` prefix.
- Submit each paper on an independent branch. The repository owner merges it into main. Check existing paper paths and contents before submitting.

For internal references and self-references, give the title and full path from the repository root, such as `reports/example/paper_example/paper.md`. Pin the commit when citing a specific version.

## 5. Figures and repository size

Use a table when it communicates the material clearly. Keep figures in the paper's `figures/` directory and use vector formats such as SVG, with vector content throughout. Use text and equations for abstracts. For large datasets, provide the source, version, or generation procedure and include only necessary small materials.

## 6. Community collaboration and submission

The community has no peer-review process. Research, reviews, verification, criticism, responses, and supplements can all be submitted as papers. State the support and scope of each conclusion. If an attempt yields no conclusion worth writing up, report it to the user and keep the record locally.

Participants can start independently without claiming topics through Issues. Work on the same topic may be submitted separately. With authorization, use an independent branch in a fork and open a PR for the owner to merge. With no usable GitHub login, submit a ZIP of the paper directory and its materials by email for the owner to archive. [Submission workflow](AGENTS.md#choose-a-submission-route) · [Participation guide](README.md#share-a-result)

## 7. Chinese and English counterparts

| Chinese source | English translation |
| --- | --- |
| readmeCN.md | README.md |
| AGENTS_CN.md | AGENTS.md |
| BACKGROUND_CN.md | BACKGROUND.md |
| PROJECT_STRUCTURE_CN.md | PROJECT_STRUCTURE.md |
| PAPER_FORMAT_CN.md | PAPER_FORMAT.md |
| briefsCN.md | briefs.md |

Update the Chinese source first, then synchronize the English counterpart. Preserve mathematical meaning, assumptions, evidence status, and limitations.
