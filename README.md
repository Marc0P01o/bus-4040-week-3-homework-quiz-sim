# BUS 4040 — Week 3 Homework, Part 2: Quiz Simulator

**File:** [`index.html`](index.html) — download it and double click. No server, no build step,
no internet connection, no external libraries.

## What type of quiz I created

A 20 question self-test covering Weeks 1 through 3, drawn only from the course files:
the weekly narratives, the homework files, the GitHub connection guide, and the Cline
and MindRouter setup guide. It is a mix of 14 multiple choice and 6 true/false, split 5
questions from Week 1, 7 from Week 2, and 8 from Week 3.

It asks one question at a time and shuffles the order on every run. When I answer, it
tells me immediately whether I was right, explains why, and names the week the answer
came from. At the end it shows my score, a per-week breakdown so I can see which week is
weakest, and a button to retry only the questions I missed.

## What worked

The single biggest thing was the constraint in the prompt: use only the files in this
folder, and skip anything unclear rather than guessing. Without it the questions drift
toward AI facts that are true in general but were never taught in this class, which
would make the quiz useless for the actual exam. Pinning the source material is what
made the output trustworthy.

Making every answer name its week also worked better than I expected. A score by itself
just tells me I got 14 out of 20. The per-week breakdown tells me *Week 3 is where I am
weak*, which is the part I can act on.

The "no external libraries, one file" requirement turned out to be a feature rather than
a limit. There is nothing to install and nothing to break later. The file will still open
in a browser a year from now.

## What did not work, and what I had to adjust

Three things needed a second pass.

The first was the retry feature. The obvious way to remember which questions I missed is
to store their position numbers, but the deck reshuffles on every run, so position 4 is a
different question the next time through. It had to key off a stable id attached to each
question instead. This is a small bug that would not show up until someone actually used
the retry button, which is exactly the kind of thing that slips through when you accept
generated code without reading it.

The second was a question I had to throw out. I wanted to ask which component is worth
the most of the final grade, but going back to the Week 1 table, SPEC, Final Product, and
Peer Review are all tied at 15%. The question had no single right answer. I rewrote it as
a comparison between two specific components instead. Checking the source caught it;
trusting the first draft would not have.

The third was verification. Rather than click through it by hand, I drove the finished
page in a browser and answered all 20 questions automatically, deliberately missing three,
to confirm the score came out to 17, the breakdown summed correctly, the retry pool
contained exactly the three missed questions, and answers locked after the first click.
Everything passed, but running the check is what makes that a fact instead of a hope.

## How I could apply this to other activities

The pattern here is not really about quizzes. It is: point AI at a fixed set of source
documents, forbid it from going outside them, describe the output format precisely, then
verify the result against the source. That works anywhere the cost of a confident wrong
answer is high.

Concretely, the same approach would build a study tool for any other class, a self-check
from onboarding docs at a job, or a practice set from a certification handbook. And the
habit underneath it — constrain the sources, specify the output, then actually test what
comes back — is the part worth carrying into the rest of this course, where the
deliverables get bigger and a wrong answer is more expensive than a missed quiz question.
