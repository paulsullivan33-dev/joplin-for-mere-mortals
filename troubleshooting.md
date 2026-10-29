# Troubleshooting

Each entry: the symptom as you meet
it, the cause this guide's lab can
stand behind, and the check that
separates it from its lookalikes.

## "Cannot find" a note that exists

You `cat` a note by title and get
`Cannot find "..."` — while the note
is plainly in the app. **Cause:**
title lookups are scoped to the
notebook you are standing in
(chapter 4, transcript t01).
**Check:** `use` the right notebook,
or find the note's ID with `ls -l`
and use that. Not lost; wrong room.

## A command printed nothing

`mkbook`, `mknote`, `set`, `config`
and friends report success with
silence in the terminal client.
**Check:** read the thing back —
`ls`, `cat`, `config <name>`. Treat
every silent command as unfinished
until its read-back agrees.

## Notes are not travelling

One machine writes; the other does
not receive. Work the chain:

1. `joplin config sync.target` and
   `config sync.2.path` on **both**
   profiles — a target set on one
   machine is set on one machine.
2. Same path, same folder, spelled
   the same way, reachable by both.
3. `joplin sync` on the writer,
   then on the reader; a one-way
   demonstration is in transcript
   t08 if you need the shape.
4. `joplin status` on both: item
   totals should converge. If the
   writer's sync reports errors, the
   profile's `log.txt` names them.

## The sync target can be read by anyone

You grepped the target folder and
found your notes in plain text —
possibly after "turning encryption
on". **Cause:** encryption is not
engaged, whatever the setup felt
like (chapter 8's trap).
**Check:** `joplin e2ee status`.
Anything but "Enabled" means the
target holds text. Fix the enabling
first; re-sync after.

## Search finds nothing

Results are empty for words you can
see in notes. **Cause:** the search
index fills only while a Joplin app
is open (chapter 6, transcripts t04
and t05); a profile driven by
one-shot commands has an empty
index. **Check:** open the profile
in the desktop app or the terminal
client's interactive screen, give
it a moment, and search again.

## The second machine asks for a password

After its first sync with an
encrypted target, a new machine
cannot read its notes. That prompt
**is** the system working: enter
the master password once (chapter
9). If nobody knows it, the synced
copies cannot be opened — by
design. Work from a machine whose
profile is already decrypted and
export from there.

## Changed the sync folder and notes vanished

You repointed `sync.2.path` at an
empty folder and synced; Joplin
treated the empty target as the
truth and removed local items to
match. The setting's own help text
warns about exactly this. **Rule:**
when moving a target, copy the old
target's contents to the new
location *first*, then change the
setting, then sync.
