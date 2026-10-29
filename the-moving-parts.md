# The Moving Parts

This chapter names the pieces before
any procedure depends on them. When a
later chapter says "the note is on the
target but not on the phone", you will
be able to say *which* piece is being
talked about — and that is most of
troubleshooting, done in advance.

**Check:** by the end you can point at
a Joplin profile folder and say what
each thing in it is for. The lab's
profile listing is in transcript t00
onwards; the folder itself is small
enough to walk through in one screen.

## The profile: where you actually live

Everything Joplin knows about you is
in one folder, the **profile**. The
terminal client makes one per user by
default; the lab used the `--profile`
flag to keep several pretend machines
side by side:

```bash
joplin --profile ~/joplin-lab/profile-a status
```

Inside a profile you will find:

- **`database.sqlite`** — the local
  database. Every notebook, note, tag
  and setting is a row in it. This —
  not the sync target — is the copy
  Joplin works from day to day.
- **`resources/`** — your attachments,
  one file each, renamed to a long
  hexadecimal ID with the original
  extension (`dc353d….txt`). The
  database remembers the real name.
- **`settings.json`** — the profile's
  configuration as plain JSON: sync
  target choice, its path, the API
  token. Readable, and worth reading
  once (chapter 7).
- **`log.txt`** — the running log; the
  first place chapter 13 sends you.

## Notebooks, notes, tags

A **notebook** is a folder for notes;
notebooks can nest inside notebooks.
A **note** is one Markdown document:
a title, a body, and a set of facts
about itself (when it was made, which
notebook holds it, whether it is a
to-do). Notes are the unit of
everything — of sync, of export, of
encryption.

A **tag** is a label that crosses
notebook boundaries: `shopping` can
mark a note in Household and a note in
Garden Club at once. A note can carry
many tags; a tag is just a name, with
no settings of its own. Chapter 6
assigns and reads back real tags.

**Resources** are the files you attach
— a photo of a meter reading, a PDF of
a manual. Inside the note, an
attachment appears as an ordinary
Markdown link to its ID name; Joplin
renders it as the file itself.

## Items: the unit the machinery sees

Underneath, notebooks, notes, tags,
note-to-tag links, attachments and old
versions are all **items**, each with a
32-character ID. This matters because
sync and export move items, not
"notebooks" in the abstract: when
chapter 7's sync reports "Created
remote items: 12", it is counting
exactly these — 3 notes, 2 notebooks,
3 tags, 3 tag links, 1 resource.

## The sync target

A **sync target** is a place Joplin
copies items to, and from. On the
target, each item is one small file
named by its ID, containing the
note's text followed by its facts
(transcript t07 shows one in full).
A tiny `info.json` describes the
target's format version. Filesystem,
WebDAV, Joplin Server and the cloud
drives differ in *where the folder
lives*, not in what lands in it.

Two profiles pointing at one target
is the whole trick of chapter 7: the
target is a meeting place, never a
home. Either profile can be deleted
and rebuilt from it — which the lab
does, in effect, by starting the
second profile empty.

## The master key (when encryption is on)

With **end-to-end encryption** enabled,
one more piece exists: a **master
key**, a keypair made on the first
machine and protected by a **master
password** only you know. Items are
encrypted with it before upload and
decrypted after download; the target
holds ciphertext. Chapter 8 explains
the model and reports the lab's
attempt to switch it on — the one
procedure in this guide that the
sandbox could not complete.
