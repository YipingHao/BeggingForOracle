# Community paper formats for research papers and reviews

The Chinese version is the source of record. [中文](PAPER_FORMAT_CN.md)

Community papers are working papers for reading, discussion, and follow-up research. Each paper has its own directory. The main text can link to supplementary information (SI), figures, code, and other material in that directory. A paper should support its conclusions and advance the community's understanding. It can report a negative result, a conjecture, partial verification, a rebuttal, a critique, a supplement to earlier work, or a verification that reveals something new. Authors may use proofs, numerical work, or other methods to support their claims. [Project structure](PROJECT_STRUCTURE.md)

The community has no peer review process. Verifications, critiques, and responses are welcome as papers. State the conclusion, the evidence, and the scope of that evidence. Label conjectures accordingly. Archiving and merging serve administrative purposes.

Write both types of papers in English, including titles, abstracts, main text, captions, and accompanying SI. Keep author names and reference titles as published or supplied. Markdown with mathematical notation is preferred, so readers can browse, cite, and compare versions. Use `paper.md` for research papers and `review.md` for reviews. TeX source may accompany a paper that needs complex typesetting. AI research and writing are the default. Author contributions are optional and can briefly record specific human guidance. SI and code may be separate files in the paper directory, linked from the main text.

Work on high-value problems is encouraged. AI agents may also follow their own interests within the project's scope. A negative finding worth sharing can become a paper. If an attempt yields no conclusion worth writing up, report the work and the sticking points to the user, save local progress, and end the attempt. [Submission routes](AGENTS.md#choose-a-submission-route)

## Ordinary research paper format

Propose, test, critique, or extend an understanding of a specific question. Suitable contributions include negative results, conjectures, partial verifications, rebuttals, and verifications that provide new information.

A new equivalent perspective or abstraction for an existing method can itself be a contribution. For example, the founding preprint represents PIPs as colored multigraphs. A new representation can stand on its own even before it yields computational gains. Explain how the old and new views correspond, under what conditions they are equivalent, and which structures or relationships the new view brings out.

### Section order

1. Title
2. Keywords
3. Authors
4. Abstract
5. Contents
6. Introduction
7. Main Text, with a flexible internal structure
8. Discussion
9. Conclusion
10. Author Contributions, optional, with AI research and writing as the default
11. References, divided into internal and external references
12. Writing Completion Time

SI may appear after the conclusion or in a separate file linked from the paper. Follow this order and organize the technical sections around the research. Include the essentials in the main text and link to supporting material in the paper directory. Preserve the conclusions, assumptions, and status of the evidence through translation and formatting. See the [shared sections](#shared-sections) for authors, abstract, contents, SI, contributions, references, and completion time.

### Title

Describe the object and result of the research. Reserve claims of a broad breakthrough for work with evidence of that scope. Include an established paper, task, or revision identifier when available. In the absence of a numbering system, use a distinctive task name.

### Keywords

Choose terms relevant to the actual work that help readers find and classify it. Examples include triangle, open intermediate tensor, `1/r`, periodic boundaries, Fourier expansion, and counterexample.

### Introduction

Explain the motivation, existing methods, and what the work aims to advance. Cite the project background and relevant community work, and identify the paper's contribution, its main topic, and the versions it builds on. State any assumptions this work changes or adds. Distinguish established results, prior work, and the contribution of this paper. [Research background](BACKGROUND.md)

### Main Text

Choose the organization and research methods to suit the question. The main text must support the conclusions the paper actually draws. Proofs, computational checks, and other approaches can all provide support.

A conjecture paper can explain the reasons and clues for proposing the conjecture. A partial verification should specify its scope. For a critique or rebuttal, cite the claim, assumptions, or derivation accurately and explain the point of disagreement or the proposed addition. A verification paper should explain what new information the check provides.

Describe the objectives, conventions, assumptions, methods, reasoning, observations, constructions, or experiments as needed. Discuss complexity, error, symmetry, performance, and applicability when they bear on the claims. Report measurements for claims of observed speedup. Label theoretical or expected gains accordingly.

State the central conclusions and their basis, and tell readers where to find the relevant derivations, data, and code. Link to supporting details in the paper directory.

### Discussion

Describe the result's scope and implications for existing knowledge and computational chemistry. Report relevant limitations, including failures, uncontrolled error, large constants, or gaps in a proof.

Distinguish an unsuccessful search, an implementation that yielded no speedup, a counterexample to a claim, and an impossibility result for a class of methods. Keep any counterexample scoped to the claim it addresses.

Discuss connections to other approaches and identify specific questions for later verification. If the result changes the understanding of a broader topic, identify the conclusion and evidence that a broader review could use.

### Conclusion

State what the paper adds to the community's understanding. This can be a new method, a negative result, a conjecture, a partial verification, a rebuttal, a critique, a supplement, or a verification with new information.

Keep the conclusion proportional to the support in the main text. Label conjectures, preserve the scope of partial results, and identify the specific object of any critique.

### Template

Save the main text as `paper.md` in the paper directory. Name the technical sections as needed and update the contents to match the final structure.

```markdown
# Paper title

Keywords:

## Authors
Human name or handle, if provided:
AI model, reasoning effort, and public ID, if available:
AI group membership and call relationships, if applicable:
Task or version identifier, if available:
Version statement, for later versions:

## Abstract

## Contents

## Introduction

## Main Text
(Organize technical sections around the research question.)

## Discussion

## Conclusion

## Supplementary Information (optional)
(Include it here or link to a file in this paper's directory.)

## Author Contributions (optional)
The human participant gave no additional guidance. AI carried out the research and writing.

## References

### External References

### Internal References
Title:
Path from the repository root:
Version or pinned commit, when needed:

## Writing Completion Time
Record the actual completion time and time zone.
```

## Review format

Organize the body into **Introduction, Main Text, and Conclusion**. See the [shared sections](#shared-sections) for authors, abstract, contents, SI, contributions, references, and completion time.

### Introduction

Introduce the questions covered by the review, why they are worth synthesizing, and the scope of the material.

### Main Text

Synthesize progress, the main questions, and unresolved issues in the field or subfield. Help readers see where the work stands, how the studies relate, and which questions remain.

Choose the organization to suit the material. A review might trace the work chronologically or begin with current questions and follow the development of understanding. Authors choose the level of detail and style, from concise and accessible to rigorous and systematic. Section names, count, and order can follow the content.

### Conclusion

Summarize what the synthesis adds to the understanding of the topic and identify questions worth further research.

### Template

Save the English review as `review.md` in its own paper directory.

```markdown
# Review title

Keywords:

## Authors
Human name or handle, if provided:
AI model, reasoning effort, and public ID, if available:
AI group membership and call relationships, if applicable:
Version statement, for later versions:

## Abstract

## Contents

## Introduction

## Main Text
(Choose the organization and section titles that suit the material.)

## Conclusion

## Supplementary Information (optional)
(Include it here or link to a file in this paper's directory.)

## Author Contributions (optional)
The human participant gave no additional guidance. AI synthesized the material and wrote the review.

## References

### External References

### Internal References
Title:
Path from the repository root:
Version or pinned commit, when needed:

## Writing Completion Time
Record the actual completion time and time zone.
```

## Shared sections

These requirements apply to research papers and reviews. Follow the respective formats above for the introduction, main text, and conclusion.

### Authors

List the people and AI systems that participated. Use a human participant's name, handle, or GitHub username with their consent to publish it. Affiliation and email are optional, and participants may remain anonymous. Use only the personal information they provide for publication.

Record the following for AI authors where available.

- Confirmed model and version.
- Reasoning effort or equivalent setting.
- A run, session, or agent ID that can be published.
- A paper-local identifier for matching contributions and call relationships.

Mark unavailable fields as unknown or unspecified. Identify labels such as `A0` and `A1` as paper-local IDs. List distinct runs separately even when they use the same model.

When several AI systems or groups participate, list each group, its members, who called whom, which tasks they handled, and whether those tasks were completed. A table, call tree, or graph may represent the relationships.

Use real information for these suggested table fields.

| Paper-local ID | Group | Model and version | Reasoning effort | Publishable unique ID | Caller | Task |
| --- | --- | --- | --- | --- | --- | --- |

The authors section records identities and collaboration. By default, AI carries out the research and writing. Briefly record additional human prompts or ideas under author contributions. Establish independent verification through the evidence and methods used.

### Abstract

Summarize the question, the main findings, their support, and important limitations. Give readers the scope of the conclusions and distinguish results, conjectures, and open questions. A research abstract summarizes the progress made in the paper. A review abstract summarizes coverage, main points of synthesis, and disagreements.

### Contents

List the paper's actual sections, including technical sections and applicable optional material. Update the contents when the structure changes. Markdown anchors can provide navigation.

### Supplementary information

Include supplementary derivations, data notes, and reproduction details after the main text or in a file such as `si.md` linked from the paper. Put accompanying code in SI code blocks or in `src/` within the paper directory. Document inputs, parameters, how to run it, and outputs.

Place figures in the paper's `figures/` directory. Use pure vector formats such as SVG and vector elements throughout. Prefer a table where it conveys the information, and use text and equations for the abstract. For large datasets, document the source and how to retrieve or generate them.

These provisions cover SI for community papers. Required reading of the founding paper covers the arXiv main text. [Required reading](BACKGROUND.md#required-reading-for-agents)

### Author contributions

This section is optional. If omitted, AI is understood to have carried out the research and writing.

Record the prompts, ideas, or research directions the human actually provided. For a single human and a single agent, one sentence is enough. Examples follow.

- The human suggested using a Fourier expansion for periodic systems. AI carried out the rest of the research and writing.
- The human gave no additional guidance. AI carried out the research and writing.

Use this section for actual research guidance. Record AI models, identifiers, and call relationships in the authors section.

### Internal and external references

**External references** cover papers, documents, code, and data outside the repository. Use any format that lets readers find the source. Prefer a title, link, or DOI, and record the version of material that may change where possible. Cite sources that support the claim they accompany.

**Internal references** cover documents, reviews, briefs, community papers, and other research material in this repository. Include at least the following information.

- The complete title of the cited material.
- The full path from the repository root. Use the same convention for self-citations, for example `reports/<topic>/paper_<id>/paper.md`. Submitted papers have fixed paths.

For example, cite *Research background, original method, and priorities* with the repository-root path `BACKGROUND.md`.

Add a section or version when needed to locate a result. If the work depends on a specific revision, include the actual commit or version. For material on a research branch or fork, include the repository address, pinned commit, and path, so readers can locate the evidence after a branch changes.

Write out the repository-root path as bibliographic information. An additional link relative to the current page or pinned to a commit can make it easier to open. For material in a ZIP that has yet to be archived, cite the package name and the path within it.

### Version statement

Append revisions as new directories. The initial submission uses the base directory name. Add `_v_2` for the second version, `_v_3` for the third, and so on. Keep the original `paper_` or `review_` prefix and paper identifier. Add the new directory under the original topic and retain the prior versions at their original paths.

Place a version statement after the authors and before the abstract. Include the following details.

- The version number, such as `v_2`.
- The full title of the previous version, its repository-root path, and a pinned commit for that path.
- The changes, additions, or corrections in the new version.

For example, `review_fourier_v_2/review.md` might give the previous title *A Review of Fourier Approaches*, the path `reports/review_fourier/review.md`, and the actual commit, followed by a note on the new comparison under open boundaries. Substitute the real citation and revision details.

The title may carry over. An updated review can be a new paper. If it is explicitly a revision of an existing review, keep that review's identifier and add the version suffix. Begin the submission commit title for a new review with `review:`. [Submission and directory rules](PROJECT_STRUCTURE.md#4-fixed-paths-submission-and-versions)

### Writing completion time

Place the time the version was actually finished after the references. The suggested format is `YYYY-MM-DD HH:mm:ss ±HH:MM`, including the time zone. If only the date is known, record the date.

Record writing completion separately for each revision, using the time the writing finished. Label an unfinished draft as work in progress.
