# Writing criteria for this guide

Every "for Mere Mortals" guide is written to the same nine-point
standard, so a reader who trusts one can trust the rest. Here it
is, with the verification notes for this particular guide below.

1. **Fix it first.** Reader outcomes lead, not action items: each
   chapter opens by naming the outcome it delivers, shows a check
   the reader can run to confirm they got it, and a reasonable
   reader finishes able to state what was done, what it means,
   and what to try next.
2. **Plain language.** Short sentences, everyday vocabulary,
   technical terms defined on first use. No slang, and no
   idioms that only make sense in one country — the reader may
   be translating as they go.
3. **No dead ends.** A guide never tells the reader to do
   something it cannot show them how to verify. Every claim a
   reader relies on — an install, a command, an output — is
   something this guide demonstrates or clearly labels
   documented-only below.
4. **Live-verified where it matters.** Procedures are run for
   real in the guide's lab wherever the build machine allows it,
   and the transcripts kept in the repository are the evidence.
   What could not be run is listed honestly below, never
   presented as if it had been.
5. **General audiences.** Nothing in this guide — examples,
   fixtures, names, addresses — is modelled on any particular
   reader or author's real life, network, or organisations.
   The lab's notes are a shopping list, a boiler note, and an
   invented garden club.
6. **Standalone.** A reader needs this guide, its lab, and
   nothing else. Where another guide would genuinely help, it
   is pointed to once, by name, and the chapter still completes
   without it.
7. **Honest about limits.** Chapter 12 names what the tool
   cannot do: sync that propagates deletions and is not a
   backup, an irrecoverable master password, encryption that
   guards the target and not the desk, per-profile rather than
   per-notebook sync, conflict copies instead of merges, and
   the terminal client's silences and scoped lookups.
8. **The ethics rule is in the text, early.** Joplin's line is
   drawn in chapter 1 and the README: your notes stay on your
   machines and travel only by a route you chose — and where
   the tool offers end-to-end encryption for notes that are
   not the sync provider's business, chapter 8 states both
   how it protects them and the condition (a lost master
   password is final) that makes it a serious promise rather
   than a feature tick.
9. **Builds clean.** The site builds with MkDocs in strict mode
   with no warnings, and a fresh reader following the chapters
   in order reaches the stated outcome of each.

## Verification notes for this guide

The build machine is a shared Ubuntu 24.04 sandbox. Joplin
**3.7.1**, the official terminal client, was installed from
its npm package and run unmodified, always against profiles
inside the lab folder (`--profile`), never a real user's
profile. All transcripts live in `joplin-lab/transcripts/`
(t00–t09a).

Run for real, with transcripts as evidence:

- Version and status on a fresh profile: version 3.7.1,
  Sync Version 3, Profile Version 53, `Keychain Supported:
  No`, `Sync target: (None)`; the empty status report as
  baseline (t00).
- Notebooks and notes: two notebooks created, three notes
  given bodies with `set ... body` and read back word for
  word with `cat` (t01, t02) — including the genuine trap in
  t01: `cat` by title answers `Cannot find` when the current
  notebook is a different one.
- Attachments: an 87-byte text file attached; the note
  gained its `resources/<id>.txt` Markdown link and the file
  appeared in the profile's `resources/` folder (t03).
- Tags: three tags assigned; `tag list`, per-tag notes and
  per-note tags all read back in agreement (t03).
- The search machinery, inspected rather than assumed: the
  profile database holds `notes_fts`/`items_fts` tables with
  **zero rows** after a session of one-shot commands, so a
  MATCH query for a word certainly in a note returns
  nothing (t04); the client's built-in API server answered
  `/ping`, listed all notes at `/notes`, and returned the
  same empty result at `/search` for the same reason (t05).
  The index fills while an app is open; the guide says so.
- Export and import: a JEX export listed with `tar` (one
  ID-named Markdown file per item); a Markdown export read
  back as a folder tree with `_resources/`; the JEX
  imported into a fresh profile restored 3 notes, 2
  folders, 1 resource, 3 tags and 3 note-tag links by
  `status` count (t06).
- Filesystem sync, both directions: profile A synced 12
  items up to a plain folder (an item file inspected in
  full; the note's words are plain text on the target);
  an empty profile B synced the same 12 down and read the
  shopping list word for word; a note written on B
  travelled back to A (t07, t08).

Attempted in good faith, and reported as failed here rather
than dressed up:

- **End-to-end encryption could not be enabled in this
  sandbox.** Three routes were tried — the `e2ee enable`
  password flag, the password piped on stdin, and a pty
  driver answering both prompts, which exited with status
  0 (t09a) — and after each, `e2ee status` still reported
  `Encryption is: Disabled` and no master key persisted.
  The environment's standing fact is `Keychain Supported:
  No` (t00), and the profile then synced in plain text,
  code word and all (t09). The enabled state — ciphertext
  on a target, a second machine unlocking — is therefore
  documented-only in chapter 8, from the project's
  documentation, and the guide teaches `e2ee status` as the
  check precisely because this attempt showed why it
  matters.

Documented only — described from the project's
documentation, not run, and the text does not claim
otherwise:

- The desktop and mobile apps: installation, editing and
  reading experience, the settings screens, the web
  clipper in a browser.
- E2EE in its working state (see above), including the
  second-device unlock prompt.
- Sync targets other than the filesystem: WebDAV and
  Nextcloud, Joplin Server, Joplin Cloud, OneDrive,
  Dropbox and S3 — plus notebook sharing and published
  notes, which need the server targets.
- Search in its working state in the apps (the query
  refinements — phrases, `tag:`, `notebook:` — are the
  documented syntax), note history and revisions browsing,
  and plugins.

Fixtures are this guide's own and deliberately generic: a
weekly shopping list, a boiler note, an invented garden
club, and a planted code word (`VELVET LEDGER 42`) that is
an example, not a secret, and is printed in the guide as
such. Every password used in the lab was a throwaway for a
disposable profile, and the lab's sync folders, profiles
and exports were deleted after the transcripts were kept.
