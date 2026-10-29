# Sync Targets and How Sync Works

**Outcome:** two separate Joplin
profiles — two pretend machines —
sharing one folder, with notes
proven to travel up, arrive on the
empty machine, and travel back
(`transcripts t07 and t08`). This
is the chapter the whole guide was
building towards.

## The idea, in one paragraph

Sync is copying, in both directions,
until two places agree. A profile
holds your notes; a **sync target**
holds copies of the same items as
individual files. Any profile pointed
at the same target converges on the
same notebooks. Nothing about the
target is clever — the lab's target
is a plain folder — and that is the
strength of it: you can look inside.

## Setting up the folder target

In the terminal client, the target
is two settings:

```bash
joplin config sync.target 2
joplin config sync.2.path /path/to/your/sync-folder
joplin sync
```

The numbers are Joplin's own list —
`config sync.target` reads it back
(transcript t07): 2 is the file
system, 6 WebDAV, 9 Joplin Server,
10 Joplin Cloud, and others. The
folder can be anything both machines
can reach: a directory on the same
computer for a first test, a folder
inside a synced drive, a share on a
home server.

The first sync reports its work:

```text
Created remote items: 12.
```

Twelve is chapter 2's arithmetic
made visible: 3 notes, 2 notebooks,
3 tags, 3 note-tag links, 1 attached
resource. Inside the target folder,
each is one file named by its ID.
The shopping list's file begins with
the note itself — title, body — and
ends with its facts:

```text
Weekly shopping list

Things to buy on Saturday:
- oat milk
...

id: d383faa76a0a4777a72a08aee5cfd51e
parent_id: dcd126a15129410b8dbc00727ba4d83b
```

**Check:** `grep -r "oat milk"` in
the target finds your note, in plain
text. Hold that fact; chapter 8 is
about when it should *not* be
findable, and what changes it.

## The second machine

Now the proof. A brand-new, empty
profile — never seen a note — is
pointed at the same folder:

```bash
joplin --profile profile-b config sync.target 2
joplin --profile profile-b config sync.2.path /path/to/your/sync-folder
joplin --profile profile-b sync
```

```text
Created local items: 12.
```

And the empty machine is empty no
longer: `use "Household"`, `ls`,
and `cat "Weekly shopping list"`
print the list, word for word, on a
profile that an hour earlier held
nothing (transcript t08).

The round trip closes the loop: a
note written on profile B, synced,
appears on profile A after A's next
sync. Neither profile is the
"master". The folder is the meeting
place; the profiles are equals.

## The other targets

The lab ran the filesystem target
because it needs no server and no
account, and because you can inspect
it with ordinary tools. The others
differ in transport, not in what
sync means:

- **WebDAV / Nextcloud** — the same
  item files, in a folder on a
  WebDAV server: yours, if you run
  one (a Nextcloud is the common
  case). The natural self-hosted
  step up from a folder.
- **Joplin Server** — the project's
  own server software: sync, plus
  notebook sharing between users
  and published notes.
- **Joplin Cloud** — the paid,
  hosted version of that server, run
  by the project; the one target
  where someone else holds the disk.
- **OneDrive, Dropbox, S3** — item
  files in a corner of a general
  cloud drive.

Those five are documented-only in
this guide; the mechanics you
proved against the folder — items,
both directions, no master — are
the same mechanics they run.

## Sync is not a backup

Say it plainly, because the design
invites the mistake: sync copies
*changes*, including deletions and
mistakes, to every machine, quickly
and correctly. A notebook deleted at
breakfast is deleted everywhere by
lunch. The target folder is a
meeting place, not an archive. The
backup is chapter 9's export —
a file you keep somewhere sync
cannot reach.
