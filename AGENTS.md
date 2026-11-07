# Agent workflow

This is the English translation of the Chinese source. The four steps below apply to new research and review tasks. For repository maintenance, follow the user's task scope. To resume research, load the progress record and continue from the first unfinished step. [Chinese source](AGENTS_CN.md)

## Start a research task

### 1. Understand the project

Verify the project root and inspect existing files. With Git metadata, check the branch and working tree and preserve existing changes. With a ZIP snapshot, record its origin and work in an independent research directory.

Read the README and background to understand the project's questions, the original method, and where the requested task fits. Then ask the user about participation. [README](README.md) · [Research background](BACKGROUND.md)

### 2. Ask the user

Use the working language requested in the first prompt. Otherwise use the principal language of that prompt. Ask about attribution and research direction together, using any choices the user has already provided.

> What attribution would you like to include? You may give a name or handle, affiliation, email, or GitHub username, or leave this blank.
>
> Is there an idea you would like to try or a topic you want to study? If you have no preference, I will choose a direction based on the project and its progress.

Use the working language for conversation, progress reports, and work notes. Write research papers, reviews, and accompanying supplementary information in English. [Paper formats](PAPER_FORMAT.md)

Attribution is optional. Use only information the user provides or agrees to publish. If the user leaves it blank, continue preparations and omit extra personal details. Record the chosen attribution in the paper and submission description. Use anonymous attribution if requested. A GitHub commit or PR remains associated with the account used. Offer ZIP and email delivery when the user wants to keep that account private.

#### Choose the research direction

- Follow a topic or idea supplied by the user and turn it into a concrete question within the project.
- If the user delegates the choice, consider existing work, the project priorities, and your own research interests within scope. Explain the chosen question and what you will investigate, then do the work.
- Use any topic already supplied in the initial prompt. Ask only about ambiguities that materially affect the work. If the direction runs into an obstacle, record it and look for a tractable question on the same route.
- While waiting for a reply, read the standards and material independent of the topic. Give the user reasonable time to respond. If no preference arrives, state the direction you are taking and incorporate later guidance.
- Save the selected direction and the user's substantive ideas in the progress record. Reuse them when the user asks to continue.

### 3. Read the standards and research material

- Read the rules for finding papers, choosing a topic directory, preserving paths, adding versions, and submitting branches. [Project structure](PROJECT_STRUCTURE.md)
- Read the format for the selected type of paper or review. [Paper formats](PAPER_FORMAT.md)
- Read the complete original paper as specified in the background, and record the version and sections actually read. On resumption, use your record to revisit the relevant parts. [Required reading](BACKGROUND.md#required-reading-for-agents)
- Check related reviews and papers, the intended quantity, output, baseline, and assumptions. A scalar, a complete open tensor, and a representation supporting only specific operations are distinct outputs.

Use the background for the project scope, priorities, and required reading. Use the structure document for paths and versions, and the format document for writing, references, and supplements. This guide governs execution and submission.

### 4. Research and write

Investigate the question through derivation, verification, criticism, synthesis, or other appropriate work. Record what you did, what you found, and the limits of the evidence. Distinguish completed work, conjectures, and plans.

An attempt may end without a paper. If actual exploration yields no conclusion worth writing up, tell the user what you tried, where it stopped, and where you saved the progress. Close the attempt with that report. Submit a paper when the work yields an insight worth sharing, including an obstacle, counterexample, or useful negative result.

Use the relevant paper format. Before submission, check the destination, directory prefix, version, branch, references, and the materials actually included. [Project structure](PROJECT_STRUCTURE.md) · [Paper formats](PAPER_FORMAT.md)

Users control model choice, reasoning effort, and usage in their software. Follow any limits the user states.

## Resume work across conversations

- Keep an updated task record such as `progress.md` with the objective, completed derivations and experiments, evidence locations, unresolved questions, branch or working directory, running tasks, and next step. Keep credentials out of the record.
- Save key progress during long tasks and before condensing the conversation context.
- If a tool, usage, or context limit may end the turn before the work is complete, save the results and tell the user where to resume. Prompt for **“Please continue”** in English or **“请继续”** in Chinese.
- Describe the limits you can actually observe. If the user needs to wait for usage to recover or select another model, explain how to resume afterward.
- On either continuation prompt, load the previous objective, language, attribution preferences, authorization, and next step. Continue the existing work.
- Keep working across routine intermediate steps. End the turn when the task is complete, a fresh turn is needed, a blocker requires user action, or the user asks to stop.

## Choose a submission route

Use this workflow when there is a result worth submitting and the user has authorized delivery.

### 1. Check available authentication

- Identify the environment and repository path. Check for GitHub CLI with `Get-Command gh` in PowerShell or `command -v gh` in WSL/Linux.
- If available, use `gh auth status --active --hostname github.com` to check usable authentication. Use `gh api user --jq .login` when the account needs confirmation.
- A GitHub connector can also check identity and permissions. Check Git push access and fork or PR API permissions separately.
- Windows and WSL can have separate CLI configurations. When permitted, check the other environment with `gh.exe` from WSL or `wsl.exe -d <known-distribution> -- gh auth status --active --hostname github.com` from PowerShell. Verify path mapping and use the environment that has usable credentials.
- Treat `git config user.name` and `user.email` as commit attribution settings. Verify GitHub identity through an authenticated tool.
- Query only the identity and status needed. Keep tokens, SSH private keys, browser login data, and other credentials out of outputs and submission files. Use the masked status output rather than `--show-token`.

See the CLI manuals and Windows/WSL guidance for these commands. [Status](https://cli.github.com/manual/gh_auth_status) · [Login](https://cli.github.com/manual/gh_auth_login) · [Environment](https://cli.github.com/manual/gh_help_environment) · [WSL interoperability](https://learn.microsoft.com/en-us/windows/wsl/filesystems)

### 2. Offer login or email when authentication is unavailable

Offer a choice once between GitHub login and a ZIP with an email draft. Continue research independently of that choice. If the user chooses login, guide them through `gh auth login --hostname github.com --web`. The user completes credentials, verification, and confirmations. Use the email route if the user declines, does not respond, or the required tool or permissions are unavailable.

Use the active valid account in the working environment when several accounts are available and the user has given no preference. State which account you plan to use. If ownership is unclear or conflicts with the user's authorization, clarify it while continuing local work.

### 3. Submit through a fork and pull request

- Use the user's existing authorization for the fork, push, and PR. Check authorization for actions outside that scope.
- Follow the branch rules in the structure document and preserve existing worktree changes. From a ZIP snapshot, finish in an independent directory. Transfer the listed results to a separate checkout for GitHub submission. [Branch and version rules](PROJECT_STRUCTURE.md#4-fixed-paths-submission-and-versions)
- Use or create the authenticated account's fork of `YipingHao/BeggingForOracle`. Preserve existing remotes by using a separate remote or checkout as needed.
- Commit the paper, code, and reproduction material for the current task. Push the independent submission branch. Leave unrelated changes and other branches intact.
- Check material, reproduction notes, sources, and commit attribution. Use an existing valid commit identity or verified account information scoped to this operation.
- Open or update the PR for the paper. Describe its conclusion, scope, verification, and unresolved questions. The repository owner handles the merge into main. [Community collaboration](PROJECT_STRUCTURE.md#6-community-collaboration-and-submission)
- Return the actual PR link. If upload fails, report what succeeded and prepare the email package.
- Include only agreed public attribution. Keep local configuration email addresses out of the paper unless the user supplied them for publication.

### 4. Prepare a ZIP and email draft

Create `BeggingForOracle-<task>-<date-or-unique-id>.zip` and `email.txt` in a separate output directory. Preserve the paper directory layout, relative paths, and attachments. Include a file list and source information.

Record the starting commit and relevant changes for a Git checkout. For a snapshot, record the source URL and any confirmed version or download date. Record the actual tools and model information available. Mark missing details as unknown.

Pack files from the explicit list. Exclude Git internals, credentials, environment files, caches, unrelated personal files, and the output ZIP itself. When essential data exceed the attachment budget, provide a small reproducible package and describe how to retrieve or generate the omitted material. Open the ZIP and check that its contents match the list and instructions.

In `email.txt`, include the recipient `hyper@dicp.ac.cn`, a subject in the form `[BeggingForOracle] <task>: <one-line result>`, a short account of the question, results, evidence, limitations, and follow-up questions, the actual ZIP filename, and the attribution the participant has approved.

Give the user the package and draft paths. Ask them to attach the ZIP, copy the subject and body, and send the email. An attempt that ends without a paper stays in the local progress record and is reported to the user.

## Collaboration and handoff

Stay within the assigned task. Bring proposed changes to shared definitions or priorities into the open. Follow the structure document for participation and archiving. Use the current authorization when launching other agents, sending messages, committing, or pushing. Report where the work lives, what was verified, the outcome, and unresolved questions. Confirm the correct repository path before editing. [Project structure](PROJECT_STRUCTURE.md)
