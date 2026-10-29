# End-to-End Encryption

**Outcome:** you understand exactly
what Joplin's encryption protects,
what it needs from you, and what an
unencrypted target exposes — the
last of those *proven*, the rest
labelled documented-only, for a
reason this chapter states in the
open (`transcript t09`).

## The problem it solves

Chapter 7 ended on a fact worth
sitting with: on an ordinary sync
target, your notes are **readable
text files**. Anyone or anything
that can read the target folder —
a borrowed drive, a breached
account, a curious admin — can read
every word, attachments included.
For a shopping list that is nothing.
For the notebook with the door
codes, the health letters, the club's
membership list, it is the whole
ballgame.

**End-to-end encryption** (E2EE)
changes what leaves the machine.
Before upload, each item is
encrypted with a **master key**;
the target stores ciphertext —
files whose bodies are scrambled
blocks, titles included. Download
reverses it, but only on a machine
that knows the **master password**
you chose when you switched
encryption on. The password itself
never travels; new machines prove
themselves by being given it.

## What the lab could and could not do

The lab set out to prove this the
same way it proved sync: enable
encryption on a fresh profile, sync,
and grep the target for a code word
planted in a note. The word was
invented for the purpose — `VELVET
LEDGER 42`, in a note called
"Example safe code".

It did not work, and the failure is
instructive enough to print. Three
routes were tried (transcript t09a
holds the terminal session): the
command's own password flag, the
password piped in, and a driver
answering both prompts — *Enter
master password*, *Confirm
password* — exactly as a person
would. The command accepted the
answers and exited without error.
And afterwards:

```text
$ joplin e2ee status
Encryption is: Disabled
```

The setting never persisted, and the
profile then synced **in plain
text** — `grep` finds `VELVET
LEDGER 42` on the target in full.
The one environmental fact that
explains the shape of the failure
was there from the first transcript:
this sandbox reports **Keychain
Supported: No**. Joplin keeps the
master password in the system
keychain; with nowhere to keep it,
the terminal client in this
environment could not complete the
switch-on. On a normal desktop —
keychain present — enabling E2EE is
a settings-screen checkbox and a
password, done once.

So, honestly divided:

- **Verified live:** the unencrypted
  state and its exposure (above);
  the `e2ee` command surface,
  prompts and status reporting; and
  the trap this creates — a sync
  that *looks* set up can be plain
  text if encryption never actually
  engaged. `e2ee status` is the
  check; run it after enabling,
  always.
- **Documented-only:** the enabled
  state itself — ciphertext on a
  real target, and a second machine
  unlocking with the master password
  and reading the note. Described
  from the project's documentation;
  this guide does not present them
  as run.

## The rules that follow from the model

Documented, and worth learning
before you need them:

- **The master password is final.**
  There is no reset and no recovery:
  lose it, and the synced copies are
  ciphertext forever. (Your local,
  already-decrypted profile still
  works — export from it, chapter
  10, and start again.)
- **Enable it before you sync
  anything sensitive**, and re-check
  with `e2ee status` — see the trap
  above.
- **Every new machine needs the
  password once.** That prompt, on a
  phone or laptop you have just
  pointed at your target, is the
  system working as designed, not an
  error.
- **Encryption covers the target,
  not the desk.** A machine signed
  in and unlocked shows its notes to
  whoever is sitting at it. E2EE is
  about the copy in transit and at
  rest elsewhere — chapter 12 keeps
  the boundary straight.
