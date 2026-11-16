# AGENTS.md

Project-specific rules, formatting guidelines, and skill definitions live in `.agents/`.

These rules are obligatory for this repo.

See `.agents/skills/` for mode-specific instructions:

- `bun-instead-of-node` for use Bun for all runtime operations.
- `caveman` for ultra-compressed response mode.

Obligatory skills for proper functions:

- `obsidian-markdown` for Obsidian Flavored Markdown syntax.
- `dt-technical-writer` for Distilled Technical writing, including chat responses.
- `lint-md` for markdownlint workflow.

You MUST load / read these before executing ANY command or reading ANY file from this repo.

## VS Code

Recommended extensions in `.vscode/extensions.json`.

Settings enable on-type markdownlint auto-fix.

## Communication

When responding in the chat, state what it is, what happened, or what needs to be done.

Avoid contrast or discarding phrases ("this is neither X nor Y", "not to be confused with", "unlike") unless that exclusion is the requested result.

Contrast adds noise. Affirmation specifies.

Do not present an inference as a fact.

If the evidence is incomplete, use terms like "for now", "it seems", or "according to this note".

## Dates

Dates use the `YYYY-MM-DD` format and time `HH:mm` in 24 hours.

The reference timezone is Paraguay (`America/Asuncion`, UTC-3).

## Emphasis

Do not use bold (`**text**`) as emphasis in text at all whenever possible.

Where hierarchy or separation is needed, use appropriate headings, lists, callouts or wikilinks.

The repo's `markdownlint` already flags an error when bold is used instead of headings.

If italics are needed, use underscores (`_italicized_`), not asterisks (`*italicized*`).

In the chat with the agent, it is acceptable to use bold or other emphasis resources when replying. This applies only to content written or edited.

## Typography

Avoid em dashes, en dashes and other typographic dashes.

If a dash is needed, use the standard keyboard one (for example, `-`).

Do not use dashes to shorten or join ideas together, If a sentence needs to continue, use comma, semicolon, or a separate sentence.

With quotes: only straight keyboard quotes (for example, `"` and `'`).

Do not use curved or smart quotes (for example, `“ ”` and `‘ ’`) nor other typographic symbols.

This includes both the chat with the agent and files / tool calls, all generated/stored text must follow this rule.

## Writing

Write in complete and natural language, not telegraphic nor stylized like a report or story.

It is best that sentences read well on their own, without compressing ideas to "optimize" communication.

Do not concatenate several independent ideas in the same paragraph or on a single line, even if each is a sentence with a period.

If they are distinct facts, they go in separate paragraphs (blank line between them) or in list items.

A dense block of pasted sentences is illegible when revisiting.

Lists and bullets can be concise, but each item must be an understandable sentence or thought, not a fragment that depends on a dash or abbreviated code to make sense.

An item should not chain three or four topics either. Split it.

## Moving files

A.k.a `git mv` vs `mv`

To avoid losing history and preserve traceability in git.

Files already tracked by git are always moved with `git mv`.

It is forbidden to delete files (for example, `rm`, `Remove-Item`, etc.) and recreate them in the new destination.

Files that are not yet tracked are moved with the normal command (for example, `mv`, `Move-Item`, etc.).

This applies to everything that lives in any repository or new files that have not yet been added to git.

## CONTEXT.md

You are operating in a workspace that uses a centralized context file. You must strictly adhere to the following rules regarding memory and context tracking.

Do not use your built in memory tools, internal knowledge saving functions, or proprietary state storage to record information about this repository, user preferences, or architectural decisions. Treat your internal memory as ephemeral.

Your only source of persistent memory for this project is the file located at .agents/CONTEXT.md. You must read .agents/CONTEXT.md at the beginning of every task or session before taking any other action, analyzing code, or proposing solutions.

Only store information directly relevant to the architecture, business logic, and coding conventions of this specific repository. Do not record conversation history, agent-specific tool configurations, generalized programming knowledge, task execution logs, or raw memory dumps in .agents/CONTEXT.md. Ensure the file remains a clean, repository-specific reference document.

When you establish new architectural decisions, identify recurring user preferences, or learn important repository specific rules, you must update .agents/CONTEXT.md directly using standard file editing tools. Do not save this information to your internal memory tools.

If you are asked to remember something, write it to .agents/CONTEXT.md. If you cannot find a specific rule, check .agents/CONTEXT.md before asking the user.
