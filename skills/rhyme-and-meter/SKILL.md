---
name: rhyme-and-meter
description: "Look up rhymes, near rhymes, syllable counts, pronunciation and stress for English words and lines, and scan a line of verse. Use when someone asks what rhymes with a word, do these two words rhyme, how many syllables is this line, is my haiku 5 7 5, where is the stress in this word, how is this pronounced, is this iambic pentameter, scan this line, or what is the rhyme scheme of a stanza."
---

# Rhyme and meter

Answer questions about the sound of words and lines with the Rhyme Finder server, which works from a pronouncing dictionary rather than from spelling.

## When to use

- Rhymes: "what rhymes with stone", "two syllable rhymes for alone", "near rhymes for silver".
- Counting: "how many syllables", "check my haiku", "is this line ten syllables".
- Stress and meter: "where is the stress in record", "scan this line", "is this iambic".
- Rhyme checks: "do love and move rhyme", "what is the rhyme scheme here".

To revise a draft line under several constraints at once use `workshop-a-line`. For meaning and synonyms use `find-the-right-word`. For a published poem's text use `read-a-poem`.

## Tools

All three are on the Rhyme Finder server, read only, with no sign in.

| Tool | Use | Arguments that matter |
| --- | --- | --- |
| `find_rhymes` | Rhymes for one word | `word`, `syllables` (1 to 8), `near` (default false), `limit` (default 30, most 60) |
| `count_syllables` | Syllables per word and in total for a line | `text` (up to 600 characters) |
| `pronounce_word` | Phonemes, stress, syllables and rhyme sound for one word | `word` |

How to read the output, including the phoneme symbols and stress digits, is in [references/pronunciation-data.md](references/pronunciation-data.md).

## Workflows

### Rhymes for a word

1. Call `find_rhymes` with `word`. Ask for `limit: 60` when the person wants choice.
2. The list is ordered from short spellings to long and mixes in surnames and rare words. It is not ordered by usefulness. Pick the words that suit the person's line and leave out names unless they fit.
3. For longer rhymes, call again with `syllables` set to 2, 3 and so on. Without it, a long list is cut off before the longer words appear.
4. If there are few or no perfect rhymes ("No rhymes for <word> in the dictionary. Try near rhymes."), call again with `near: true`. Near rhymes share the stressed vowel and the final sound. Present them under their own heading and be selective: many will be weak.
5. Give the result grouped by syllable count, perfect rhymes first, then near rhymes. Say how many perfect rhymes exist in all when the tool reports it.

### Do these words rhyme?

1. Call `pronounce_word` on each word.
2. Compare the `Rhyme sound` lines. The same rhyme sound is a perfect rhyme. The same final consonants with a different vowel, or the same vowel with different consonants, is a near rhyme. Nothing shared is no rhyme.
3. If a word has several pronunciations, say which one makes the rhyme work.
4. Spelling that matches while sounds differ is an eye rhyme. Say so. In an older poem add that the pair may have rhymed in the poet's speech.

### Counting syllables

1. Call `count_syllables` once per line. The tool returns one total for the whole text and ignores line breaks, so a three line haiku needs three calls.
2. Read the per word counts. A count followed by `?` is an estimate for a word the dictionary does not list, and those words are named at the end. Tell the person which words were estimated.
3. Numerals in the text are skipped. Write numbers as words before counting.
4. Some words have more than one accepted count ("fire", "every", "heaven" in older verse). The tool uses its first listed pronunciation. If a line is one syllable off a target, check such words with `pronounce_word` and say that the count depends on how the word is spoken.
5. Report the total and the per word breakdown. For a form with fixed counts, state each line's count against its target.

### Stress and scansion

1. Call `count_syllables` on the line for the syllable total.
2. Call `pronounce_word` on each word of two or more syllables to find its stressed syllable: the vowel marked `1`. A vowel marked `2` has secondary stress and one marked `0` has none.
3. Place stress on the one syllable words by sense: nouns, main verbs, adjectives and adverbs usually take stress, and articles, prepositions, conjunctions and auxiliaries usually do not. The dictionary's stress marks on one syllable words are not a guide to how they behave in a line.
4. Mark the line, group the syllables into feet, and name the meter only if the pattern holds. Terms and the method are in [references/meter-and-scansion.md](references/meter-and-scansion.md).
5. Present the scansion as a reading. Mark any foot that could go either way and say why. Do not report a line as "wrong" for a common variation.

### Rhyme scheme of a stanza

1. Take the last word of each line.
2. Call `pronounce_word` on each and compare rhyme sounds.
3. Assign letters, treating near rhymes as a match and marking them, for example A B A B with the second A marked as near.

## Empty results and errors

- **"The pronouncing dictionary does not list <word>":** check spelling, try the base form, or try a common spelling of a name. For an invented or dialect word, ask how the person says it and reason from that, saying that the dictionary could not confirm it.
- **"No rhymes for <word> in the dictionary. Try near rhymes.":** do that, and say plainly when a word has no good rhyme.
- **Hyphenated or multi word input to `find_rhymes` or `pronounce_word`:** look up the last word, since that is what carries the rhyme.
- **Tool failure:** say so and retry once. Do not present a guessed rhyme list or count as dictionary output.

## Limits to state honestly

- The data is the CMU Pronouncing Dictionary: modern North American English. Other accents, older pronunciations and song or dialect forms can differ, and the person's own ear decides.
- The tools return facts about single words. Meter is a judgment about a whole line, and two careful readers can scan a line differently.
- Rhyme lists include proper names and rare words and are not ranked by quality.

## Examples

**"What rhymes with stone? I need two syllables."**
`find_rhymes` with `word: "stone"`, `syllables: 2`, `limit: 60`. Pick the ordinary words from the result, leave out surnames, and note how many rhymes exist in all.

**"Is my haiku 5 7 5?"**
Call `count_syllables` on each of the three lines. Report three counts against 5, 7 and 5 with any estimated words flagged.

**"Is 'Shall I compare thee to a summer's day' iambic pentameter?"**
`count_syllables` gives ten. `pronounce_word` shows the stress in "compare" on its second syllable and in "summer's" on its first. Mark the line, show five feet, and note that the third foot is light and can be read with little stress on either syllable. Call it iambic pentameter with that variation.
