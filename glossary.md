# Glossary

**Attachment** — see *resource*.

**E2EE** — end-to-end encryption:
items are encrypted on your machine
before sync and decrypted only on
your other machines, so the sync
target holds ciphertext (chapter 8).

**Item** — the unit Joplin's
machinery moves: a notebook, note,
tag, note-tag link, resource or
revision, each with its own ID.
Sync counts and exports are counted
in items.

**JEX** — the Joplin Export File:
one tar archive holding every item,
the complete backup format
(chapter 9).

**Master key** — the keypair made
when encryption is enabled; items
are encrypted to it, and it is
itself protected by the master
password.

**Master password** — the password
you choose when enabling E2EE. It
unlocks the master key on each new
machine, never travels, and cannot
be recovered if lost.

**Notebook** — a folder for notes;
notebooks nest. The terminal client
always stands in one notebook at a
time, and title lookups are scoped
to it.

**Note** — one Markdown document:
a title, a body, and its facts. A
note can also be a to-do, with a
checkbox state and an alarm.

**Profile** — the folder holding
one user's whole Joplin life on one
machine: `database.sqlite`,
`resources/`, `settings.json`,
`log.txt`.

**Resource** — an attached file,
stored in the profile's `resources/`
folder under an ID name and linked
from its note.

**Sync target** — the place profiles
meet: a folder, a WebDAV server,
Joplin Server, a cloud drive. It
holds one small file per item, plus
an `info.json`; it is a meeting
place, not a backup.

**Tag** — a label that crosses
notebooks; a note can carry many,
and a tag carries no settings.

**Web clipper** — the browser
extension that saves web pages as
notes, through the local API server
(`joplin server start`) the lab
exercised in chapter 6.
