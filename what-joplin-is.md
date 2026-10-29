# What Joplin Is

You have things to remember — a shopping
list, the boiler's filter size, the
rota for a club you help run — and you
want them written down somewhere that is
*yours*: readable in ten years, on a
machine you own, without asking a
company's permission. The familiar way
is a note app tied to an account: the
notes live on the company's servers,
and the app is a window onto them.

**Joplin is note-taking with the account
made optional.** It is a free,
open-source program (desktop, mobile,
and a terminal client) that keeps every
note in a **profile** on your own disk:
a folder holding a database, your
attachments, and your settings. Notes
are written in **Markdown**, the plain
text format with light markup — a line
starting with `#` is a heading, `-` is
a list — so the words themselves are
never locked inside a private format.

Sync, when you want it, is a separate
decision with a separate address. You
point Joplin at a **sync target** — a
folder, a WebDAV server, a drive you
already pay for, a Joplin Server — and
Joplin copies your notes there as
individual files, one per note, so
another machine can pick them up. And
if the target is not a place you fully
trust, **end-to-end encryption** (E2EE)
scrambles each note before it leaves,
with a key only your machines know.
Chapter 7 proves the sync with two
profiles and one folder; chapter 8 is
honest about the part the lab could
not switch on.

## A first taste

After installing (chapter 3), a note is
three lines in the terminal client:

```bash
joplin mkbook "Household"
joplin use "Household"
joplin mknote "Weekly shopping list"
```

A notebook exists, it is the one you
are standing in, and it holds a note.
Chapter 4 writes the shopping list
itself and reads it back — the receipt
every later chapter builds on.

**Check:** nothing above needed an
account, a network, or anyone's server.
That is the point of the tool, and the
guide keeps returning to it.

## What it is not

Joplin is not a word processor: notes
are Markdown text, and laying out a
polished document is another tool's
job (the Pandoc guide in this series
starts where a finished note ends).
It is not a real-time collaboration
suite — several people can share a
notebook through Joplin Server or
Joplin Cloud, but two cursors in one
note, Google-Docs style, is not what
it does. It is not, by itself, a
backup: sync faithfully copies your
mistakes and deletions to every
machine, a point chapter 7 makes —
answering it with chapter 9's export
command, which *is* the backup. And its encryption protects
notes *on the sync target* — a machine
that is already unlocked and logged in
shows its owner everything, as any
note app must.

## Who it is for

The person leaving a notes service
whose price or terms changed. The
household that wants one notebook on
the kitchen tablet and the study
computer without a family account on
someone else's cloud. The careful
note-taker whose jottings include
things — health details, door codes,
other people's business — that should
not sit readable on a rented server.
The common thread is notes that are
yours first, and shared only by a
route you picked.

## The honest catch, up front

Joplin is a volunteer-built open
source project, and it feels like one:
powerful, plain-looking, and with the
occasional rough edge this guide does
not hide — a terminal client that can
answer a command with silence, a
search index that only fills while an
app is open, an encryption switch the
lab's keychain-less machine could not
turn. Chapter 12 collects the limits.
None of them undo the core bargain:
your words, in an open format, on
your disk, syncing where you say.
