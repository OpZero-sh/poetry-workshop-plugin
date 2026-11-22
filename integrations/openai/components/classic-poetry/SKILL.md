---
name: use-classic-poetry
description: "Find classic poems by title, poet or remembered wording, read the matching work, or bring up a poem for the day."
---

Use this connection for classic public domain poetry in English.

1. To find a poem, call search_poems with line for remembered words, or with poet and title. Fields combine and accept part of a name. Each result shows title, poet, line count and the poem's first line, which is not always the line that matched.
2. To read it, call get_poem with the exact title from the result and always pass author. A shared title with no author returns one poem without warning.
3. For a poem for today or for a date, call poem_for_today. Optional arguments are date as YYYY-MM-DD, poet, and max_lines. If it answers that the day's poet has nothing within the line limit, raise max_lines or name a poet.
4. To see who is included, call list_poets, optionally with part of a name.

Quote the text exactly as returned and keep its line breaks. Give title and poet. Keep your reading of the poem apart from its words, and tie each point to a quoted line.

The library is a fixed set of older poets drawn from PoetryDB. Most twentieth century and all contemporary poets are absent. When a poem is not found, say so and do not reproduce it from memory. Texts are older transcriptions and can differ from modern editions.
