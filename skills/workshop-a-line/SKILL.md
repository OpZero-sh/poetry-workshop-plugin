---
name: workshop-a-line
description: "Use when a poet wants to revise a line for meter, rhyme, or word choice while keeping its meaning and voice."
---

Start with the writer's original line and the constraint they gave. Keep the image or meaning they want to preserve. If they're exploring without a form in mind, work with the emphasis already present in the line.

1. For a length constraint, call `count_syllables` on the original line. Check the returned unknown words. A name, contraction or local pronunciation may need the writer's reading. Mark an uncertain count.
2. For an end rhyme, use `find_rhymes` on the intended rhyme word. Narrow by syllables when it helps. Use `near: true` when slant rhymes fit and label those separately. Check pronunciation variants with `pronounce_word` when they change the result.
3. For a semantic constraint, use `define_word` or `find_synonyms` for the relevant sense. A dictionary synonym can change register, imagery or grammar. Read each candidate in the line.
4. Offer two or three revisions with different tradeoffs. Recount each line claimed to meet a precise syllable target. Show the original beside the revisions and point to the one word or beat that changes the effect.

A syllable count describes length. Scan spoken stresses separately when the user asks for meter. Keep unpublished drafts in the conversation where possible and send only the individual words or lines needed by a lookup.
