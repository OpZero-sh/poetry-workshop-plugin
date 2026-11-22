---
name: use-rhyme-finder
description: "Explore rhymes, pronunciation and syllable counts for a word or a line in progress."
---

Use this connection for the sound of English words. It works from the CMU Pronouncing Dictionary, so results reflect modern North American pronunciation and not spelling.

1. For rhymes, call find_rhymes with the word. Results run from short spellings to long and include surnames and rare words, so choose the ones that suit. Set syllables to reach longer rhymes, near to true for near rhymes, and limit up to 60.
2. For length, call count_syllables on one line at a time. It returns a count per word and one total and ignores line breaks. A count marked with a question mark is an estimate for a word the dictionary lacks.
3. For stress, call pronounce_word. Vowels carry a digit: 1 is primary stress, 2 secondary, 0 unstressed. The rhyme sound line is the part of the word from the stressed vowel on. Two words with the same rhyme sound are perfect rhymes.

When helping with a line, start from the writer's original and the rhythm they want. Offer a small set of choices, recount any line that claims a syllable target, and say what each choice does to meaning and sound. Label near rhymes as near. If the writer pronounces a word differently from the dictionary, their pronunciation governs.
