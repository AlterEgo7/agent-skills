---
name: technical-writing
description: Technical writing for software and computer engineering. Use whenever creating, editing, or reviewing documentation, READMEs, design or architecture documents, API guides, tutorials, runbooks, code comments or docstrings, PR descriptions, issue tracker tickets, release notes, engineering explanations, or an agent's own discussion points and final output during software work. Apply it even when writing is only one part of a coding task. Keep comments and docstrings as short as practical.
---

# Technical writing

Make correct technical content easy for its intended reader to understand, trust, and act on. Use the smallest amount of writing that achieves that result.

Follow the repository's terminology, templates, and style guide when they differ from this skill. Preserve exact code identifiers, quoted text, and required legal or organizational wording.

## Write from the reader's position

Before drafting, identify these constraints. Infer them silently when they are obvious.

1. **Audience:** Who will read this? If audiences differ, which one is primary? What do they already know? What unfamiliar terms, assumptions, or context block them?
2. **Purpose:** What should the reader understand, decide, or do after reading?
3. **Occasion:** What form, length, formality, template, and political or organizational constraints apply?

Organize around the reader's task, not the order in which the author performed the work. Begin with familiar context, then introduce new details. Give readers the reason to continue before asking them to absorb complexity.

## Draft in this order

1. **Usually lead with the result or purpose.** State the outcome, decision, problem, or requested action before background detail. For a resistant audience, first acknowledge its material concern and establish shared facts before presenting a contested conclusion.
2. **Set the necessary scope.** Include prerequisites, constraints, exclusions, and definitions only when readers need them or might reasonably expect something else.
3. **Build an assertion-evidence path.** Support consequential claims with measurements, examples, references, test results, or explicit reasoning.
4. **Arrange details by relevance.** Put the most important information in titles, openings, headings, and conclusions. Use progressive disclosure for secondary detail.
5. **Revise structure before sentences.** Fix scope, order, omissions, and repetition before polishing grammar.
6. **Finish for correctness.** Check facts, code, identifiers, commands, links, units, dates, and claimed verification.

## Write clear, efficient prose

- Prefer precise, concrete nouns and strong verbs: “The parser rejects malformed input,” not “An error occurs due to malformed input.”
- Prefer active voice when the actor matters. Use passive voice when the actor is unknown, irrelevant, or less important than the result.
- Use one term for one concept. Repeat the exact term instead of inventing synonyms.
- Define an unfamiliar term at first useful use. Introduce an abbreviation only when it recurs enough to reduce effort.
- Keep pronoun references unmistakable. Replace a vague `this`, `that`, `it`, or `they` with the noun when a reader could hesitate.
- Keep one main idea per sentence. Split nested clauses, alternatives, and sequences that make readers reread.
- Put conditions and goals before the actions they qualify: “If caching is enabled, restart the worker.”
- Use present tense for general behavior, past tense for completed work, and future tense only for an actual future event.
- Distinguish obligation from advice. Use an imperative or **must** for requirements, **recommend** for recommendations, **can** for options or ability, and **might** for possibility. Avoid an ambiguous **should**.
- Replace judgment with evidence: “reduces median latency by 18% in the benchmark,” not “is dramatically faster.”
- Mark uncertainty. Separate observed facts, assumptions, hypotheses, and conclusions.
- Prefer plain, globally understandable words. Avoid idioms, slang, clichés, sports metaphors, unnecessary humor, and rare words where a common word is precise.
- Use inclusive language. Preserve legacy terms only when they are exact identifiers, quotations, or required search terms; explain them without normalizing them.
- Avoid claims such as **always**, **never**, **best**, **secure**, or **optimal** unless the evidence and scope justify them.
- In user-facing documentation, address the reader as **you** or use the imperative. Reserve **we** for a clearly identified authoring organization.

Cut filler and ceremony. Common signals include “please note,” “it is important to note,” “in order to,” “the fact that,” “there is,” “is able to,” “utilize,” “very,” “clearly,” “obviously,” “simply,” and “easy.” Do not delete a caveat, prerequisite, rationale, or safety constraint merely to shorten the text.

## Make structure visible

- Use a descriptive title that identifies the task, subject, or outcome and narrows the scope.
- Use sentence case for titles and headings unless local style differs.
- Make headings describe reader tasks or concepts. Keep sibling headings parallel and do not skip heading levels.
- Follow a heading with orientation when readers need it; do not stack headings without context.
- Lead each paragraph with its point. Keep each paragraph on one topic.
- Use numbered lists only when order, sequence, or priority matters. Use bullets for unordered items.
- Introduce lists when their meaning is not already clear. Keep list items grammatically and logically parallel.
- Use tables for compact two-dimensional data or comparisons, not page layout or long prose.
- Use descriptive link text that names the destination or purpose. Do not use “click here” or an unexplained raw URL.
- Format commands, paths, identifiers, flags, values, and other code entities as code when the medium supports it.
- Format UI labels according to local style, often bold, rather than as code.

For accessibility, do not rely on position, color, size, or punctuation alone to convey meaning. Give every image an alt attribute: use concise, context-aware alt text for informative images and empty alt text for decorative images. Put complex or new information in equivalent surrounding text. Use descriptive headings, meaningful links, captions or transcripts for media, sufficient contrast, and labels or figure numbers instead of spatial references such as “above,” “below,” or “right.”

## Engineering documentation

Scale the structure to the document. Do not add empty sections or boilerplate.

For a substantial document, cover the following as needed:

- the purpose or expected outcome;
- the intended audience and prerequisites;
- the scope and any surprising exclusions;
- the concepts needed before the task;
- the task or explanation in a reader-centered order;
- verification, failure modes, troubleshooting, or next steps.

Use task-based headings for procedures and noun-phrase headings for concepts. Move from simple to complex examples. Keep secondary background near the section that needs it instead of front-loading everything.

Treat sample code as production code:

- Make it correct, runnable, safe, idiomatic, and representative of the recommended approach.
- Include required setup, dependencies, placeholders, and expected output.
- Remove irrelevant code, but do not shorten the sample into an unsafe or misleading pattern.
- Test commands and samples when the environment permits. Never imply that untested code was verified.
- Put a short, copy-relevant caveat in the code when readers would lose it by copying only the snippet. Keep longer explanations in prose.

Give every useful diagram or screenshot one takeaway. State that takeaway in a brief caption, direct attention to the relevant part, remove distracting detail, and split a dense visual into focused views. Ensure that the prose and visual describe the same system, and provide an equivalent textual path through information that the visual alone introduces.

## Code comments and docstrings

Keep comments and docstrings as short as correctness permits.

### Comments

First ask whether clearer code can remove the need for a comment. A request to write, rewrite, improve, or shorten a comment does not establish that the code needs one. If no non-obvious information remains, recommend removing the comment instead of manufacturing replacement text. If a comment remains necessary:

- Explain **why**, a non-obvious constraint, invariant, unit, side effect, workaround, security property, concurrency assumption, or externally imposed behavior.
- Do not narrate what the next line visibly does.
- Place the comment beside the smallest code region it explains.
- Prefer one line. Add detail only when omitting it would make maintenance unsafe or error-prone.
- Delete stale comments. Do not preserve change history in source comments when version control already does so.
- Make TODO comments actionable and traceable according to project convention.

```text
Input:  Increment the retry count before retrying.
Output: Remove the comment; it only narrates the code.

Avoid: Increment the retry count.
Use:   Count the initial request so the limit matches the user-visible attempt total.
```

### Docstrings and API comments

Follow the language and project's required documentation format. Document the public contract, not the implementation.

- Start with a one-line summary of the purpose or action.
- Add parameters, return values, errors, side effects, defaults, units, thread-safety, or examples only when the signature and types do not make them clear or when the format requires them.
- For a complete public API reference, briefly document every public member and each parameter, return value, and exception. Be complete about behavior and failure modes, but do not merely repeat names and types.
- For booleans, explain both states when either is non-obvious.
- For deprecations, name the replacement and the migration action.
- Omit a docstring for a private helper when its name, types, and context already communicate its contract and project rules allow omission.

## PR descriptions

Help reviewers understand the change and assess its safety. Use this minimal shape, omitting sections that add no information:

1. **Why:** State the problem, user impact, or decision that motivated the change.
2. **What changed:** Summarize behavior and design choices, not a file-by-file diary.
3. **Validation:** Name the tests, checks, measurements, or manual scenarios actually run and their outcomes.
4. **Risk and rollout:** Include compatibility, migration, rollback, security, performance, data, deployment, or screenshot details only when relevant.

Make breaking changes and reviewer-sensitive tradeoffs easy to find. Link tickets and design documents with descriptive labels. Do not claim that a test passed unless it ran.

## Issue tracker ticket descriptions

Make the ticket actionable without prescribing an unnecessary implementation.

- Use a summary that names the observable problem or desired outcome.
- State the context and impact.
- For a bug, separate observed behavior, expected behavior, reproduction steps, environment, and evidence. Label a suspected cause as a hypothesis.
- For a change, state the desired behavior, scope, constraints, and dependencies.
- Write acceptance criteria as observable outcomes. Include implementation details only when they are genuine constraints.
- Use ordered steps for reproduction and bullets for independent criteria.
- Omit sections that would contain only “N/A.”

## Agent discussion and output

Apply this skill to communication produced while doing software work, not only to documentation files.

- Lead with the answer, result, decision, finding, or blocker.
- Report only meaningful phase changes. Do not narrate routine tool use or repeat the plan without new information.
- Explain consequential reasoning and tradeoffs; omit private scratch work and chronological debugging diaries.
- Distinguish verified behavior from inference. Point to concrete evidence such as a file and line, test result, command outcome, metric, or reproduced behavior.
- Use short paragraphs and headings only when they improve scanning. Do not wrap a tiny answer in a report template.
- When reporting completed work, state the user-visible result, verification performed, anything material that was not verified and why, and a next action only when one remains.
- Match the requested depth. Answer a narrow question narrowly; give more context when the reader must make a decision or safely operate the result.

## Final edit

Review from largest concern to smallest:

1. **Correct:** Does every claim match the source, code, data, and observed behavior?
2. **Audience-fit:** Can the intended reader act without guessing? Is anything explained that this reader already knows?
3. **Complete:** Are necessary rationale, constraints, risks, failures, and expected results present?
4. **Ordered:** Does the result come first, and does each detail appear when readers need it?
5. **Clear:** Are actors, terms, pronouns, requirements, and uncertainty explicit?
6. **Concise:** Does every sentence earn its place? Can a paragraph, phrase, acronym, or heading disappear without loss?
7. **Scannable and accessible:** Do headings, lists, links, code formatting, and media help all readers find meaning?

Stop revising when the writing is correct, sufficient for the reader's task, and free of details that do not change understanding or action.

## Sources

This guidance synthesizes:

- Michael Alley, *The Craft of Scientific Writing*, fourth edition, Springer, 2018.
- [Google Technical Writing One](https://developers.google.com/tech-writing/one)
- [Google Technical Writing Two](https://developers.google.com/tech-writing/two)
- [Google Developer Documentation Style Guide](https://developers.google.com/style)
