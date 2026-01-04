---
layout: post
date: 2026-01-05 00:00
title:  "Preparing JOSS for a generative AI future: From code to human creativity and design"
authors: 
- arfon
category:
- announcements
---

> JOSS was created with the goal of providing scholarly credit to the developers of software that was or would be useful in research. That software must be useful for research has been a criterion from the start.

Five years ago, we introduced a second criterion, [*"substantial scholarly effort"*](https://blog.joss.theoj.org/2020/07/minimum-publishable-unit), to ensure that we publish meaningful contributions to research software. Our benchmark at the time – at least roughly three months of developer time – offered a practical, human-centered proxy for effort. For that era, it served us well.

Today, the landscape is fundamentally different. Where generating code once took three months, in some cases this can now be accomplished in three days – or even three hours – with generative AI tools. With AI agents increasingly capable of producing entire codebases from natural language prompts, the marginal cost of code generation is rapidly approaching zero. This transformation in what is possible to create in a short period of time, sometimes without even [directly interacting with code](https://en.wikipedia.org/wiki/Vibe_coding), enables people of all backgrounds to create new software tools. It also poses a fundamental challenge: how do we evaluate what constitutes credit-worthy, publishable research software contributions?

### Recognizing value in the age of generative AI

Generative AI tools have progressed rapidly over the past three years, and we expect their capabilities will continue to grow. As AI becomes capable of handling increasing fractions of the actual implementation work, the irreplaceable human contributions to software become clearer: understanding context, collaboration with others, making design tradeoffs, creating abstractions that capture domain expertise, and building conceptual foundations and following sustainable software practices that enable future discovery.

Going forward, these are the contributions JOSS will prioritize and reward. Since there are now many ways that software can be cited (e.g., via archival deposits in Zenodo, via Software Heritage), a JOSS publication will recognize more than just software that is used in research.

Put simply, we're shifting from evaluating software through proxies for effort – like lines of code – toward clear evidence of research impact, intellectual contribution, scholarly significance, and open-source software practices. Regardless of whether you leveraged AI assistance, show the human work: the problem framing, key design decisions and abstractions, and the practices that make the software usable and sustainable for others (tests, documentation, licensing, versioned releases, and a transparent issue and review process).

A JOSS submission should demonstrate real or credible reuse and sustained value to the research community. Short-lived, single-use codebases remain out of scope for JOSS.

### What we'll look for

**Research impact and significance:** Provide concise evidence of realized impact or credible near-term significance. This may include publications/analyses using the software, new experiments or workflows it enables, external adopters/integrations; or, prospectively, comparative benchmarks and a reproducible reference analysis/tutorial. Where related tools exist, state the unique scholarly contribution – problem framing, key design choices/abstractions – and why alternatives are insufficient for your research context. Signals like multi-institution teams and external contributions can strengthen the case but aren't required.

**Design thinking:** A JOSS publication should reveal design thinking. Show us the trade-offs you weighed, the architecture you settled on, and why it matters. The most valuable contributions often lie not in the code itself but in the conceptual framework it embodies. We particularly value work that thoughtfully builds upon or extends existing software ecosystems rather than reinventing solutions where quality alternatives already exist. We recommend this information live in your user-facing documentation to help would-be users understand what your software does, and how it does it.

**Open-source software practice:** In an era of rapid code generation, the work of creating maintainable, well-documented, test-driven systems becomes even more valuable. We'll look for evidence of good practices: comprehensive testing, clear documentation, statements describing support and governance, and clear pathways for community contribution. Software should be developed and maintained in an open manner, ideally with open governance, not developed in a private place and then deposited online (e.g., GitHub, GitLab) with an OSI-approved license in order to meet minimal open-source requirements.

**Development history:** Meaningful research software typically emerges from sustained collaborative effort over time. We will examine the project's development timeline and commit history as indicators of genuine community engagement and iterative refinement. Projects with development histories spanning multiple months or years, showing contributions from multiple developers, and demonstrating evolution through community feedback are more likely to represent substantial scholarly contributions. While we don't impose strict temporal requirements, very recent projects (particularly those with commit histories of only weeks) may warrant additional scrutiny to ensure they represent genuine collaborative scholarship rather than rapid AI-assisted code generation. Projects developed in private are not eligible until there is a public record of open development: at least six months of public history prior to submission, with evidence of releases, public issues/pull requests. A history of contributions and engagement from individuals beyond the original team, across organisations, is especially welcome, though not essential. We particularly value projects that show evidence of open development practices from early stages, rather than private development followed by public release.

### Implementing this scope change

We recognize that any policy change affects authors at different stages of the submission process, and we want to be transparent about how we'll handle this transition.

Existing submissions that have already begun their review will continue to be evaluated against the editorial scope in place when their review started. We believe this is the fairest approach for authors and reviewers who have already invested time and effort under the previous expectations.

Submissions currently awaiting review – including those in a pre-review state – will have the updated scope applied to them. Authors of these submissions will be asked to update their papers to match the new required format, with guidance from our editorial team.

We acknowledge that this approach will result in some papers that were previously in scope for JOSS now being deemed out of scope. For authors who submitted some time ago and have been waiting in our backlog, we understand this is frustrating, and we apologize for that. However, we believe this is the most straightforward path forward, particularly for our volunteer reviewers and editors who need clear, consistent criteria to do their work effectively.

The JOSS editorial team remains firmly committed to the belief that high-quality open-source software is essential to the research enterprise, and we want JOSS to continue providing a valuable service to the people creating it. AI is fundamentally changing how software is built and how we assess scholarly contributions. We hope these updated policies will serve the community well as that transformation continues.


