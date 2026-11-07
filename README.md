# BeggingForOracle

An open research workshop for people and AI agents working on fast molecular graph sums, with a focus on permutationally invariant polynomial potential energy surfaces (PIP PESs) in computational chemistry.

[中文介绍](readmeCN.md)

Yiping Hao · [hyper@dicp.ac.cn](mailto:hyper@dicp.ac.cn)

Hello to everyone, human or AI, who has found this repository. I'm Yiping Hao, the founder of BeggingForOracle. Thank you for stopping by.

I started this project to ask for help. If you are willing to spend some time or model usage, I would appreciate your help with an algorithmic problem in computational chemistry.

I am a PhD student at the Dalian Institute of Chemical Physics, Chinese Academy of Sciences. I develop computational methods for PIP potential energy surfaces. In a recent preprint, we introduced tensor-network descent, which expresses PIP evaluation as sums over colored multigraphs and speeds it up by sharing tensor contractions. [Preprint](https://arxiv.org/abs/2610.23034v1)

I was pleased with the result and wanted to see how much further it could go. Can we evaluate the same quantities faster? In particular, can the geometry of interatomic distances help us improve on the complexity in the paper?

I explored several ideas with GPT-6 Astra. It suggested other routes, helped complete some derivations, and found counterexamples. Some ideas give better complexity under particular assumptions. Choosing useful radial functions, achieving the necessary accuracy, and keeping computational constants small have made the practical problem harder. I still do not have a general answer that satisfies me.

I started BeggingForOracle as a small open research community where people and their AI agents can explore different approaches, check one another's arguments, and leave conjectures, findings, counterexamples, and failed attempts for later contributors.

Our goal is to **accelerate the molecular graph homomorphism sums $H_F$, improve on existing complexity bounds where possible, and make the results useful for computational chemistry**. You can start contributing while you learn the mathematical details. [Research background](BACKGROUND.md)

## How you can help

If you have time or model usage to spare, you can use an agent that can read local files and run code, such as Codex, Claude Code, Cursor, or WorkBuddy. Checking a formula, reproducing an experiment, or taking one approach a step further is already useful. Human derivations, code, comments, and counterexamples are welcome too.

### Start with one prompt

Download and unzip the project, then open the directory in your agent. A public ZIP download works without a GitHub account or a Git installation. If you use Git, you can clone the repository or fork it first. [Download ZIP](https://github.com/YipingHao/BeggingForOracle/archive/refs/heads/main.zip) · [Repository](https://github.com/YipingHao/BeggingForOracle)

Choose a prompt for the language you want to use with the agent.

**English**

```text
Please work with me in English and follow AGENTS.md to conduct research and submit your results.
```

**中文**

```text
请用中文与我交流，按 AGENTS.md 开展研究并汇交成果。
```

The agent takes its working language from the first prompt. Before starting research, it asks about optional attribution and your preferred direction in one round. You can suggest a topic or let the agent choose. Research papers and reviews are written in English.

### Continue research

Research may span several conversations. If the agent anticipates a context, usage, or tool limit, it should save its progress and prompt you to enter **“Please continue”** in English or **“请继续”** in Chinese. Once usage is available again, or after switching to an available model, send that prompt to resume. Saving progress during work also helps when a limit interrupts a reply.

### Codex

Open the local repository in Codex, start a conversation, and send the prompt. The agent guide is in the repository. You can ask Codex to report the repository path at startup to confirm which copy it opened. [Agent guide](AGENTS.md) · [OpenAI documentation](https://learn.chatgpt.com/docs/agent-configuration/agents-md)

### Claude Code

Enter the local repository directory, run `claude`, and send the prompt. It directs Claude Code to the project's shared instructions in `AGENTS.md`. [Claude Code quickstart](https://code.claude.com/docs/en/quickstart) · [Project instructions](https://code.claude.com/docs/en/memory)

### Cursor

Open the local repository in Cursor and send the prompt in Agent mode. The agent can use the project instructions in the root `AGENTS.md`. [Cursor Agent](https://cursor.com/docs/agent/overview) · [Project rules](https://cursor.com/docs/rules)

### WorkBuddy

Select the local repository as the task directory and send the prompt. The prompt explicitly directs the agent to read `AGENTS.md`. Confirm that the agent can read the project files and run code if the work calls for an experiment. [WorkBuddy task guide](https://cloud.tencent.com/document/product/1831/137516)

### Share a result

An attempt can end without a paper. If the agent finds no conclusion worth writing up, it should tell you what it tried, where it got stuck, and where it saved its progress. A failed approach that teaches us something can become a negative-results paper.

For a result worth sharing, the agent can help with either route within your authorization.

- **GitHub.** With a usable login, the agent prepares an independent branch in your fork, pushes the paper, and opens a pull request. It gives you the PR link. The repository owner merges into the main branch.
- **Email.** The agent prepares a ZIP of the paper directory and an email draft with the recipient, subject, body, and attachment name. Attach the ZIP and send the draft to **hyper@dicp.ac.cn**. This route also works if account or network problems prevent a GitHub submission.

If you choose to sign in, the agent can guide you through the browser flow. You may need to complete verification yourself. Check the agent's report to see what it actually delivered. Papers can include separate supplementary material, figures, code, and reproduction instructions inside their own directories. [GitHub pull requests](https://docs.github.com/en/pull-requests/reference/pull-requests)

The community has no peer-review process. Discussion, verification, criticism, and responses can themselves become papers. [Project structure](PROJECT_STRUCTURE.md) · [Paper formats](PAPER_FORMAT.md)

### Attribution and contributions

The agent asks what you would like to make public. You can provide your name or handle, affiliation, email, or GitHub username, or omit them. Research and writing are attributed to AI by default. If you gave additional guidance, the contribution note can record the actual prompt or idea. If you gave no additional guidance, one sentence is enough, or the note can be omitted.

GitHub commits and pull requests remain associated with the account used. Choose email if you want to keep that account private.

If work you contributed to with AI meets academic publication standards and we decide to use it in a publication, I will contact you to confirm contributions, authorship, and the manuscript. Other contributions can be recorded in the project or acknowledged where appropriate.

Thank you for offering your time, judgment, and model usage. I hope we find answers worth keeping.
