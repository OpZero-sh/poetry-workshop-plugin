# Library notes

How the Classic Poetry server behaves, from live calls in November 2026.

## What the library holds

- Classic public domain poetry in English, drawn from the PoetryDB collection.
- `list_poets` reported 129 poets. They run from Chaucer to poets of the early twentieth century such as Wilfred Owen and Rupert Brooke.
- Modernist and later poets are not included. A request for a twentieth century poem in copyright will not be found.
- The set of poets is fixed by the source. The server does not take submissions and has no search across the wider web.

## Poet names

`list_poets` returns names as stored. Pass part of a name in `name` to filter. Some stored forms are not the ones a reader would type:

| A reader says | Stored as |
| --- | --- |
| Byron, Lord Byron | George Gordon, Lord Byron |
| Tennyson, Alfred Tennyson | Lord Alfred Tennyson |
| Coleridge, Samuel Taylor Coleridge | Samuel Coleridge |
| Leigh Hunt | James Henry Leigh Hunt |
| The Brontë sisters | Anne Bronte, Charlotte Bronte, Emily Bronte (no diaeresis) |

One entry is stored as a surname only (Robinson). When a lookup by full name fails, filter `list_poets` by surname.

`search_poems` and `poem_for_today` accept part of a poet's name: `Keats` finds John Keats. `get_poem` also accepted a surname in `author`.

## Search behaviour

- `title` matches words inside titles. A search for `Song` returned 118 poems, including titles such as "A Song of Autumn".
- `line` matches words that appear in a line of the poem.
- `poet`, `title` and `line` combine: all given fields must match.
- A result entry shows title, poet, line count and the poem's first line. The first line is shown even when a later line matched.
- The first sentence of the result gives the total, such as "118 poems match Song, first 20 shown." The most a call returns is 20. There is no next page, so narrow the search to see the rest.
- No match reads "No poems match <terms>."
- There is no search by theme, form, date or mood. To find "a poem about autumn", search likely title words or line words and read what comes back.

## Fetching a poem

- `get_poem` needs the title as stored. Capitalisation did not matter in testing.
- When several poets have a poem with the same title and no `author` is given, one poem comes back with no notice. Always pass `author`.
- When one poet has two poems with the same title, only one can be fetched.
- The result is the title, a "by" line and the full text with stanza breaks. There are no line numbers, dates, notes or source edition.
- Some poems are very long. Search results have shown poems of 400 and 600 lines. Check the line count first.
- A title that is not found reads "No poem titled <title> in the library."

## Text quirks

The texts are transcriptions of older printed editions. Expect:

- Underscores around a word to mark italics.
- Two hyphens in a row standing for a dash.
- Opening words in capitals, and first lines used as titles for untitled poems.
- Old spellings and contractions, sometimes with a space inside the contraction.
- Section numerals or headings that appear as lines of a long poem.
- Editorial choices of the source edition. Early editions of some poets regularised punctuation and changed words, so a text here can differ from a modern scholarly edition.

When quoting, keep the text as returned. It is fine to render underscores as italics. Do not silently modernise spelling or punctuation.

## Quoting and credit

- The poems are in the public domain, so quoting them in full is acceptable. Length should still fit the question.
- Give title and poet with every quotation.
- Name the source once per answer when it is useful: the Classic Poetry service, with texts from PoetryDB. This plugin is not affiliated with PoetryDB.
- The server's description says requests are not stored.
