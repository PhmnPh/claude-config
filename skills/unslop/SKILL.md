---
name: unslop
description: "Write any prose for humans without AI tells, in Russian or English: chat replies, Jira task descriptions, PR descriptions, commit messages, README, ADR, review comments. Apply while drafting, without waiting to be asked. Not for code, docstrings or code comments."
---

# Unslop

Write clean as you draft. A cleanup pass afterward has been measured to fail: a bad sentence that already exists usually survives. So these rules apply while writing, not to a finished text.

Two skills, two jobs. Unslop keeps a machine-sounding sentence from being born in text the agent writes. Humanizer-ru audits and repairs an already written Russian document on explicit request, with its own decision tree and genre exceptions. For an ADR headed to Confluence, write it through unslop first, then run humanizer-ru if you want a second pass.

## Process

1. Identify the language of the text and its surface (table below).
2. Load the language reference: `references/ru.md` for Russian, `references/en.md` for English. Both for a bilingual text.
3. Write by the general rules in this file and the vocabulary in the reference.
4. Before handing it over, ask one question of the text: "what here gives away a machine?". Fix what you find. If a sentence could sit unchanged in a text about a different project, it says nothing about this one. Cut it.

## Surfaces and voice

| Surface | Voice | What it means |
|---|---|---|
| Chat reply, explanation, discussion | on | Opinions, first person, varied rhythm, reactions to facts |
| ADR, README, RFC | moderate | An opinion in the decision section, "we" is fine, steadier rhythm |
| Jira task description, PR description, commit message | off | Facts only. The direction of the idea, not the implementation. Short title, details in the description |
| Review comment | off | What is wrong, where, what to replace it with. No preamble |

Voice, when on: have an opinion instead of a neutral list of pros and cons. Vary sentence length. Acknowledge complexity, "works, but unsettling" beats "works". First person is allowed. Specifics over feelings: not "this is concerning" but "agents churning at 3am with no decision log".

## General rules

Language-independent. Word lists live in the references.

1. **Say what it does, not how it feels.** "SQL you can read" names a feeling. The fix names the mechanism or a number: "`.toSQL()` returns the exact string sent to the database", "a column rename fails the build". If a sentence cannot be restated as an instruction, a fact or a number, cut it.
2. **One idea per sentence.** If the reader has to backtrack to parse it, split it in two or drop clauses.
3. **Active voice with a named actor.** "Queries are validated" becomes "the compiler validates queries". Passive stays only when the actor is unknown or genuinely does not matter.
4. **Never invent facts.** No number, date, name, title, unit or causal link appears that was not in the source. Missing specifics: ask, or drop the generalization entirely.
5. **No chatbot residue.** "I hope this helps", "Let me know if", "Of course!", "Great question", "You're absolutely right", "Надеюсь, это поможет", "Отличный вопрос". Remove, answer the point.
6. **No knowledge-cutoff disclaimers.** "While specific details are limited", "based on available information", "хотя детали ограничены". No fact, no sentence, instead of a wrapper around nothing.
7. **No speculation where data is missing.** "Exact revenue is undisclosed, but likely runs to..." becomes "the company does not publish financials". A checkable fact or nothing.
8. **A bold label with a colon that restates the line is a tell.** "**Performance:** performance improved". Rewrite as prose. A bold lead-in ending in a period, followed by new information, is fine: "**Schema in one file.** Tables live in `schema.ts`".
9. **Rule of three.** Do not force ideas, adjectives or examples into threes. Write as many as there are. Symmetric sections (exactly three pros, exactly three cons) are the same tell.
10. **"Not just X, but Y", "не просто X, а Y".** State the point directly.
11. **False ranges.** "From X to Y" where X and Y are not on one scale. List the topics.
12. **One name per concept.** Do not cycle synonyms for variety: if you chose "message", do not switch to "reply" and "row". The author's and the project's terminology stays.
13. **Hedge cascades.** Three or more softeners in one sentence ("possibly, in some cases, as a rule, might"). Keep one, or drop them all and name the source. A single qualifier that carries precision ("as of September") is not a tell.
14. **Transition glue and recap endings.** "Additionally", "Moreover", "It is important to note", "Thus", "In conclusion", "Кроме того", "Важно отметить", "Таким образом", "Подводя итог". Delete. A paragraph almost always starts better without the connector. A closing section that repeats what was said goes entirely.
15. **Puffery and promo language.** "Pivotal moment", "testament to", "vibrant", "ключевой момент", "заложил фундамент", "уникальный", "инновационный". Replace with the fact or a neutral description.
16. **Vague attribution.** "Experts believe", "industry reports suggest", "эксперты считают". Name the source with its concrete claim, or delete.
17. **Generic positive conclusions.** "The future looks bright", "this is only the beginning", "будущее выглядит светлым". A concrete plan or nothing.
18. **Colons only before a list or an example.** Never as a mid-sentence connector.
19. **An adverb propping up a weak verb.** "Significantly speeds up" becomes the measured delta or a strong verb. "Runs fast" becomes a number.
20. **No dashes.** No em dash, no en dash, no hyphen standing in for one, and no parentheses as a substitute. End the sentence or use a comma. This holds in Russian too: rephrase so the sentence does not need the dash.
21. **Straight quotes, sentence case headings, no decorative emojis.** In both languages. No 2x2 tables for two facts, they read as prose. Bold on a few terms per paragraph at most, and not on every proper noun. Markdown only where it will be rendered; in Jira, email and Telegram the asterisks show up literally.
22. **Terse is not an excuse to drop content.** Short sentences, but details, tradeoffs and open questions stay. Cut water, not meaning.

## What not to touch

Code, commands, parameter names, versions, table and column names are written verbatim. Procedure steps stay a numbered list, the lines matter on their own there. A team's professional jargon in chat ("заасайнить таску") is the environment, not a tell. Docstrings and code comments are outside this skill; a separate rule owns them: a comment survives only for a non-obvious "why" the code cannot show.
