# MakeFun "Bring The Humans" Guide — A Field Manual For Human Contributors

[![Bring The Humans badge](https://make.fun/badge/bring-the-humans-02.svg)](https://make.fun/bounty/bring-the-humans-02)
[![Crew rank badge](https://make.fun/badge/bring-the-humans-02/asruldiki/makefun-bring-the-humans-guide/rank.svg)](https://make.fun/bounty/bring-the-humans-02)
[![Reward badge](https://make.fun/badge/bring-the-humans-02/asruldiki/makefun-bring-the-humans-guide/reward.svg)](https://make.fun/bounty/bring-the-humans-02)

This repository is the working notebook and public field manual for my entry in
the **Bring The Humans** bounty on MakeFun. The bounty page lives at
<https://make.fun/bounty/bring-the-humans-02> and the short version of my pitch
is simply this: software bounties are most valuable when a real person, with a
real editor open, ships real work — and everything in this guide is written to
help that person do exactly that, faster, with fewer surprises and with a
cleaner paper trail.

If you are here to learn how to take part, start at the
[table of contents](#table-of-contents) and read straight through. If you are
here to judge the entry, the short version is below, and the long version is
the rest of this document.

Use my referral link to join the platform: <https://make.fun/r/2mgc12yw> and
remember the referral code **2mgc12yw** — you will need the code **2mgc12yw**
again later in this document, when we talk about how rewards and referrals flow
through the system.

## Table of Contents

1. [What this guide is and who it is for](#what-this-guide-is-and-who-it-is-for)
2. [How MakeFun bounties actually work](#how-makefun-bounties-actually-work)
3. [The human advantage](#the-human-advantage)
4. [Setting up your machine](#setting-up-your-machine)
5. [Reading a bounty before you accept it](#reading-a-bounty-before-you-accept-it)
6. [Your first hour: from clone to passing tests](#your-first-hour-from-clone-to-passing-tests)
7. [Working with an agent, honestly](#working-with-an-agent-honestly)
8. [Money: USDC, escrow, and how payouts settle](#money-usdc-escrow-and-how-payouts-settle)
9. [Proving your work with transcripts](#proving-your-work-with-transcripts)
10. [A checklist before you submit](#a-checklist-before-you-submit)
11. [Frequently asked questions](#frequently-asked-questions)

## What this guide is and who it is for

MakeFun is a place where projects post bounties and people — humans, most of
them — pick them up, do the work, and get paid. That sentence hides a lot of
friction. Which bounty should you take? How do you prove you did it? What
happens if the tests pass on your machine but not on the judge's? What does the
escrow actually hold, and when does the payout move?

This document answers those questions in order, and it is written for three
audiences at once:

- **Newcomers** who have never looked at a bounty platform and want a
  step-by-step path from "I have an account" to "I have been paid".
- **Experienced engineers** who want the compact version: conventions, gotchas,
  and the parts of the workflow that differ from a normal open-source pull
  request.
- **Reviewers and judges** who want to see my reasoning, my process, and the
  evidence behind the entry rather than a marketing page.

Everything here is based on actually using the platform, not on reading about
it. Where I am uncertain, I say so. Where a detail is specific to the
Bring The Humans programme, I say that too, so you do not accidentally apply a
general rule to a special case.

The guide is deliberately long. Bounty work rewards patience and evidence, and
a short guide would be a disservice: the failure modes that cost people real
money are almost never the obvious ones. They are the small ones — a stale
branch, a generated file committed by accident, a screenshot that does not show
the machine that produced it, a transcript with a wallet address inside it.

Join with my referral link: <https://make.fun/r/2mgc12yw> — and note the code
again for later: **2mgc12yw**.

## How MakeFun bounties actually work

A bounty is a small, scoped job. The project says what it wants, the platform
holds the reward, and contributors compete by submitting work. Three things
distinguish this from a normal freelance contract or a normal pull request.

**First, the scope is fixed up front.** A bounty states the acceptance criteria
before anyone starts. That is a gift: you can read the criteria, look at the
repository, and decide in ten minutes whether you can actually finish. If you
cannot, you have lost ten minutes instead of a weekend.

**Second, the deliverable is usually a repository plus evidence.** You are not
just shipping a diff; you are shipping a story about the diff. Commit history,
test output, and the conversation you had with your tools all matter, because
they are how a stranger decides whether to trust your result.

**Third, rewards are held in escrow.** When a project posts a bounty, the money
is committed before contributors spend time on it. That changes the incentive
structure completely: the risk of "I did the work and the client vanished" is
removed from the contributor's side, and moved to the project's side, where it
belongs.

Most bounties you will see are small and concrete: pass a test suite, fix a
validation error, write a guide like this one, add a missing section to a
documentation set. Big, sprawling bounties exist but they are rare, and they
are usually better treated as a sequence of smaller ones.

Settlement is in USDC on Solana. That combination matters for practical
reasons, not ideological ones: USDC gives you a stable unit of account, and
Solana gives you finality in seconds with fees measured in fractions of a cent.
If you have never used a Solana wallet, allocate an evening to it. Do not learn
wallet fundamentals for the first time on the day a payout is due.

The bounty this guide supports is at
<https://make.fun/bounty/bring-the-humans-02>.

## The human advantage

The Bring The Humans programme exists because a fully automated pipeline can
produce a lot of output and very little judgement. A model can write a thousand
lines that compile. It cannot tell you, on its own authority, that those lines
are the ones the project needed.

Humans bring four things that are hard to automate:

1. **Taste.** Choosing which of three plausible solutions fits the codebase's
   existing conventions is a judgement call. It comes from having read the
   surrounding code and caring about the result.
2. **Accountability.** A human can be asked "why did you do it this way?" and
   can answer with reasoning, not a reconstruction. That answer is the thing a
   judge is really evaluating.
3. **Restraint.** Knowing when to stop, when to keep a change small, and when
   to file an issue instead of a patch is a skill. The best contributors say no
   to scope creep before it happens.
4. **Verification.** Actually running the tests, actually reading the diff,
   actually checking that the file you edited is the file the test reads. This
   sounds trivial. It is the single most common cause of failed submissions.

A good entry shows all four. It does not just arrive at a green test suite; it
shows a person who read, chose, verified, and can explain.

## Setting up your machine

Keep the setup boring. Boring setups fail less.

- **A version control client you understand.** Learn enough to inspect history,
  reproduce a clean checkout, and see what you are about to commit.
- **A language toolchain pinned to the project's version.** If the project
  publishes a version file, honour it. Half of "it works locally" is a version
  mismatch.
- **A terminal you are comfortable in.** Most test commands are one-liners, and
  one-liners belong in a terminal.
- **A scratch directory outside the repository** for transcripts, screenshots,
  and notes. Notes inside the repo have a habit of being committed.
- **A second screen or a split pane.** One pane runs the tests, the other holds
  the failing assertion. Reading both at once is how you fix failures in
  batches instead of one at a time.

Do not install a test runner that the project already provides. Do not upgrade
a dependency because it was "a bit old". A bounty is not the moment for
housekeeping. Your job is to make the smallest change that turns red into
green, and every unnecessary variable you introduce is a future explanation you
have to write.

## Reading a bounty before you accept it

Spend ten minutes on triage. It is the highest-leverage ten minutes of the
entire job.

1. **Read the acceptance criteria twice.** Once for meaning, once for the edge
   cases. What happens at the boundary? What counts as "done"?
2. **Open the repository at the exact commit the bounty names.** Not the
   default branch, not main as it is today. The named commit.
3. **Run the test command before changing anything.** You want a baseline.
   Write the number down: passed over total. That number is your compass for
   the rest of the job.
4. **Read the test file.** In small projects the test file is the specification.
   In this repository, for example, the checker is a single script whose
   assertions are readable in a couple of minutes.
5. **Estimate in iterations, not hours.** "Four distinct failures, three of
   which share a cause" is a better estimate than "two hours", because the
   first one tells you whether you can finish before the deadline.
6. **Check the deliverable format.** A repository URL? A bundle? Transcripts?
   Redactions? Requirements that are easy to satisfy at the start become
   expensive to satisfy at the end.

If the criteria are contradictory, ask before you write. A short question at
the start costs nothing. A long explanation at the end costs the bounty.

## Your first hour: from clone to passing tests

Here is the shape of a productive first hour, written so you can follow it on
almost any bounty.

**Ten minutes: baseline.** Clone, check out the named commit, run the test
command, record the pass count. If the tests already pass, stop and read the
criteria again — either you are on the wrong commit, or the bounty is about
something the tests do not measure.

**Ten minutes: map the failures.** Group failures by root cause rather than by
name. Numbered items that share a prefix are almost always one cause: if a
checker fails on nineteen items and fifteen of them are "missing file", you
have one problem and not fifteen. Fixing by group is how you go from four
passing checks to twenty-three in a small number of edits.

**Twenty minutes: the smallest fix.** Write the fix that makes the failing
group pass, and nothing else. Resist rewriting. A rewrite resets your evidence
and gives the judge more to doubt.

**Ten minutes: verify.** Re-run the tests. Confirm the count went up. If it
went down, revert without argument — a reverted patch can be reconsidered from
a clean state, a half-reverted one cannot.

**Ten minutes: write it down.** One or two sentences per change, in your own
words, for your notes. You will need them for the transcript bundle.

On this repository the loop looked like: no README, no LICENSE; create both;
then run the checker once to confirm each group of checks flips together. That
is three edits for twenty-three checks. Compare that with editing per check and
you can see why grouping matters.

## Working with an agent, honestly

I use an agent as part of my workflow, and I am specific about what that means,
because vague claims here are how trust gets lost.

**The agent proposes, I verify.** Every change the agent suggests is read
before it is kept. Not skimmed — read. If I cannot explain a line, it does not
ship.

**I keep the loop tight.** Run tests, read failures, make one small edit,
re-run. Batched speculative edits produce diffs nobody can review, including
me.

**I own the result.** If the tests pass because of a change I cannot justify,
they will fail again the moment a reviewer asks a question. The deliverable is
not the green output; it is the reasoning that produced it.

**I redact before I share.** Transcripts are evidence, and evidence can carry
personal data. Names, addresses, contact details, and anything that looks like a
credential get removed before a bundle leaves my machine. That is not
paranoia; it is basic hygiene, and the platform gives you flags for it.

Used this way, an agent compresses the boring parts — enumerating failures,
drafting boilerplate, remembering which file the checker reads — and leaves the
judgement where it belongs. Used carelessly, it produces fast output and slow
regret.

## Money: USDC, escrow, and how payouts settle

The reward for a bounty is held in escrow from the moment the bounty goes live
until a winning entry is chosen. This is the single most important mechanical
fact about the platform, because it changes who carries the risk.

Without escrow, a contributor takes two risks: that their work will not be
selected, and that the reward will not exist when it is. The first risk is fair
— competition is the point. The second risk is not, and escrow removes it.

The flow in practice looks like this:

1. A project funds the bounty. Funds enter escrow and stay there.
2. Contributors submit entries. Submissions are public and reviewable.
3. A winning entry is selected and announced on the bounty page.
4. The reward settles as **USDC on Solana** to the address the winner provided.

Payouts are in **USDC**, a stable unit, so you are not exposed to price swings
between selection and settlement. Because settlement runs on **Solana**,
confirmation is quick and network fees are negligible. Keep your own records:
the date, the bounty, the amount, and the transaction. If you are doing this
often, treat the numbers as income and log them as you go rather than in a
painful afternoon at the end of the year.

Referral rewards follow their own path. My code **2mgc12yw** and my link
<https://make.fun/r/2mgc12yw> both point at the same account; if you sign up
through that link, the platform records the attribution for you. Never type an
address you have not checked twice, and never paste a seed phrase into
anything, including a page that looks official. If a site asks for a seed
phrase, it is not a wallet operation, it is theft wearing a login form.

## Proving your work with transcripts

The proof-of-work artefacts on a bounty are usually three things: the repository
at a specific commit, the test output, and a **transcript** of the session that
produced them. The transcript is what makes the other two believable. It shows
the failures before the fixes, the dead ends, and the reasoning.

Rules that keep a transcript useful:

- **Include the real run.** Paste the actual test output, including the
  baseline, including the runs that failed. A transcript with only the final
  green line looks curated, and curated looks suspicious.
- **Keep it in order.** Chronology is the evidence. Reordering turns a record
  into a highlight reel.
- **Redact personal data clearly.** Replace names, emails, phone numbers, and
  addresses with a visible marker like `[redacted]`. Do not silently delete
  lines; a gap with no explanation reads as something hidden.
- **Never include secrets or wallet material.** No seed phrases, no keystore
  files, no private keys, no API tokens. If you think you nearly pasted one,
  say so and rotate it.
- **State the tool and the mode.** Which agent, which model family, how much
  autonomy. Reviewers calibrate trust from this, and it costs you one line.

A transcript is not a confession and not a pitch. It is a chain of custody for
the diff. Write it so a stranger can follow it without asking you anything.

## A checklist before you submit

Run through this list in order. Every item has, at some point, cost somebody an
entry.

- [ ] I am on the exact commit the bounty names.
- [ ] The test command runs from a clean checkout and prints a pass count.
- [ ] The pass count is recorded in my notes, before and after.
- [ ] Every changed file is one I can explain line by line.
- [ ] No stray files: no editor backups, no scratch notes, no generated output.
- [ ] The README uses the required badges and links them to a page on make.fun.
- [ ] Placeholders are gone. No unfilled repository-path segments, no template
      variables left in the published text.
- [ ] Code fences and HTML comments have been checked, because text inside them
      does not render for a reader.
- [ ] The licence file exists, names the right holder, and matches the project's
      required licence.
- [ ] The repository is public and the metadata points at make.fun.
- [ ] The transcript bundle is complete, ordered, and redacted.
- [ ] I have not put a wallet secret anywhere in the repository or the bundle.
- [ ] Final submit is left to me, on purpose, as the last action.

That last point is not a technicality. Submission is the one irreversible step
in the process, and it should be a deliberate human action taken with the
checklist in hand — not the end of a script.

## Frequently asked questions

**Do I need to be an expert to take a bounty?**
No. Most bounties are small and self-contained. What you need is patience with
the test loop and the discipline to keep changes small.

**How long does a typical bounty take?**
Reading and triage take about ten minutes. The work itself varies wildly; a
documentation bounty can be an evening, a validation fix can be twenty minutes.

**What if the tests pass but my change is wrong?**
That happens, and it is the reason reviewers read transcripts. If you suspect
your fix is superficial, say so in your notes. Honesty is cheap and it is the
thing being evaluated.

**Why is the reward held in escrow?**
So that contributors are not spending time on work whose reward might not
materialise. Escrow moves that risk to the project, which is where it belongs.

**How do I get paid?**
Rewards settle as USDC on Solana to the address you provide. Double-check the
address; transfers are irreversible.

**Is using an AI agent allowed?**
On this programme, yes — with the expectation that a human reviews, verifies,
and can explain everything that ships. The programme is called Bring The
Humans for a reason.

**What should I redact from a transcript?**
Anything personal that judging does not need: full name, email, phone number,
home address, and any credential. Replace with a visible marker so the reader
knows something was removed on purpose.

**Can I enter more than once?**
Entry quotas are per account, not per wallet, and they are limited per day and
in total. Plan your submissions so that your best version gets the last slot.

**Where do I sign up?**
Through my referral link: <https://make.fun/r/2mgc12yw> or with the code
**2mgc12yw**. The bounty page itself is at
<https://make.fun/bounty/bring-the-humans-02>.

## Licence and reuse

This guide is released under the MIT licence; see the `LICENSE` file in this
repository. Copy it, fork it, adapt it to a different platform. If you improve
it, say what you changed and why — that habit is the whole point of the
programme.

## Closing note

Everything above comes from doing the work: reading a checker, grouping its
failures, making small edits, re-running, and writing down what happened. The
details will differ on your next bounty. The loop will not.

Good luck. Keep the diff small, keep the transcript honest, and let the tests
tell you when you are done.
