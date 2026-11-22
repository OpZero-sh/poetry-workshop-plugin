---
name: read-a-poem
description: "Use for a close reading of a classic poem, for finding a poem from a remembered line, or for studying how a poet uses sound and diction."
---

For a remembered phrase, run `search_poems` with the `line` field. Search by `poet` or `title` when those are known. When several titles match, distinguish the poets or first lines before choosing.

Pass the selected title and author to `get_poem`. Ground the reading in the returned text and preserve line breaks in quotations. Attribute the poet and title, and retain the returned PoetryDB source credit. When a poem has no line numbers, name the stanza or quote a short anchor. A catalog miss is grounds to try a spelling variant or say the poem was unavailable.

Choose one or two features relevant to the reader's question. For example, compare the sound of two line endings with `pronounce_word`, or use `define_word` to distinguish plausible senses of a repeated term. A modern dictionary gloss is a clue and may differ from historical usage. Explain how the choice changes the reading. End with a specific line worth rereading.
