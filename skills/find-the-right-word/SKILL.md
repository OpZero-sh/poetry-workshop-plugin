---
name: find-the-right-word
description: "Look up what an English word means sense by sense, find synonyms grouped by the sense they share, and list words that begin with given letters. Use when someone asks what does this word mean, define ephemeral, which sense of light is this, give me another word for broken, a synonym that means out of order, words that start with gl, five letter words beginning with st, or needs alliteration candidates or a word for an acrostic."
---

# Find the right word

Use the Open Dictionary server to separate a word's senses, choose among synonyms, and collect words by their opening letters.

## When to use

- Meaning: "what does stile mean", "is light a verb here", "what is the noun sense of ephemeral".
- Choice: "another word for broken, as in a broken promise", "something plainer than illuminate".
- Letters: "words starting with quix", "five letter words that begin with gl", "I need an m word for this line".

For rhymes, syllables and stress use `rhyme-and-meter`. For revising a whole line use `workshop-a-line`.

## Tools

All three are on the Open Dictionary server, read only, with no sign in.

| Tool | Use | Arguments that matter |
| --- | --- | --- |
| `define_word` | Senses with part of speech, and examples and synonyms where the entry has them | `word` (a word or short phrase), `part_of_speech` (`any`, `noun`, `verb`, `adjective`, `adverb`) |
| `find_synonyms` | Synonyms grouped by the sense they share | `word` |
| `words_starting_with` | Dictionary words with a given opening | `prefix` (up to 20 letters), `length` (exact letter count, optional), `limit` (default 25, most 40) |

## Workflows

### What does it mean?

1. Call `define_word` with the word. Inflected forms are resolved to the base entry, so "feathers" returns "feather".
2. If the person gave a sentence or line, pick the sense that fits and say why. If not, give the senses in order, grouped by part of speech.
3. Use `part_of_speech` when the word is long on senses and the person only wants one class. If the tool answers that the word "has no verb senses in the dictionary", say so and show the senses it does have by calling again with `any`.
4. Quote definitions as returned. Add your own gloss only as a separate sentence.

### Another word for it

1. Fix the sense first. If it is not obvious, call `define_word` and settle which sense is meant, asking the person if two senses are both plausible.
2. Call `find_synonyms`. The result groups synonyms under the sense each belongs to, with the part of speech and a short definition of that sense.
3. Offer only the synonyms from the matching sense. For each, say how it differs: more formal or plainer, stronger or weaker, literal or figurative, and whether it changes the grammar of the sentence.
4. Put the best two or three into the person's sentence so they can hear them.
5. If the list is short or empty ("The dictionary lists no synonyms for <word>"), try `define_word` on the word: some senses carry synonyms there. Then try a near word of the same meaning and look up its synonyms.

### Words by their opening letters

1. Call `words_starting_with` with `prefix`. Add `length` for a fixed letter count and raise `limit` to 40 for a fuller list.
2. The first line gives the total and how many are shown, such as "258 words start with gl, first 5 shown". Results are alphabetical, so a short list covers only the start of the alphabet. Lengthen the prefix to move further in.
3. For alliteration, remember that it depends on sound, not spelling. Check doubtful cases (a silent first letter, c or g before e and i) with the rhyme tools' `pronounce_word` if it is available, and drop words whose first sound differs.
4. Present the words that suit the purpose, not the raw list.

## Reading the dictionary honestly

- It is a modern general dictionary built on the Wordset data, which is based on WordNet. It is not a historical, legal, medical or slang dictionary.
- **Senses can be missing.** A lookup of "stile" returned only the door frame sense and not the steps over a fence. When the person's meaning is absent, say the dictionary does not list it. Do not bend a listed sense to fit, and do not tell the person their usage is wrong.
- **Parts of speech** are limited to noun, verb, adjective and adverb.
- **Not every sense has an example or synonyms.**
- **No etymology, pronunciation, dates, usage labels or frequency.** Judgments about register and tone are yours. Label them as such.
- **Synonyms are near matches, not swaps.** Each belongs to one sense and brings its own shade.

More detail is in [references/dictionary-notes.md](references/dictionary-notes.md).

## Empty results and errors

- **"No entry for <word> in the dictionary. Check the spelling, or try the base form of the word.":** check the spelling with the person, try the base form, or try the main word of a phrase. If it is still absent, say so. You may explain the word from general knowledge if you label that it did not come from the dictionary.
- **"<word> has no <part of speech> senses in the dictionary":** call again with `part_of_speech: "any"`.
- **No words for a prefix:** shorten the prefix or remove `length`.
- **Tool failure:** say so and retry once. Do not present a remembered definition as the dictionary's.

## What the answer should look like

For a meaning: the chosen sense first, quoted, with its part of speech, then other senses briefly if useful. For synonyms: a short list under the sense, each with a few words on how it differs, then the sentence with the best options tried in it. For letter lists: the words, grouped by length if that helps, with the total available.

## Examples

**"Define ephemeral."**
`define_word` with `word: "ephemeral"`. Give the adjective sense with its example, then the noun sense.

**"Another word for broken, as in a broken promise."**
`find_synonyms` with `word: "broken"`. Use only the group for the sense about promises being violated. Offer what is there, say how each differs, and note that the other groups (out of order, financially ruined, uneven ground) do not apply.

**"I need words starting with gl for a line about light."**
`words_starting_with` with `prefix: "gl"`, `limit: 40`. Since the list is alphabetical and long, call again with `gle`, `gli`, `glo`. Pick the words to do with light and offer them with one line on each.
