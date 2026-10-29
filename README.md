# Joplin for Mere Mortals

Most note apps keep your notes on
someone else's computer: you write, the
text travels to a company's servers, and
you read it back through their app, on
their terms, while the account lasts.
**Joplin** does the same job with the
company left out. It is an open-source
note-taking program that runs on your
own machines. Your notes live in a
folder on your disk first; if you want
them on your other machines, Joplin
syncs them through a target *you*
choose — a folder, your own server, a
cloud drive — and it can encrypt them
end to end, so the sync target only
ever holds ciphertext.

This guide explains how Joplin organises
notes, how to install the terminal
client, and how to take your first
notes. Then it does the part most
note-app guides skip: it **proves** the
sync. The lab that wrote this guide ran
two separate Joplin profiles — two
pretend machines — against one shared
folder, and watched notes travel up,
arrive on the empty machine, and travel
back again.

The lab behind this guide ran the real
thing: **Joplin 3.7.1**, the official
terminal client, installed from npm on
a small Linux machine. Against it the
lab made notebooks and notes, wrote
note bodies, attached a file, tagged
and exported, imported the export into
a fresh profile to prove it was a real
backup, and ran the two-machine sync
described above. It also tried, three
different ways, to switch on end-to-end
encryption from the terminal — and
failed, for a reason this guide states
plainly rather than papering over
(chapter 8): this sandbox has no system
keychain, and in it the master password
has nowhere to live. The encryption
chapter is therefore labelled
documented-only, and shows instead the
verified opposite — exactly what an
*un*encrypted sync target exposes.

What the lab could not do, it did not
fake. It had no display, so the desktop
app's windows are described, never
graded. Search was checked at the level
of the database and the local API, and
chapter 6 shows what that check found —
including the empty index.

## How to use this guide

Read chapter 1 for the model, and
chapter 2 before installing anything —
knowing which part holds what turns
later confusion into a named problem.
Chapters 3 and 4 get you the program
and your first notes in the same
sitting. Chapter 7 is the one to read
slowly even if you never sync: its
checks are how you catch the dangerous
misunderstanding — that sync is a
backup — before it costs you a
notebook. The lab's transcripts live
in `joplin-lab/transcripts/`.

---

## Part of the series

This guide is one of the [For Mere Mortals](https://paulsullivan33-dev.github.io/mere-mortals/) guides: plain-language guides to the tools programmers and makers use.

Related guides:

- [Obsidian for Mere Mortals](https://paulsullivan33-dev.github.io/obsidian-for-mere-mortals/)
- [Markdown for Mere Mortals](https://paulsullivan33-dev.github.io/markdown-for-mere-mortals/)

## License

The writing in this guide is licensed under [CC BY 4.0](https://github.com/paulsullivan33-dev/joplin-for-mere-mortals/blob/main/LICENSE). Code examples and lab scripts are licensed under the [MIT License](https://github.com/paulsullivan33-dev/joplin-for-mere-mortals/blob/main/LICENSE-CODE).
