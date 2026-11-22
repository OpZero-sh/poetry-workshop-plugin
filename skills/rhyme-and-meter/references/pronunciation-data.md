# Pronunciation data as the server returns it

The Rhyme Finder server uses the CMU Pronouncing Dictionary, a dictionary of North American English pronunciations written in ARPAbet. Everything below was checked against live results in November 2026.

## `pronounce_word`

A result for a word with one pronunciation:

```
heaven has 1 pronunciation. Digits mark stress: 1 primary, 2 secondary, 0 none.

- HH EH1 V AH0 N
  Syllables: 2
  Rhyme sound: EH V AH N
```

A word with several pronunciations lists each one as `Pronunciation 1`, `Pronunciation 2` and so on, each with its own syllable count and rhyme sound. The noun and the verb "record" are an example: one pronunciation has the stress on the first vowel and two have it on the second.

### Reading a pronunciation

- Symbols are separated by spaces. Each symbol is one sound (a phoneme), not one letter.
- Vowel symbols end in a digit. Consonant symbols have no digit.
- The digit is the stress on that vowel: `1` primary stress, `2` secondary stress, `0` unstressed.
- The number of vowel symbols is the number of syllables.
- `Rhyme sound` is the part of the word from its main stressed vowel to the end, with the digits removed. Two words with the same rhyme sound are perfect rhymes. For a word with no primary stress, such as the usual pronunciation of "the", the rhyme sound is its vowel onward.

### Vowel symbols

| Symbol | As in | Symbol | As in |
| --- | --- | --- | --- |
| AA | father, odd | IH | it, bid |
| AE | at, cat | IY | eat, bee |
| AH | hut, and with `0` the neutral vowel in about | OW | oat, go |
| AO | ought, law | OY | toy |
| AW | cow, out | UH | hood, could |
| AY | hide, my | UW | two, blue |
| EH | Ed, red | ER | hurt, and with `0` the ending of butter |
| EY | ate, day | | |

### Consonant symbols

| Symbol | As in | Symbol | As in |
| --- | --- | --- | --- |
| B | be | N | knee |
| CH | cheese | NG | ping |
| D | dee | P | pea |
| DH | thee | R | read |
| F | fee | S | sea |
| G | green | SH | she |
| HH | he | T | tea |
| JH | gee, judge | TH | theta, thin |
| K | key | V | vee |
| L | lee | W | we |
| M | me | Y | yield |
| | | Z | zee |
| | | ZH | seizure |

Pairs that are easy to confuse: `DH` (this) and `TH` (thin), `AH` (hut) and `AA` (father), `AO` (law) and `AA` (odd), `ER` (one vowel sound with an r colour) and `EH R` (two sounds, as in "air").

## `count_syllables`

```
10 syllables in 8 words.

- 10 syllables
  shall 1, i 1, compare 2, thee 1, to 1, a 1, summer's 2, day 1
```

- Words are lowercased and punctuation is dropped. Possessives and contractions are counted as written.
- The whole text gets one total. Line breaks are ignored, so count one line per call when per line totals matter.
- A count with `?` after it is an estimate for a word that is not in the dictionary. A final line names those words: "Not in the dictionary, estimated: ...". Poetic contractions such as "o'er" can fall into this group.
- Numerals are skipped and do not appear in the breakdown.
- When a word has several pronunciations with different syllable counts, the count shown follows the first one listed by `pronounce_word`. "fire" is counted as two.
- `text` can be up to 600 characters.

## `find_rhymes`

```
Rhymes for stone (1 syllable).

- Perfect rhymes (161 in all, 10 with 2 syllables shown)
  alone, arone, atone, ...
```

- The first line repeats the word and its syllable count.
- `Perfect rhymes` gives the total number in the dictionary and then up to `limit` words. With `syllables` set, it also says how many of that length are shown.
- Words are ordered by spelling length and then alphabetically. Common words, rare words and surnames are mixed together. Words that sound the same as the input but are spelled differently, such as "bare" for "bear", are included.
- With `near: true` a second group, `Near rhymes`, follows. The tool defines these as words that share the stressed vowel and the final sound. The group is broad and contains many names.
- The largest `limit` is 60. For a word with many rhymes, use `syllables` to reach the longer ones.
- A word with no perfect rhymes returns "No rhymes for <word> in the dictionary. Try near rhymes."
- A word the dictionary does not have returns "The pronouncing dictionary does not list <word>. Check the spelling, or try a related form."
- Input is not case sensitive.

## What the data cannot tell you

- **Other accents.** The dictionary records North American pronunciations. Rhymes and counts that depend on a British, Irish, Australian, Caribbean or other accent may come out differently. Vowel mergers are the usual cause.
- **Older pronunciations.** A pair in a poem from an earlier century may have rhymed for the poet and not in this data.
- **Stress in context.** The digits describe a word spoken alone. In a line, one syllable words gain or lose stress by meaning and position, and a secondary stress can be promoted to carry a beat.
- **Which pronunciation is meant.** For a word with several, the tools do not know the part of speech or sense in your line. Choose by reading the line.
- **Names and coinages.** Many names are present. Invented words are not, and estimates for them are rough.
