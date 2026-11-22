# Revision template

Use this shape when presenting revisions. Keep it short enough to read at a glance.

## Layout

**Original**
> [the writer's line, unchanged]

[syllable count] syllables. [One clause on what the line already does well or where the problem sits.]

**Option 1: [the trade in three or four words]**
> [revised line]

- Count: [n] syllables (checked)
- Rhyme: [perfect / near / none] with "[target word]"
- What changes: [the one word or beat that shifts, and its effect]

**Option 2: [the trade]**
> [revised line]

- Count: ...
- Rhyme: ...
- What changes: ...

**Option 3** only when it makes a different trade from the first two.

**If none of these is right:** [one sentence naming what would have to give: the rhyme, the count or the image.]

## Rules for filling it in

- "Checked" means `count_syllables` was run on that exact line. If any word was estimated by the tool, write "about [n], with [word] estimated".
- For a meter goal, add a line with the stress pattern in `x` and `/` and one clause on how it reads.
- "Perfect" means the rhyme sounds from `pronounce_word` match. "Near" means they share a vowel or the final consonants and are not identical. Name which.
- Describe change in terms of the poem: "the cattle now arrive instead of cross", not "improved flow".
- Keep the writer's capitalisation and punctuation style.
- Do not rank the options. If asked which you would choose, answer and give the reason in one sentence.

## When working on a stanza

- Show the stanza once with the lines numbered.
- Give the syllable count per line, from one `count_syllables` call per line.
- Give the rhyme scheme in letters, marking near rhymes.
- Then revise only the lines that miss the writer's goal, with the template above for each.

## When the writer asks only for words, not lines

Give a short grouped list instead:

- **Perfect rhymes that fit the poem:** [words]
- **Near rhymes worth a look:** [words]
- **Left out:** names and rare words from the raw list

Add the syllable count beside any word of more than one syllable.
