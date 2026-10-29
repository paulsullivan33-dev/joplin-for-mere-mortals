# Recipes

Short, complete jobs. Each uses only
machinery the earlier chapters
proved, and each ends with its own
check.

## 1. The weekly backup habit

Export a JEX to a dated file, and
keep it off the sync target:

```bash
joplin export ~/backups/joplin-$(date +%F).jex --format jex
```

Once a month, prove the latest one
(chapter 9): import it into a
scratch profile and compare the
`status` counts with your real
profile's. A backup routine with a
monthly restore is a backup; without
one it is a ritual.

## 2. A second machine, start to finish

On the new machine, install Joplin,
then point its fresh profile at your
existing target and sync *before*
writing anything:

```bash
joplin config sync.target 2
joplin config sync.2.path /path/to/your/sync-folder
joplin sync
joplin use "Household"
joplin ls
```

Your notebooks arrive complete.
**Check:** the note counts match
the old machine's `status`. If
encryption is on, the new machine
asks for the master password —
that prompt is the design working
(chapter 8).

## 3. The shared household notebook

For notes the whole household
genuinely shares — the boiler, the
bins, the wifi — keep them in one
notebook on a target every machine
points at, and keep private
notebooks' contents out of it by
habit rather than by setting:
Joplin's sync is all-or-nothing
per profile, so a shared *target*
means shared *everything* on it.
For selective sharing between
people, Joplin Server or Joplin
Cloud sharing (documented-only
here) is the tool shaped for it.

## 4. Leaving another note app

Export from the old app in the most
open format it offers — Markdown if
it can, HTML if it cannot. Import a
small sample first:

```bash
joplin --profile scratch import ~/old-notes-sample
joplin --profile scratch ls -r
```

Read three notes against their
originals. Formatting that survives
a sample survives the bulk; what
the sample mangles, fix in the
export settings, not by hand in ten
thousand notes.

## 5. The pre-travel freeze

Before a trip with an untrusted
network in it: sync at home, export
a JEX to a drive that stays home,
and confirm `e2ee status` if you
rely on encryption. Three minutes,
and the worst case abroad is a lost
device, not lost notes.
