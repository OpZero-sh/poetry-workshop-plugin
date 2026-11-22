# Poetry Workshop

Find the poem you remember from one line, hear how its ending works, then bring the same attention to a line of your own. Poetry Workshop pairs a searchable classic-poetry library with a pronunciation dictionary and sense-by-sense word lookup.

[Connect with Claude, ChatGPT, Muse Code, or Grok](PROVIDERS.md)

> “Find the Dickinson poem with ‘a thing with feathers’ in it and show me what the rhyme does in the first stanza.”

> “My line is ‘At dusk the cattle crossed the broken stile.’ Give me two endings that rhyme with *stone* and keep the ten-syllable shape.”

## Use it in Claude Code

```sh
claude plugin marketplace add OpZero-sh/plugins
claude plugin install poetry-workshop@opzero
```

Use `/poetry-workshop:read-a-poem` for a source-grounded reading or `/poetry-workshop:workshop-a-line` for revisions. Ask the **verse-editor** agent to compare alternatives when sound, meaning and rhythm pull in different directions. All three lookups are public and work without sign-in. The word or line used in a lookup goes to the corresponding hosted service.

| Connection | What it adds |
| --- | --- |
| [Classic Poetry](https://classic-poetry.mcp.opzero.sh/) | Searches by poet, title or line and retrieves the chosen poem from the PoetryDB collection. |
| [Rhyme Finder](https://rhyme-finder.mcp.opzero.sh/) | Finds sound-based rhymes and checks syllables and stress with the CMU Pronouncing Dictionary. |
| [Open Dictionary](https://open-dictionary.mcp.opzero.sh/) | Separates definitions and synonyms by sense with the Wordset dictionary, based on WordNet. |

## In use

Examples from the connected services in Claude.

![Reading William Blake’s The Tyger](media/the-tyger.webp)

- [Definitions for ephemeral](media/ephemeral.webp)
- [Rhymes for light](media/rhymes.webp)
