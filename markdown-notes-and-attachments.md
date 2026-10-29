# Markdown Notes and Attachments

**Outcome:** a note whose body uses
real Markdown structure, and a file
attached to a note — stored by
Joplin, linked from the note, and
visible in the profile where chapter
2 said it would be (`transcript
t03`).

## What Markdown gives a note

A Joplin note's body is Markdown end
to end. The small set that covers
most notes:

```markdown
# A heading
## A smaller heading

A paragraph of ordinary text, with
**bold** and *italic* in it.

- a list
- of things

1. a numbered list
2. in order

- [ ] an unticked to-do box
- [x] a ticked one
```

Headings divide long notes; the
checkbox lines make a note behave
like a checklist in the apps. The
Markdown guide in this series covers
the format itself — flavours, traps
and all — and this chapter only
needs you to know that what you type
is the document: there is no hidden
rich-text layer to fall out of sync
with the words.

Because notes are text, the terminal
client's `set ... body` (chapter 4)
and the desktop editor are two doors
into the same room — text written by
one reads perfectly in the other,
which the sync chapter relies on.

## Attaching a file

An **attachment** is a file Joplin
keeps for a note: a photo, a PDF, a
text file. In the terminal client:

```bash
joplin use "Garden Club"
joplin attach "Spring planting plan" ~/seed-order.txt
```

Read the note back and the attachment
is already part of it:

```text
[seed-order.txt](resources/dc353d7e45a1407a96316cff78f3c3d6.txt)
```

Three things happened, all checkable:

1. The file was **copied** into the
   profile's `resources/` folder,
   renamed to a long ID with the same
   extension. Your original stays
   where it was; Joplin keeps its own.
2. A Markdown **link** to that copy
   was placed at the top of the note.
   In the apps, the link renders as
   the picture or file itself; in
   plain text, it is this honest
   address.
3. The note now depends on the
   resource item — delete either with
   care. Sync and export carry both
   (chapters 7 and 9 count the
   resource among the items).

**Check:** `ls` your profile's
`resources/` folder. One file per
attachment, size matching the
original. Transcript t03 shows the
lab's 87-byte seed order in place.

## The size question

Every attachment lives in every copy
of your notes: the profile, the sync
target, each machine, each export.
A photo habit adds up quietly. This
is not a warning against attaching —
it is the arithmetic to keep in mind
before the profile is measured in
gigabytes, and chapter 12 returns
to it.
