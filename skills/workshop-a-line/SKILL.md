---
name: workshop-a-line
description: "Revise a line or stanza of the writer's own poem for rhyme, syllable count, meter or word choice while keeping its meaning and voice, and return a few checked alternatives. Use when a poet says help me fix this line, I need this to rhyme with, make this ten syllables, this line feels clunky, find me a better word here, tighten this stanza, help with my sonnet, villanelle or haiku, or give me options for this ending."
---

# Workshop a line

Work on the writer's draft. Offer a small number of revisions, each verified against the constraint it claims to meet, and leave the choice to the writer.

## When to use

- A draft line or stanza plus a goal: a rhyme to hit, a syllable count, a meter, a word that is not right, a form to satisfy.
- "Give me options" for an ending, an opening or a troublesome phrase in the writer's own poem.

For a single lookup with no draft (what rhymes with a word, how many syllables) use `rhyme-and-meter`. For meaning and synonyms alone use `find-the-right-word`. For a published poem use `read-a-poem`. This skill revises. It does not write the whole poem for the writer unless they ask for that.

## Tools

All are read only and need no sign in.

| Tool | Server | Use here |
| --- | --- | --- |
| `count_syllables` | Rhyme Finder | Length of the original line and of every revision that claims a count |
| `find_rhymes` | Rhyme Finder | Candidates for an end word. `syllables` narrows, `near: true` adds near rhymes, `limit` up to 60 |
| `pronounce_word` | Rhyme Finder | Stress pattern and rhyme sound of a candidate |
| `define_word` | Open Dictionary | The senses of a word in the line or of a candidate |
| `find_synonyms` | Open Dictionary | Alternatives grouped by sense |
| `words_starting_with` | Open Dictionary | Candidates that open with given letters, for alliteration or an acrostic |

## Workflow

1. **Write down the fixed points before any lookup.**
   - The original line, exactly as given.
   - The constraint: the rhyme word or scheme, the syllable target, the meter, the form.
   - What must survive: the image, the meaning, a particular word, the speaker's voice.
   If the goal is unclear ("make it better"), ask one question: what bothers them about the line. If they are exploring with no form in mind, work with the emphasis already in the line.
2. **Measure the original.** Call `count_syllables` on the line. Note any word marked with `?`: its count is an estimate, and a name or dialect word needs the writer's own pronunciation. For a meter goal, find the stresses as described in the `rhyme-and-meter` skill.
3. **Gather material for the constraint.**
   - *End rhyme:* `find_rhymes` on the word to rhyme with. Use `syllables` to get longer rhymes, since the list runs from short spellings to long and is cut at `limit`. Use `near: true` when a slant rhyme would suit, and keep near rhymes labelled as such.
   - *Length:* decide which words can be cut, swapped or expanded. Check candidate words with `count_syllables` or `pronounce_word`.
   - *Meter:* `pronounce_word` on candidates of two or more syllables to see where the stress falls.
   - *Word choice:* `define_word` on the word in question to fix the sense, then `find_synonyms`. A synonym can change register, image or grammar, so read each one in the line.
   - *Alliteration or an acrostic:* `words_starting_with` with the opening letters, and `length` if a letter count matters.
4. **Draft two or three revisions that make different trades.** For example: one that keeps the image and bends the rhyme to a near rhyme, one that keeps a perfect rhyme and changes the verb, one that reorders the line.
5. **Verify every claim.** Call `count_syllables` on each revision that is meant to hit a count. Call `pronounce_word` on a new end word and compare its rhyme sound with the target. If a revision misses, fix it or say by how much it misses.
6. **Present** the original and the revisions using [references/revision-template.md](references/revision-template.md): each with its checked count, its rhyme type, and the one word or beat that changes the effect.
7. **Hand the choice back.** Say which trade each option makes. Do not declare a winner unless asked.

Requirements of common forms are in [references/forms.md](references/forms.md). Check the writer's form there before telling them a line breaks it.

## Working principles

- **The writer's voice comes first.** Keep their vocabulary level, their line break habits and their punctuation. Do not make a plain line ornate.
- **Change as little as will solve the problem.**
- **Counts describe length, not rhythm.** Ten syllables is not yet pentameter. If the writer asked for meter, scan.
- **Dictionary data is a tool, not a judge.** The pronunciations are modern North American English. If the writer hears a word differently, their pronunciation governs, and you should say the dictionary differs.
- **Rhyme lists are raw.** They include surnames and rare words. Offer only words that could plausibly stand in this poem.
- **Do not flatter and do not rewrite out of taste.** Say what each option does.

## Privacy of the draft

Send the services only what a lookup needs: single words to the rhyme and dictionary tools, and one line at a time to `count_syllables`. Do not send the whole poem, the title or the writer's name. The services state that requests are not stored. The draft itself stays in the conversation.

## Empty results and errors

- **No perfect rhyme exists:** offer near rhymes, or move a different word to the line end and rhyme on that. Say plainly that the word has no perfect rhyme in the dictionary.
- **A word is not in the pronouncing dictionary:** ask the writer how many syllables they hear and where the stress falls, and mark the count as theirs.
- **`define_word` has no entry or lacks the sense the writer means:** the dictionary is a general modern one with gaps. Go by the writer's meaning and say the dictionary could not confirm it.
- **The constraints cannot all be met:** say which one has to give, and show the best option for each choice.
- **Tool failure:** say so, retry once, and mark any count or rhyme you could not verify.

## Examples

**"My line is 'At dusk the cattle crossed the broken stile.' Give me two endings that rhyme with stone and keep the ten syllable shape."**
Count the original (ten). `find_rhymes` on "stone" with `syllables: 1` and `syllables: 2`. Draft endings that keep the dusk and cattle image, recount each revision, confirm the rhyme sound of each new end word, and present two with their trades.

**"This feels clunky: 'The extraordinarily bright moon rose.'"**
Ask nothing: the problem is likely the long adverb. Count the line, look at the stress of the long word, use `find_synonyms` on "bright" in the sense of giving light, and offer three versions that shorten or move the weight. Show counts.

**"I'm writing a villanelle and my second refrain doesn't fit."**
Check the form's requirements in the forms reference. Ask for the two refrains and the stanza in question. Verify that the refrain end words rhyme as the form needs, then workshop the misfit line against both the rhyme and the line length the writer has set.
