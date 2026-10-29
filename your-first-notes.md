# Your First Notes

**Outcome:** two notebooks, three
notes with real bodies in them, and
the habit this whole guide relies on —
after every change, read the thing
back (`transcripts t01 and t02`).

## Notebooks first

The terminal client works like a
person standing in one notebook at a
time. You make notebooks, step into
one, and notes you create land there:

```bash
joplin mkbook "Household"
joplin mkbook "Garden Club"
joplin use "Household"
joplin mknote "Weekly shopping list"
```

Most of these commands print nothing
at all. Silence is this client's
accent, not an error — the read-back
commands below are how you confirm
anything. (Chapter 13 lists the
silences worth worrying about; a
quiet success is not one of them.)

## Writing the body

A new note has a title and an empty
body. The `set` command writes any
field of a note, and `body` is the
field that matters:

```bash
joplin set "Weekly shopping list" body "Things to buy on Saturday:

- oat milk
- eggs
- coffee beans
- the good jam"
```

The body is Markdown: those `-` lines
are a list, and a blank line is a new
paragraph. Chapter 5 says more about
what Markdown inside a note can do.

Two more notes complete the lab's
set — one in each notebook:

```bash
joplin mknote "Boiler notes"
joplin set "Boiler notes" body "Serviced in spring. Filter size is 16x25x1."
joplin use "Garden Club"
joplin mknote "Spring planting plan"
```

## Reading back — and a trap, met early

```bash
joplin use "Household"
joplin ls
joplin cat "Weekly shopping list"
```

`ls` lists the notes in the notebook
you are standing in; `cat` prints a
note's title and body:

```text
Weekly shopping list

Things to buy on Saturday:

- oat milk
- eggs
- coffee beans
- the good jam
```

**Check:** if your `cat` prints your
words, your first notes exist. That
is the whole outcome of this chapter.

The trap is worth meeting here, in
transcript t01, where the lab met it:
run `cat "Weekly shopping list"`
while standing in *Garden Club* and
Joplin answers `Cannot find "Weekly
shopping list".` — title lookups are
scoped to the notebook you are in.
The note is not lost; you are looking
in the wrong room. `use` the right
notebook (or use the note's ID, which
`ls -l` shows) and it is there. On
the desktop app this never bites,
because search covers everything;
in the terminal it is the single
most common false alarm.
