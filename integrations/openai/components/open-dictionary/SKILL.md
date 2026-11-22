---
name: use-open-dictionary
description: "Check a definition, explore synonyms for the particular sense a writer intends, or list words that begin with given letters."
---

Use this connection for word meanings and word choice. It is a modern general English dictionary.

1. Call define_word with the word. Each sense has a part of speech and may have an example and synonyms. Use part_of_speech to limit the result to noun, verb, adjective or adverb. Inflected forms are answered with the base entry.
2. Identify the sense the writer intends, then call find_synonyms. Synonyms come grouped by sense. Offer only those from the matching group.
3. For words by their opening letters, call words_starting_with with prefix, and length for an exact letter count. Results are alphabetical, up to 40 per call.

Offer alternatives in a short example line and explain differences in register or meaning. Quote definitions as returned. The dictionary has gaps: a sense or a word can be missing, and it gives no etymology, dates or usage labels. When the writer's meaning is not listed, say the dictionary does not have it and go by the writer.
