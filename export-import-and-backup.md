# Export, Import and the Real Backup

**Outcome:** two kinds of export on
disk, opened and inspected, and the
backup *proven* by importing it into
an empty profile and counting what
came back (`transcript t06`).

## The JEX export: the backup

```bash
joplin export ~/backups/joplin-backup.jex --format jex
```

A **JEX** file is Joplin's complete
export: every notebook, note, tag
and resource. The lab opened it —
it is an ordinary tar archive, and
inside, every item is one Markdown
file named by its ID, exactly the
shape chapter 7 met on the sync
target:

```text
$ tar -tf joplin-backup.jex
004a909db62c4df29a33dbca8acdf688.md
010c4167691649a297fed5dbae2810e7.md
...
```

An archive you can list with
decades-old tools is an archive you
can rescue with them. Keep the JEX
somewhere sync cannot reach — an
external drive, an occasional copy
to another machine by hand — on
whatever rhythm your notes deserve.

## Proving it: import into nothing

A backup you have never restored is
a hope, not a backup. The lab
imported the JEX into a fresh,
empty profile:

```bash
joplin --profile profile-c import ~/backups/joplin-backup.jex
joplin --profile profile-c status
```

```text
Note: 0/3
Folder: 0/2
Resource: 0/1
Tag: 0/3
NoteTag: 0/3
```

Three notes, two notebooks, the
attachment, the tags — the whole
set, back from one file. (The 0/ is
the sync column: restored items
have not been synced anywhere, and
do not need to have been.) Do this
once with your own export, on a
scratch profile, before you trust
the routine.

## The Markdown export: the readable copy

```bash
joplin export ~/backups/joplin-md --format md
```

This is the export for *reading*
rather than restoring — a folder
per notebook, a `.md` file per
note under its real title, and
attachments in a `_resources`
folder:

```text
Garden Club/Spring planting plan.md
Household/Boiler notes.md
Household/Weekly shopping list.md
_resources/seed-order.txt
```

Open the shopping list in any text
editor and it is simply the note.
This is the format for leaving
Joplin, for handing notes to
someone else, or for the drawer
copy you can read with no Joplin
anywhere in sight. The trade: tags
and some internal facts do not
survive the trip as structure —
the JEX is the backup, this is the
reading copy. Make both; they
answer different emergencies.

## Import, generally

`joplin import` also takes Markdown
files and folders — the way in for
notes kept as loose text, and for
the exports of several other note
apps, whose formats the importer
understands in the desktop app.
Imported items land as new notes
with new IDs; importing is a birth,
not a reunion, which is why the
import check above counts items
rather than comparing IDs.
