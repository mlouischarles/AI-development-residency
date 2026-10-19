---
name: accessibility
description: >-
  Make user-facing software accessible to people with disabilities and compliant
  with WCAG 2.2 Level AA. Use this skill whenever building, changing, or
  reviewing anything a person perceives or operates — HTML/JSX markup,
  components, forms, color choices, images, modals, navigation, keyboard
  behavior, focus management, or dynamic content. Apply it even when the user
  doesn't say "accessibility" or "a11y", because accessibility is a requirement
  of enterprise and public-sector software (ADA, Section 508, EN 301 549, the
  European Accessibility Act), not an add-on. Covers the POUR principles,
  semantic HTML, ARIA, keyboard access, color contrast, and screen-reader
  support.
---

# Accessibility (WCAG 2.2 AA)

Accessibility means people with disabilities — visual, motor, auditory,
cognitive — can perceive, understand, navigate, and use the software. It is also
a legal requirement for most enterprise, government, and public-facing products,
and the techniques that make software accessible (semantic structure, keyboard
support, clear focus) make it better for *everyone*. Build it in from the start;
retrofitting accessibility is far more expensive than doing it correctly the
first time.

The current standard is **WCAG 2.2** (W3C Recommendation, October 2023). Target
**Level AA** — it is the level referenced by virtually all accessibility laws,
procurement rules, and legal settlements. Level A is the bare minimum; AAA is
selective.

## The four POUR principles

Everything in WCAG rolls up to these. Use them as your mental model:

- **Perceivable** — users can perceive the information (text alternatives,
  captions, sufficient contrast, content not conveyed by color alone).
- **Operable** — users can operate the interface (full keyboard access, enough
  time, no seizure-inducing content, clear focus).
- **Understandable** — content and operation are predictable and
  understandable (readable text, consistent navigation, helpful errors).
- **Robust** — content works with assistive technologies now and in the future
  (valid, semantic markup; correct names/roles/values).

## Semantic HTML first — ARIA second

The single highest-leverage accessibility practice is using the right native
element. Native elements come with accessibility built in: focusability,
keyboard behavior, and the correct role for screen readers.

- Use `<button>` for actions, `<a href>` for navigation — never a clickable
  `<div>`. A `<div>` with an `onClick` is invisible to keyboard and screen-reader
  users.
- Use real headings (`<h1>`–`<h6>`) in order, lists (`<ul>`/`<ol>`), and
  landmarks (`<nav>`, `<main>`, `<header>`, `<footer>`).
- Associate every form control with a `<label>` (via `for`/`id` or wrapping).
- **First rule of ARIA: don't use ARIA if a native element will do.** ARIA
  patches semantics onto non-semantic markup; incorrect ARIA is worse than none.
  Reach for it only for custom widgets (tabs, comboboxes, dialogs) and follow the
  ARIA Authoring Practices patterns exactly.

## Keyboard access and focus

Many users never touch a mouse. Everything must work with the keyboard alone:

- Every interactive element must be reachable and operable via Tab/Enter/Space/
  arrow keys, in a logical order.
- **Focus must always be visible** — never remove focus outlines without
  replacing them with a clearly visible alternative (WCAG 2.2 strengthened this
  with 2.4.11 Focus Not Obscured).
- Manage focus in dynamic UI: when a modal opens, move focus into it and trap it;
  on close, return focus to the trigger. Announce route changes in SPAs.
- Provide a "skip to main content" link so keyboard users can bypass repeated
  navigation.

## Color and contrast

- **Text contrast:** at least **4.5:1** for normal text and **3:1** for large
  text (≥24px, or ≥18.66px bold) against its background (WCAG 1.4.3).
- **Non-text contrast:** at least **3:1** for UI components and meaningful
  graphics — button borders, form field outlines, icons, focus indicators
  (WCAG 1.4.11).
- **Never rely on color alone** to convey meaning. Pair color with text, icons,
  or patterns (e.g. an error field needs an icon and/or message, not just red).

## Images, media, and non-text content

- Every meaningful image needs descriptive `alt` text; decorative images get
  empty `alt=""` so screen readers skip them.
- Provide captions for video and transcripts for audio.
- Don't convey information in an image of text when real text will do.

## New and notable in WCAG 2.2 (AA)

- **2.5.8 Target Size (Minimum)** — interactive targets at least 24×24 CSS px
  (or adequate spacing), so people with motor impairments can tap accurately.
- **2.5.7 Dragging Movements** — any drag action needs a single-pointer
  alternative (e.g. click-based reorder, not drag-only).
- **3.3.8 Accessible Authentication** — don't force a cognitive test (like
  retyping or puzzle-solving) to log in; allow password managers / copy-paste.
- **2.4.11 Focus Not Obscured** — the focused element must not be fully hidden by
  sticky headers, footers, or overlays.

## How to apply this in practice

When writing or reviewing front-end work:

1. Check the structure: semantic elements, heading order, labeled controls,
   landmarks.
2. Tab through the whole flow with the keyboard. Can you reach and operate
   everything? Is focus always visible? Do modals trap and restore focus?
3. Check color contrast for text (4.5:1) and UI/graphics (3:1), and confirm no
   meaning is carried by color alone.
4. Check text alternatives for images and media.
5. For any custom widget, verify it follows the correct ARIA pattern (name,
   role, value, keyboard interaction).

Report issues with the specific WCAG success criterion and the concrete fix, and
prefer a native-HTML fix over an ARIA workaround wherever possible.
