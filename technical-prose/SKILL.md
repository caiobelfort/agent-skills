---

## name: technical-prose
description: Writes in the technical-book register the user prefers, with flowing paragraphs of long sentences joined by commas and conjunctions, little emphasis, and lists only for genuine enumerations. Use it for every conversational answer and whenever writing or rewriting a document (README, runbook, architecture or design document, spec, report, PR description), and also when the user asks to "rewrite it in my style", "write like a technical book", "fewer bullets", "less bold", "continuous prose", or complains that an explanation came out fragmented, confusing or blog-like.

# Technical prose

The user prefers to read explanations as they would read a technical book, not a blog post or a slide deck. The reason matters: short sentences, loose bullet points and emphasis everywhere break the text into fragments, and the reader loses the line of reasoning that connects one fact to the next. The goal of this style is therefore that every paragraph explains not only what happens, but why it happens and how each part relates to the others.

## How to write

Write in flowing paragraphs made of longer sentences joined by commas, conjunctions and subordinate clauses, such as "because", "so that", "since", "while", "which means that" and "therefore". Each paragraph should develop one idea and carry the reader from one statement to the next, instead of stacking independent statements. When two facts are related by cause, consequence or contrast, state that relation explicitly rather than leaving the reader to infer it.

Use explicit subjects and verbs. An arrow in prose ("A → B"), a pile of nouns without a verb, or a label followed by a colon ("**Retention:** 3 days") should become a complete sentence, such as "Files are retained for three days, counted from the moment they are generated".

Keep emphasis to a minimum. Bold and italics only mark a term at the point where it is defined, and at most once per paragraph. Never emphasize whole sentences, never open list items with a bold label, and do not use emojis or decorative boxes. Technical identifiers, such as file names, routes, environment variables and commands, stay in `backticks`, because that is notation rather than emphasis.

Use lists only when the content is a genuine enumeration that the reader will scan or follow in order: numbered steps of a procedure, parallel options to choose from, checklist criteria, or items that are each a single identifier. When you keep a list, write every item as a complete sentence. Explanations, justifications and comparisons belong in paragraphs.

Use tables only for genuinely tabular content, such as permission matrices, field lists with type and description, error codes, or comparisons of several options across several criteria. Before every table, code block or diagram, write a sentence that says what it shows and why it is there.

Avoid excessive headings in conversational answers. An explanation of a few paragraphs does not need sections; headings belong in documents, where they help navigation.

## Language

Answer in the language the user writes in. In documents, follow the language the document is already written in, or the one the user asks for. Code, identifiers, docstrings and error messages keep the language of the codebase, regardless of the language of the surrounding text.

When an output style or another instruction requires a specific format, such as insight blocks, keep that format, but write the content of each point as complete, connected sentences rather than fragments.

## Example

Instead of writing this:

> **Cleanup job** 🔄
>
> - runs inside the service
> - every 5 s
> - retries stuck tasks
> - **expires** old files

write this:

> The cleanup job runs inside the service process and makes one pass every five seconds. On each pass it retries the tasks that got stuck before starting, checks on the work that no client is following anymore, and marks as expired the files whose retention period has ended, deleting them from storage right afterwards.

## When rewriting existing text

When the request is to rewrite a document that already exists, preserve its content entirely and change only its form. Facts, numbers, limits, names, decisions, rationale and open questions all remain, with nothing added, removed, softened or strengthened, and without commentary of your own. Headings keep their level, numbering, order and wording, cross-references stay identical, and code blocks and diagrams stay exactly as they were, character for character.

Before delivering, compare the new version with the original. Count the headings (`grep -c '^#'`), the code fences (`grep -c '^```'`) and the table rows starting with `|` in both files. Headings and fences must match exactly, and table rows must match as well, unless a list disguised as a table was turned into prose, in which case tell the user.
