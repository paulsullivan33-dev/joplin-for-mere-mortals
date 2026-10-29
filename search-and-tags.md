# Search and Tags

**Outcome:** tags assigned and read
back three ways, and an honest map
of how search works — including what
the lab found when it looked inside
the search index (`transcripts t03,
t04 and t05`).

## Tags: the cross-notebook filing

Tags are assigned per note:

```bash
joplin tag add shopping "Weekly shopping list"
joplin tag add errands "Weekly shopping list"
joplin tag add home "Boiler notes"
```

And read back per tag or per note:

```bash
joplin tag list              # every tag
joplin tag list shopping     # notes carrying it
joplin tag notetags "Weekly shopping list"
```

```text
$ joplin tag list shopping
	Weekly shopping list
$ joplin tag notetags "Weekly shopping list"
errands
shopping
```

**Check:** a note with two tags
answers to both, and the tag list
and the note's own list agree. Tags
are items too (chapter 2): they sync
and export with everything else, as
chapter 7's item count shows.

One habit to build early: tag by
*errand or project*, not by topic
alone. `shopping`, `to-ask-the-club`,
`tax-2026` — tags earn their keep
when they answer "what needs me",
across every notebook at once.

## Search: an index, kept by the app

Joplin's search is a full-text index
inside the profile database — SQLite
tables named `notes_fts` and friends,
in the same `database.sqlite` as
everything else. Searching in the
apps asks that index, which is why
it is instant and why it finds words
in the middle of notes.

The lab opened the database
read-only and looked (transcript
t04). The tables exist. After a
whole session of one-shot terminal
commands — notes made, tagged, even
synced — the index held **zero
rows**, and a query for a word that
is certainly in a note (`jam`, from
the shopping list) found nothing:

```text
notes_fts rows: 0
search 'jam' -> []
```

The same answer came through
Joplin's own local API. The lab ran
the client's built-in server
(`joplin server start` — the local
API the web clipper talks to) and
asked it directly (transcript t05):

```text
$ curl ".../search?query=jam"
{"items":[],"has_more":false}
$ curl ".../notes?fields=title"
{"items":[{"title":"Weekly shopping list"}, ...]}
```

The notes are there; the *index* is
empty. The reason is plain once
stated: the index is filled by a
background service **while a Joplin
app is open** — the desktop app on
your desk, the terminal client in
its interactive screen. One-shot
commands start, act, and exit before
that service does its round.

So the honest division of this
chapter: in daily use — an app open
while you work — search simply
works, over titles and bodies, with
the usual refinements (words are
matched as prefixes, phrases in
quotes, `tag:shopping` and
`notebook:"Garden Club"` narrow the
field; those refinements are
documented-only here). What this
lab *proved* is the machinery
underneath and its one sharp edge:
a profile touched only by one-shot
commands has nothing to search with
yet. If a script of yours ever
reports "no results" for a note you
can see, this empty index — not a
lost note — is the first suspect.
