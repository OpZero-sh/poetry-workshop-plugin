# Meter and scansion

Vocabulary for describing rhythm in English verse, and a method for scanning a line with the pronunciation tool.

## Feet

A foot is a unit of two or three syllables. In the patterns below `x` is an unstressed syllable and `/` is a stressed one.

| Foot | Pattern | Adjective | Example word |
| --- | --- | --- | --- |
| Iamb | x / | iambic | compare |
| Trochee | / x | trochaic | summer |
| Anapest | x x / | anapestic | understand |
| Dactyl | / x x | dactylic | happily |
| Spondee | / / | spondaic | heartbreak |
| Pyrrhic | x x | pyrrhic | two light syllables, such as "to a" inside a line |

Iambic and anapestic rhythms rise toward the stress. Trochaic and dactylic rhythms fall away from it.

## Line lengths

| Feet per line | Name |
| --- | --- |
| 1 | monometer |
| 2 | dimeter |
| 3 | trimeter |
| 4 | tetrameter |
| 5 | pentameter |
| 6 | hexameter |
| 7 | heptameter |
| 8 | octameter |

A meter is named by foot and length: iambic pentameter is five iambs, ten syllables in its plain form. Trochaic tetrameter is four trochees, eight syllables.

## Related terms

| Term | Meaning |
| --- | --- |
| Accentual syllabic verse | Verse that counts both stresses and syllables. Most metrical English verse since the sixteenth century |
| Accentual verse | Verse that counts stresses only and lets the number of syllables vary |
| Syllabic verse | Verse that counts syllables only, such as English haiku written to 5, 7 and 5 |
| Free verse | Verse with no regular meter |
| Blank verse | Unrhymed iambic pentameter |
| Common meter | Alternating lines of iambic tetrameter and iambic trimeter, as in many hymns and ballads |
| Substitution | A different foot in place of the expected one |
| Inversion | A trochee where an iamb is expected, most often at the start of a line or after a pause |
| Feminine ending | An extra unstressed syllable at the end of an iambic line |
| Catalexis | A final unstressed syllable left off, common in trochaic lines |
| Promotion | A normally light syllable carrying a beat because of its position between two lighter ones |
| Demotion | A normally stressed syllable losing its beat between two stronger ones |
| Elision | Two syllables run together as one to keep the count, such as "heaven" or "flower" spoken as one syllable in older verse |
| Caesura | A pause inside a line |

## Scanning a line with the tools

1. **Count.** `count_syllables` on the single line gives the total and the count per word. Note any word marked as estimated.
2. **Fix the stress in longer words.** `pronounce_word` on each word of two or more syllables. The vowel marked `1` is stressed. A vowel marked `2` has secondary stress: treat it as able to take a beat or give one up, depending on its neighbours. Vowels marked `0` are unstressed.
3. **Choose among pronunciations.** If a word has several, pick the one that fits the part of speech and sense in the line. A noun and its matching verb often differ only in stress.
4. **Place the one syllable words.** Stress falls by meaning. Nouns, main verbs, adjectives and most adverbs are usually stressed. Articles, prepositions, conjunctions, auxiliary verbs and most pronouns are usually light. Contrast or emphasis can override this.
5. **Write the pattern** with `x` and `/` over or under the syllables.
6. **Look for the base meter.** Try the commonest fits first: with ten syllables, iambic pentameter. With eight, iambic or trochaic tetrameter. With a triple lilt, anapests or dactyls.
7. **Account for departures** using the related terms above. An inversion in the first foot, a feminine ending or one promoted syllable is ordinary variation and does not change the name of the meter.
8. **State your confidence.** If a foot can be read two ways, show both. If no pattern holds, say the line is not regular and describe what it does instead: the number of stresses, where they cluster.

## A worked line

"Shall I compare thee to a summer's day?"

- `count_syllables` returns ten syllables.
- `pronounce_word` puts the stress in "compare" on the second syllable and in "summer's" on the first.
- By sense, "day" is stressed and "a" and "to" are light. Of the opening pair, "I" takes the beat.
- Pattern: x / x / x x x / x /, or with a light beat on "to", x / x / x / x / x /.
- Reading: iambic pentameter. The third foot ("thee to") is the weak spot. It can be heard as a pyrrhic or as an iamb with a promoted "to".

## Judgments to avoid

- Do not call a line "incorrect" because one foot varies. Variation is part of how meter works.
- Do not scan from the dictionary digits alone. They describe words spoken in isolation.
- Do not assume a poet's pronunciation matched the dictionary. Elisions and older stress patterns are common in classic verse.
- Do not force free verse into feet. Describe its line lengths, stresses and pauses.
- Do not claim precision the method does not have. Scansion is a careful reading, and readers differ.
