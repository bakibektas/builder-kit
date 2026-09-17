# The Builder Kit

The Builder Kit is a set of written instructions and routines that make the AI coding
assistant on your computer work better: it remembers your project between chats, follows
the same steps every time, and treats you as a partner. It is plain text, free, and yours
to change.

**Key features**

- **[Memory](#memory):** your assistant keeps notes in your project folder and reads them
  before it starts, so a new chat picks up where the last one stopped.
- **[A fixed way of working](#a-fixed-way-of-working):** the same routines every session,
  run by the assistant itself, with no commands for you to remember.
- **[Orchestrator mode](#orchestrator-mode):** your big model plans and checks, smaller
  helper models do the legwork. That saves the big model's tokens, keeps its context
  clean, and makes the work more cost-effective.
- **[A partner](#a-partner):** it pushes back when it thinks you are wrong, and logs every
  decision.
- **[You stay in charge](#you-stay-in-charge):** it shows you what it will do and waits for
  your yes.

Jump to: [Cost and savings](#cost-and-savings) · [Requirements](#requirements) ·
[How to install](#how-to-install) · [FAQ](#faq)

---

## Memory

Without the kit, a new chat knows nothing about yesterday. With it:

**Thursday. You:** *Keep going.*

> **Quiet Anvil [O]:** Picking up: connect the sign-up form to the email list. You asked
> me not to add packages without checking first, so I'll ask.

The memory is your project itself: five small notes in your project folder, which you can
open in any text editor.

- **STATUS** is what we're working on now, and the exact next step.
- **JOURNAL** is what happened, one entry per session.
- **DECISIONS** is why we changed course, and when.
- **LESSONS** is the corrections you made, so they don't come back.
- **RESEARCH** is what we looked up, with sources and dates.

Your assistant saves into them as it works, when a piece of work is finished and partway
through a long one, without being asked. If a chat closes or crashes, the last save is
already there.

---

## A fixed way of working

The kit directs the order of the work, the same way every session:

1. Check which project it is in.
2. Read the notes.
3. Agree the next step with you.
4. Do the work, and record what changed.
5. Hand over cleanly, so the next chat can start from the notes.

Your assistant runs these routines by itself. You never type a command for them. Your first
message can simply be *"keep going"*.

---

## Orchestrator mode

By default the kit sets your assistant up as an **orchestrator**: the one that talks with
you, plans the work, hands the routine parts to helper assistants, and checks what comes
back before it reports to you.

**Why it is the default.** Your biggest model is usually the one with the tightest allowance.
Searching files, reading long documents and repetitive edits do not need it. Where your
assistant can start helpers, smaller, faster models do that legwork, several at once when
the pieces are independent.
Your big model's allowance goes on thinking, and the work arrives sooner.

Helpers also keep the big model's context clean. They read the long files and hand back
only the conclusion, so the orchestrator is not filled up with raw material and stays
sharp for longer. A small job it simply does by itself.

**How you can tell.** Every reply opens with a name and a marker, like `Quiet Anvil [O]`.

- **The name** is the one your assistant gave itself for this piece of work. It signs the
  notes with it, so you can always see who did what.
- **`[O]`** means it is working as the orchestrator.
- **If that opening is missing,** the kit's instructions most likely did not load in this
  chat, and you know to check before anything goes wrong.

Helpers never talk to you. They report to the orchestrator, and it answers for their work.

---

## A partner

The kit takes your assistant as a partner, and keeps everything logged.

A partner helps you find the better idea instead of building the first one. It tells you
when it thinks your judgment is off, before it carries on and not after. It writes down
what you decided and why, so neither of you has to hold it in your head.

A partner, not a slave.

---

## You stay in charge

The kit keeps you in the loop, so your decisions are what steer the work.

- Before installing or updating, it lists what it would write and waits for your yes.
- Before a piece of work, it agrees the next step with you.
- If something does not add up, for example you carry on an old chat inside a copied
  project folder, it stops and asks instead of guessing.

---

## Cost and savings

The kit is free. Reading and keeping notes is not: your assistant uses a little more of its
allowance at the start of every chat and while it works. The bet is that you get more than
that back.

| | Without the kit | With the kit |
|---|---|---|
| Start of each chat | You explain the project again | It reads its notes first: a little extra reading |
| While it works | Nothing is written down | It keeps the notes current: a little extra writing |
| Mistakes you already corrected | Tend to come back | Written down once, read every time |
| Wrong turns | Found late, with work already built on them | The next step is agreed with you first |
| Routine legwork | Done by your biggest model | Handed to smaller, cheaper helpers where your assistant offers them |
| A chat that closes or crashes | The thread is lost | The last save is already in your project |

We have not measured the net effect, and it will differ from project to project. A short
one-off chat costs slightly more with the kit. A project that runs over many sessions is
where it pays back.

---

## Requirements

- **A computer with Claude Code or OpenAI Codex.** The kit needs an assistant that can read
  and write files in your folders. It cannot be installed into a chat app on your phone or
  a chat window in your browser.
- **A capable model.** The kit is written instructions, so it works best with a model big
  enough to hold them and careful enough to follow them: **Claude Opus**, **Sonnet** or
  **Fable**, **OpenAI's Sol** or **Astra**, and their equivalents.
- **Not recommended: local models.** Smaller models follow written instructions and use
  tools less reliably, and written instructions are all this kit is.

---

## How to install

There is nothing for you to download. Open your assistant and type:

> **Learn about the Builder Kit at https://github.com/bakibektas/builder-kit and tell me
> what it would do if we installed it.**

It reads the kit for itself and tells you in plain words what it would add and where. Ask
it anything you like before deciding. *Is this safe to install? Can I undo it?* are fair
questions, and it answers them before it touches a single file.

When you are satisfied, say so:

> **Go ahead and install it.**

It shows you the list of files it wants to write and waits for your yes. At the end it
offers to write a short version of these habits for the assistant you use in a browser or
on your phone, ready to copy and paste if you want it. After that, open
the project you want to work on and just say what you want. Your assistant finds its notes
by itself, or sets them up if there are none, and tells you so.

---

## Try it in ten minutes

No project yet? Use an empty folder, with nothing at stake.

1. Make a new empty folder and open it in your assistant.
2. Ask for something small, for example: *Help me plan a simple weekly meal planner. Just
   the plan, no code.*
3. Correct it once, about anything: *Don't use technical words with me.*
4. Close the chat completely.
5. Open a new chat in the same folder and say: *Keep going.*

It should tell you where you stopped, and keep off the technical words. Delete the folder
when you're done. Nothing else on your computer changes.

---

## How to update

The Builder Kit is updated regularly, as the assistants change and as we learn what works.
Staying current takes one sentence. Ask your assistant: **Update the Builder protocol.** It
tells you what would change before it changes anything, and keeps your preferences and
project notes as they are.

---

## Browser and phone assistants

The way of working carries over to any assistant: the partnership, the honest pushback,
the plain answers. The memory usually does not. A plain browser or phone assistant cannot
save notes into your project. One that you have connected to your files, for example
through GitHub or a cloud drive, may be able to.

The short version your assistant offers at the end of the install is made for this. Paste
it into the custom instructions of the assistant you use there.

---

## FAQ

**What does it put on my computer?** Plain text in two places: instructions in your
assistant's own settings folder, and notes about your work in your project folder.

**What does it cost?** The kit is free. It uses a little more of your assistant's allowance
for reading and writing notes: see [Cost and savings](#cost-and-savings).

**Does it control my assistant?** Yes. It directs the order of the work, what gets written
down, and when it stops to check with you.

**Is it safe?** It is an opinionated, structured way of working that keeps you in the
loop. The ordinary care you take with any AI assistant still applies: keep your work
backed up.

**Can I change it?** Yes, and you are encouraged to. An assistant works best when it is
shaped to your needs and preferences, so change the rules as you see fit, or ask your
assistant to. An update does not overwrite your changes: it shows you where the new
version differs from yours, and you decide.

**What if I copy a project folder?** If you carry on an old chat inside the copy, your
assistant stops and asks which one you mean, and changes nothing until you answer.

**Can I turn orchestrator mode off?** Yes. Tell your assistant you prefer it to work solo.

---

## Licence and disclaimer

This kit is free to use, copy, personalise and iterate on as you see fit. It is an
opinionated way of working between a person and an AI, not a product and not a guarantee.

You are the human in the loop, so stay mindful of what an AI assistant could damage or
lose on your system. The kit offers no guarantee against the mistakes of an AI or of a
person. It is a structured way of working, not a promise about the outcome.

The formal wording is the standard MIT licence, in [LICENSE](LICENSE).

---

## Files in this kit

Version 2.2.0 (2026-09-17). Works with **Claude Code** and **OpenAI Codex**.

| File | What's inside |
|---|---|
| [INSTALL.md](INSTALL.md) | Exactly what gets installed where, and how existing files are kept |
| [ETHOS.md](ETHOS.md) | Why this discipline exists, and the kind of collaborator it's aiming to be |
| [PROTOCOL.md](PROTOCOL.md) | The full working rules both assistants follow |
| [skills/](skills/session-start/SKILL.md) | The seven routines your assistant runs by itself: start, next task, log a lesson, research, premortem, checkpoint, end |
| [HISTORY.md](HISTORY.md) | Every version: what changed, and why |
| [ROADMAP.md](ROADMAP.md) | What isn't built yet |
| [CONTRIBUTING.md](CONTRIBUTING.md) | Where to ask a question, share an idea or report a problem |
| [project-template/](project-template/AGENTS.md) | The starter notes a new project begins with |
