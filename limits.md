# Limits

What Joplin cannot do, or does not
do here — stated plainly, as the
series promises.

- **Sync is not a backup.** It
  propagates deletions and mistakes
  to every machine by design
  (chapter 7). The JEX export
  (chapter 9) is the backup, and
  it is your habit, not a feature
  that runs itself.
- **The master password is
  irrecoverable.** End-to-end
  encryption has no reset: lose the
  password and the synced copies are
  ciphertext for good (chapter 8).
- **Encryption guards the target,
  not the machine.** A profile on
  an unlocked, signed-in computer
  is readable by whoever sits at
  it; E2EE says nothing about the
  desk.
- **The terminal client is quiet
  and particular.** Commands
  commonly answer with silence;
  title lookups are scoped to the
  notebook you are standing in
  (chapter 4); and its search index
  only fills while an app is open,
  so one-shot sessions have nothing
  to search with (chapter 6).
- **Enabling E2EE needs a keychain
  this guide's lab did not have.**
  In the sandbox (`Keychain
  Supported: No`) the switch-on
  could not be completed from the
  terminal at all — chapter 8 has
  the evidence and the status check
  that keeps the trap visible. On
  ordinary desktops the keychain
  exists and this limit does not
  apply.
- **Sync is per-profile, not
  per-notebook.** Every profile on
  a target syncs everything on it.
  Selective sharing between people
  needs Joplin Server or Joplin
  Cloud (documented-only here).
- **Attachments multiply.** Every
  resource exists in the profile,
  on the target, on each machine
  and in each export; a photo-heavy
  notebook is heavy in five places.
- **Conflicts are copies, not
  merges.** Edit the same note on
  two machines while both are
  offline and sync keeps a conflict
  copy rather than weaving the
  texts; reconciling is by hand.
- **It is a notes app, not a
  database or a publisher.**
  Structured records, calculations
  and finished documents belong to
  other tools; Joplin's Markdown is
  the raw material, not the press.
