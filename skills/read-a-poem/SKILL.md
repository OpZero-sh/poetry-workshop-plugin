---
name: read-a-poem
description: "Find a classic poem by title, poet or a half remembered line, show its text, and give a close reading grounded in the words on the page. Use when someone says find the poem that goes, what's that poem with the line, show me Ode to a Nightingale, what does this poem mean, explain this stanza, how does the rhyme or meter work here, which poems by Keats do you have, or wants to study a poet's sound and diction."
---

# Read a poem

Locate the poem in the Classic Poetry library, quote it exactly, and build the reading from what the text does.

## When to use

- Finding: "the Dickinson poem with a thing with feathers", "poems by Christina Rossetti", "do you have Ozymandias".
- Reading: "what is going on in the last stanza", "why does this line sound so heavy", "compare the endings of these two sonnets".

For a poem chosen for the day use `poem-of-the-day`. For the learner's own draft use `workshop-a-line`. For a quick rhyme, syllable or stress lookup with no poem involved use `rhyme-and-meter`.

## Tools

All are read only and need no sign in.

| Tool | Server | Use | Arguments that matter |
| --- | --- | --- | --- |
| `search_poems` | Classic Poetry | Find poems | `line`, `poet`, `title` (any combination), `limit` (default 10, most 20) |
| `get_poem` | Classic Poetry | Full text of one poem | `title` (required), `author` |
| `list_poets` | Classic Poetry | Who is in the library | `name` (part of a name, optional) |
| `pronounce_word` | Rhyme Finder | Stress and rhyme sound of a word | `word` |
| `count_syllables` | Rhyme Finder | Syllables per word in one line | `text` |
| `define_word` | Open Dictionary | Senses of a word | `word`, `part_of_speech` |

## Workflow

1. **Search.**
   - A remembered phrase: `search_poems` with `line`. Use the few words the person is surest of. Fewer words match more reliably than a long misremembered phrase.
   - A known title or poet: use `title` and `poet`. Both accept part of a name, and filters combine.
   - "What do you have by ...": `search_poems` with `poet` and `limit: 20`. If the poet is not found, check the stored spelling with `list_poets`.
2. **Read the result list.** Each entry shows the title, the poet, the line count and the poem's first line. The first line shown is not the line that matched. If several entries could be the one, show them and ask. If the count line says more matched than are shown, narrow with another field.
3. **Fetch the text.** Call `get_poem` with the exact `title` from the result and always pass `author`. Without an author, a shared title returns one poem with no warning that others exist.
4. **Check length before quoting in full.** The line count is on the search result. Show a short poem whole. For a long poem, show the passage that matters and say how long the whole is.
5. **Quote exactly.** Keep line breaks, stanza breaks, spelling and punctuation as returned. Give the title and poet. Refer to a place by stanza and line within the stanza, or by a short quoted anchor, since the text has no line numbers.
6. **Build the reading from one or two features that answer the question.** Do not survey every device. Work from observation to pattern to effect: what the words do, where that repeats or breaks, and what difference it makes to the reading. Terms are defined in [references/sound-and-structure.md](references/sound-and-structure.md).
7. **Use the other tools as evidence, sparingly.**
   - Two line endings that may or may not rhyme: `pronounce_word` on each and compare the rhyme sounds.
   - A line whose rhythm is in question: `count_syllables` on that single line, then `pronounce_word` on its longer words for stress.
   - A word whose sense matters: `define_word`, then say which sense fits the line and why.
8. **End with one line worth rereading** and the reason.

## Evidence rules

- Every claim about the poem points to words in the returned text.
- Keep description and interpretation apart: "the stanza ends on a near rhyme" is description, "which leaves the thought unsettled" is your reading. Offer readings as readings.
- The pronunciation data is modern North American English and the dictionary is a modern general dictionary. A poet writing centuries ago may have heard a rhyme or meant a sense that neither records. Say "in modern pronunciation" or "in the modern sense" when it matters, and do not correct the poet.
- Do not bring in the poet's life as proof of what a line means. Context is welcome when labelled as context.
- Texts are older public domain transcriptions. Punctuation and wording can differ from modern scholarly editions. If a reader's copy differs, both may be legitimate.

## Empty results and errors

- **"No poems match":** try fewer words, a different word from the line, or the poet alone. Spelling in the texts is often old or British.
- **"No poem titled ... in the library":** search by `title` to find the stored form. Titles of untitled poems are usually their first lines.
- **"No poet named ...":** call `list_poets` with part of the surname. Some names are stored in an unexpected form.
- **The poem is not in the library.** The library holds classic public domain poetry in English from a fixed list of poets. Most twentieth century and all contemporary poets are absent. Say so plainly. Do not reproduce a poem from memory in its place. If the reader pastes the text, the reading can go ahead from their copy.
- **Two poems with the same title by the same poet:** `get_poem` can return only one of them. Tell the reader which first line you got and that the other cannot be fetched by title.

Library coverage, search behaviour and text quirks are in [references/library-notes.md](references/library-notes.md).

## What the answer should look like

The poem or passage in a quotation block with title and poet. Then the reading in two to four short paragraphs, each tied to a quoted word or line. Then the line to reread. Mention the source once: the text comes from the Classic Poetry service, which draws on PoetryDB.

## Examples

**"Find the Dickinson poem with 'a thing with feathers' in it and show me what the rhyme does in the first stanza."**
`search_poems` with `line: "thing with feathers"` and `poet: "Dickinson"`. `get_poem` with the returned title and `author: "Emily Dickinson"`. Quote stanza one. Call `pronounce_word` on the second and fourth line endings, compare their rhyme sounds, and say whether the pair is a perfect or a near rhyme in modern pronunciation and what that does to the close of the stanza.

**"What odes by Keats do you have?"**
`search_poems` with `poet: "Keats"`, `title: "ode"`, `limit: 20`. List titles with line counts. Offer to open one.

**"Can you show me The Waste Land?"**
`get_poem` reports no such title. Say the library does not include it, do not paste it from memory, and offer a poem the library does hold or a reading of a passage the reader supplies.
