# Dictionary notes

How the Open Dictionary server behaves, from live calls in November 2026.

## Source

- An English dictionary served by OpZero from the Wordset dictionary data, which is based on WordNet.
- The server's description calls it a general dictionary and says it is not a specialist or legal one. It also says requests are not stored.
- This plugin is not affiliated with Wordset or WordNet.

## `define_word`

The result opens with the headword and the number of senses, such as "ephemeral: 2 senses." Each sense then has:

| Part | Always present? |
| --- | --- |
| A number and the definition | Yes |
| Part of speech in parentheses: noun, verb, adjective or adverb | Yes |
| `Example:` a short usage example | No |
| `Synonyms:` words that share this sense | No |

Behaviour:

- **Base forms.** An inflected word is answered with its base entry: "feathers" returned the entry for "feather". The headword in the first line shows which entry you got.
- **Phrases.** Short phrases with their own entry work, for example a verb with its particle.
- **Sense order.** Do not assume the first sense is the commonest. The first sense returned for "feather" was a rowing term, ahead of the bird's feather.
- **`part_of_speech` filter.** Limits the result to one class. When the word has no sense in that class, the tool answers "<word> has no <class> senses in the dictionary." instead of returning the other senses.
- **Missing entry.** "No entry for <word> in the dictionary. Check the spelling, or try the base form of the word."

## `find_synonyms`

The result opens with a count, such as "8 synonyms for broken across 7 senses." Each group is one sense: the synonyms first, then the part of speech and a short definition of that sense in parentheses.

- Groups follow senses, so the same word can call up unrelated groups. Choose the group, then the word.
- A sense with no synonyms is left out.
- A word with no synonyms in any sense returns "The dictionary lists no synonyms for <word>."
- A word with no entry returns the same "No entry" message as `define_word`.
- Antonyms, related words and broader or narrower terms are not provided.

## `words_starting_with`

The result opens with the total and what is shown, such as "258 words start with gl, first 5 shown." or "31 words start with gl and have 5 letters."

- Words come in alphabetical order.
- `limit` goes up to 40. To see more of a long list, call again with a longer prefix.
- `length` is an exact letter count from 2 to 30.
- The list holds dictionary headwords, including technical and rare ones. It has no frequency information, so common and obscure words sit side by side.
- There is no search by ending, by pattern with gaps, or by sound. For words that end alike in sound, use the rhyme tools.

## Coverage limits seen in testing

- A sense that many readers would expect can be absent. The entry for "stile" had the door frame sense only.
- Coinages and nonsense words have no entry.
- The dictionary gives no dates. It cannot say whether a sense existed when an old poem was written. For classic poetry, treat its definitions as the modern starting point and reason from the line.

## Choosing among synonyms for a line of verse

Check each candidate against the line on five points:

1. **Sense.** Does it belong to the same sense group as the word being replaced?
2. **Register.** Is it as plain or as formal as the words around it?
3. **Image.** Does it bring a picture the poem does not want, or lose one the poem needs?
4. **Grammar.** Does it take the same objects and prepositions?
5. **Sound.** Syllable count, stress and how it sits beside its neighbours. The rhyme tools can verify the first two.

State the difference each candidate makes. The writer decides.
