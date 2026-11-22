# Common forms

What each form asks of its lines. Use this to check a draft against the form the writer names. Poets bend these rules on purpose, so describe a departure and ask whether it is intended before calling it a fault.

In rhyme schemes, the same letter means the same rhyme. A capital letter with a number marks a refrain: a whole line that returns.

## Forms defined by syllable count

| Form | Lines | Requirement |
| --- | --- | --- |
| Haiku in English | 3 | Often written to 5, 7 and 5 syllables. Many English haiku are shorter and do not count strictly. No rhyme. Traditionally a seasonal reference and a cut between two images |
| Tanka in English | 5 | Often 5, 7, 5, 7 and 7 syllables. No rhyme |
| Cinquain (American) | 5 | 2, 4, 6, 8 and 2 syllables. No rhyme |

Check these with one `count_syllables` call per line.

## Forms defined by meter and rhyme

| Form | Lines | Meter | Rhyme scheme |
| --- | --- | --- | --- |
| Heroic couplet | 2 | Iambic pentameter | AA |
| Blank verse | any | Iambic pentameter | Unrhymed |
| Ballad stanza | 4 | Alternating four and three stresses, usually iambic | ABCB, sometimes ABAB |
| Limerick | 5 | Lines 1, 2 and 5 have three stresses, lines 3 and 4 have two, with a triple lilt | AABBA |
| Shakespearean (English) sonnet | 14 | Iambic pentameter | ABAB CDCD EFEF GG |
| Petrarchan (Italian) sonnet | 14 | Iambic pentameter | ABBAABBA for the octave, then a sestet such as CDECDE or CDCDCD |
| Spenserian sonnet | 14 | Iambic pentameter | ABAB BCBC CDCD EE |
| Terza rima | tercets | Often iambic pentameter in English | ABA BCB CDC and onward, usually closing on a single line or couplet |
| Ottava rima | 8 | Iambic pentameter | ABABABCC |
| Rhyme royal | 7 | Iambic pentameter | ABABBCC |
| Spenserian stanza | 9 | Eight lines of iambic pentameter and a ninth of iambic hexameter | ABABBCBCC |

Sonnets usually turn in thought: after the octave in the Petrarchan form, and often before the final couplet in the Shakespearean.

## Forms defined by repetition

| Form | Lines | Pattern |
| --- | --- | --- |
| Villanelle | 19 | Five tercets and a quatrain on two rhymes. Line 1 and line 3 are refrains. Line 1 returns as lines 6, 12 and 18. Line 3 returns as lines 9, 15 and 19. Scheme: A1 b A2, a b A1, a b A2, a b A1, a b A2, a b A1 A2 |
| Sestina | 39 | Six stanzas of six lines and a three line envoi. No rhyme. The six end words of the first stanza end the lines of every later stanza in a set rotating order: each stanza takes the previous stanza's end words in the order 6, 1, 5, 2, 4, 3. The envoi uses all six |
| Pantoum | quatrains | Lines 2 and 4 of each stanza become lines 1 and 3 of the next. The last stanza often brings back lines 1 and 3 of the first |
| Triolet | 8 | Two rhymes. Line 1 returns as lines 4 and 7, line 2 returns as line 8. Scheme: A B a A a b A B |
| Ghazal in English | couplets | Each couplet stands alone. Both lines of the first couplet, and the second line of every later couplet, end with the same refrain word or phrase, with a rhyme just before it |

## Checking a draft against a form

1. Count the lines and stanzas.
2. For a counted form, run `count_syllables` on each line.
3. For a rhymed form, take each end word, compare rhyme sounds with `pronounce_word`, and write the scheme in letters. Mark near rhymes.
4. For a refrain form, compare the returning lines word for word. Small variations in a refrain are a common and accepted technique. Point them out without calling them errors.
5. For a metrical form, scan two or three representative lines before drawing a conclusion about the whole.
6. Report what matches, what departs, and ask whether each departure is intended.

## Cautions

- Syllable counts for Japanese forms in English are a convention, not a rule shared by all poets.
- Meter names describe a base pattern. Individual lines vary.
- A near rhyme in a rhymed form is a choice many poets make. Label it and move on.
- The pronunciation data is modern North American English, so a rhyme that works in the writer's accent may not register. Ask before flagging it.
