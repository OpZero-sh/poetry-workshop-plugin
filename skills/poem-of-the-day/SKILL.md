---
name: poem-of-the-day
description: "Bring up one classic poem for today or for any date, optionally by a chosen poet and within a length limit, and offer a short way in. Use when someone says give me a poem for today, poem of the day, read me a poem, a short poem by Dickinson, a poem for my birthday date, something to read this morning, or asks which poets are in the library."
---

# Poem of the day

Fetch the day's poem from the Classic Poetry server, present it cleanly, and offer one thing to notice.

## When to use

- "A poem for today." "Read me something short." "A Dickinson poem for this morning."
- "What was the poem for 1 March?" "Give me the poem for my birthday."
- "Which poets can you pull from?"

For a specific poem or a remembered line use `read-a-poem`. That skill also covers a full close reading.

## Tools

Both are on the Classic Poetry server, read only, with no sign in.

| Tool | Arguments | Notes |
| --- | --- | --- |
| `poem_for_today` | `date` (YYYY-MM-DD, optional), `poet` (optional), `max_lines` (4 to 200, default 40) | One poem per date, the same all day |
| `list_poets` | `name` (part of a name, optional) | The poets in the library, 129 at last check |

## Workflow

1. **Call `poem_for_today`.**
   - No preferences: call with no arguments.
   - A named poet: pass `poet`. Part of the name works.
   - "Short": pass `max_lines`, for example 16. "Long" or "substantial": raise it, up to 200.
   - A particular date: pass `date` as YYYY-MM-DD. When the reader's local date may differ from the server's, or two people want the same poem, pass the date explicitly instead of relying on the default.
2. **Present the poem as returned:** title, poet, then the text with its line and stanza breaks intact. Do not trim, modernise or summarise it in place of the text.
3. **Add a short way in.** Two or three sentences at most: one thing to listen for or one question, tied to a word or line. Do not explain the whole poem unless asked.
4. **Offer one next step:** a closer reading (`read-a-poem`), another poem by the same poet, or the same date's poem from a different poet.

## How the pick behaves

- The poem is fixed by the date. Asking again on the same date with the same arguments returns the same poem. For a different one, change the `poet`, the `max_lines` cap or the `date`, and tell the reader that is what you did.
- Without `poet`, the day has a poet attached. If that poet has nothing within `max_lines`, the tool answers "No poems by <poet> within <n> lines." It does not fall back to another poet. Raise `max_lines`, or pass a `poet` who writes short poems.
- The date only selects which poem comes up. Nothing in the result says the poem was matched to a season, holiday or anniversary, so do not claim it suits the occasion. If the reader wants a poem about a subject, use `read-a-poem` and search by title or line words.
- Future and past dates both work.

## Errors and edge cases

- **"No poems by <poet> within <n> lines":** raise `max_lines` or choose another poet, and say which you did.
- **"No poet named <name> in the library. Try list_poets":** call `list_poets` with part of the surname. Offer the closest match or say the poet is not included. The library is classic public domain verse, so living and most twentieth century poets are absent.
- **The reader asks for a poem by someone not in the library:** say so. Do not write out one of that poet's poems from memory.
- **The reader wants a different poem "for today":** explain that the date's pick is fixed, then vary the poet or length.
- **Tool failure:** say so and retry once. Do not substitute a poem from memory and present it as the day's pick.

## What the answer should look like

The title and poet on their own lines, the poem in a quotation block, then the short way in and the offer. Keep commentary shorter than the poem.

## Limits to state honestly

The texts are older public domain transcriptions from PoetryDB and may differ in punctuation or wording from modern editions. The plugin is not affiliated with PoetryDB. The service keeps no reading history, so it cannot avoid repeats across days on its own or remember what the reader liked.

## Examples

**"Give me a poem for today."**
Call `poem_for_today` with no arguments. Show the poem. Add one thing to notice and offer a closer reading.

**"Something short by Emily Dickinson."**
Call `poem_for_today` with `poet: "Emily Dickinson"` and `max_lines: 12`. Show it.

**"A poem for today, under 14 lines."** The tool answers that the day's poet has nothing within 14 lines.
Tell the reader, then either call again with a larger cap or ask for a poet they like and pass `poet` with `max_lines: 14`.
