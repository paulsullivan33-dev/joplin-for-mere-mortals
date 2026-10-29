# Installing Joplin

**Outcome:** a working `joplin`
command that reports its version and
shows an empty, healthy profile.
Every install in this guide is the
**terminal client** — the desktop and
mobile apps are described in chapter
12's terms (documented-only here),
and everything the terminal client
does uses the same profiles, formats
and sync targets they do.

## The terminal client, from npm

Joplin's terminal client is published
as an npm package, so you need
**Node.js** first — any current LTS
release. Then:

```bash
npm install -g joplin
joplin version
```

The lab installed it into a folder of
its own instead of globally, which is
the same package run from a different
address:

```bash
mkdir joplin-cli && cd joplin-cli
npm install joplin
./node_modules/.bin/joplin version
```

Either way, the receipt is the same
(transcript t00):

```text
Joplin CLI Client
joplin 3.7.1 (prod, linux)
Sync Version: 3
Profile Version: 53
Keychain Supported: No
Sync target: (None)
```

Read that block slowly; it is a
checklist. The version tells you whose
documentation applies. **Keychain
Supported** says whether this machine
can store secrets for Joplin — "No"
on the lab machine, a fact chapter 8
meets again. **Sync target: (None)**
is the honest starting state: nothing
leaves this machine until you say so.

Two practical notes from the install.
The download is large for a notes
program (it carries a full app
inside), and the npm step prints a
pile of warnings that are noise; the
version block is the signal. And the
first command against a new profile
is slow — the profile is being built
— while later commands answer in a
couple of seconds.

## The profile check

Point the client at a fresh profile
and ask after its health:

```bash
joplin --profile ~/joplin-lab/profile-a status
```

A new profile reports zeroes across
the board — no attachments, no items
synced, no notebooks (transcript
t00). That empty report is your
baseline: every later chapter's
`status` output is this one, with
numbers that mean something.

The `--profile` flag is how this
guide keeps its pretend machines
apart. On a real machine you will
rarely type it — the default profile
is simply *your* profile — but
knowing it exists explains where
your notes live, and gives you a
safe sandbox of your own:

```bash
joplin --profile /tmp/scratch-profile mknote "practice"
```

## The desktop and mobile apps

For the reader at a desk: the desktop
app (Windows, macOS, Linux) is a
download from joplinapp.org, and the
mobile apps are in the usual stores.
They open the same kind of profile,
speak the same sync, and are where
most people do their daily writing —
the terminal client in this guide is
the same engine with the bonnet up,
which is why it teaches so well.
Installing and driving the graphical
apps is documented-only in this
guide; nothing in later chapters
depends on a window the lab could
not open.
