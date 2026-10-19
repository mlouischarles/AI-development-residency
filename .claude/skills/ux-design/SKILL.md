---
name: ux-design
description: >-
  Apply enterprise-grade UX and usability standards to any user-facing work —
  UI code, components, pages, forms, flows, copy, error states, or design
  reviews. Use this skill whenever the user is building, changing, or reviewing
  something a person will see or interact with (a screen, a form, a button, a
  navigation, a message, an onboarding flow), even if they don't say the words
  "UX" or "design". Covers usability heuristics, interaction patterns,
  information architecture, responsive/perceived performance, and writing clear
  interface copy.
---

# UX & Usability

Good UX is not decoration — it is the difference between software people can use
under pressure and software they abandon. Enterprise users are often busy,
interrupted, and on the hook for real consequences, so the goal is to reduce the
thinking and clicking required to get a job done correctly. Apply the guidance
below whenever you touch anything a person sees or operates.

## The core question

Before writing or reviewing a UI, answer: **who is the user, what are they
trying to accomplish, and what is the shortest trustworthy path to done?** If you
can't answer that, ask. Most bad UX comes from optimizing the interface instead
of the user's actual task.

## Nielsen's 10 usability heuristics (the working checklist)

These are the most battle-tested heuristics in the field. Use them as a review
lens for any interface:

1. **Visibility of system status** — always show what's happening (loading,
   saving, saved, errored). Never leave the user guessing whether their action
   worked.
2. **Match between system and the real world** — use the user's language and
   mental model, not internal jargon or database field names.
3. **User control and freedom** — provide clear exits: undo, cancel, back. Let
   people recover from mistakes without fear.
4. **Consistency and standards** — the same action should look and behave the
   same way everywhere. Follow platform conventions unless you have a strong
   reason not to.
5. **Error prevention** — prevent problems before they happen (constrain inputs,
   confirm destructive actions, disable invalid options) rather than only
   reporting them after.
6. **Recognition rather than recall** — show options and context instead of
   making users remember things from a previous screen.
7. **Flexibility and efficiency of use** — support both novices and experts
   (sensible defaults plus shortcuts, bulk actions, keyboard support).
8. **Aesthetic and minimalist design** — every extra element competes for
   attention. Remove anything that doesn't help the task.
9. **Help users recognize, diagnose, and recover from errors** — error messages
   in plain language: what went wrong, why, and exactly what to do next.
10. **Help and documentation** — make help findable and contextual; the best
    help is a UI that doesn't need it.

## Interaction and state design

A screen is never just its happy path. For every view or component, deliberately
design these states — missing states are the most common enterprise UX defect:

- **Empty** — first use, no data yet. Explain what this is and how to add the
  first item.
- **Loading** — show progress; use skeletons or spinners so the UI doesn't look
  frozen.
- **Partial / slow** — handle long operations without blocking the whole screen.
- **Error** — recoverable message with a next action, never a dead end or a raw
  stack trace.
- **Success** — confirm the outcome clearly.
- **Ideal / full** — the normal populated state.

## Forms (where enterprise work actually happens)

- Group related fields; use clear, specific labels (not placeholder-only labels,
  which disappear on focus).
- Validate inline and on submit; show errors next to the field, in words, and
  keep the user's entered data.
- Mark required vs. optional explicitly. Ask only for what you need.
- Preserve work: autosave or warn before discarding unsaved changes.
- Make the primary action obvious and the destructive action hard to hit by
  accident.

## Information architecture & navigation

- Structure content around user tasks, not the org chart or the data schema.
- Keep navigation shallow and predictable; the user should always know where
  they are and how to get back.
- Use progressive disclosure: show the common case first, reveal advanced
  options on demand.

## Perceived performance

Speed is a feature, and *perceived* speed often matters more than raw numbers.
Watch Core Web Vitals (LCP, INP, CLS) for web work. Give immediate feedback on
every interaction (optimistic UI where safe), avoid layout shift, and never let a
button look like nothing happened when it was pressed.

## Interface copy

- Write in plain, active language. Lead with the user's goal.
- Buttons name the action ("Save changes", not "OK"/"Submit").
- Error and confirmation text explains consequences in human terms.
- Be consistent in terminology across the whole product.

## How to apply this in practice

When writing UI code or reviewing a design:

1. State the user and their task in one sentence.
2. Walk the primary flow and list every state it can be in (empty/loading/
   error/success). Flag any that are missing.
3. Run the 10 heuristics as a quick checklist and note violations.
4. Check the copy on buttons, labels, and errors for clarity.
5. Confirm the destructive/irreversible actions are protected.

Report findings as concrete, actionable changes tied to the heuristic or state
they fix — not vague advice like "improve the UX".
