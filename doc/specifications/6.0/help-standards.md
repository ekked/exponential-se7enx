# Help standards

Status: proposal, 18 October 2026. Belongs to [the help system plan](help-system.md) (content model,
access, workflow) and [the help style guide](help-style-guide.md) (editorial rules).

The help follows five standards. Each of them governs something different;
none replaces another.

## Overview

| Standard | Publisher, edition | Governs | Where it applies |
|---|---|---|---|
| **DITA 1.3** | OASIS, standard of December 2015 | the information model: topic types, maps, filter attributes | `help_*` classes, fields, manuals as relation lists, export |
| **IEC/IEEE 82079-1:2019** | IEC and IEEE | the content of instructions for use: completeness, order, notices | structure of tasks, notice levels, where notices stand |
| **ISO/IEC/IEEE 26514:2022** | ISO, IEC and IEEE | information for users of software: design and development | minimalism, task-oriented instructions, figures |
| **ISO 3864-2:2016** | ISO | safety signs and signal words for hazards | only as a boundary: the signal words are **not** used |
| **EPUB Accessibility 1.1** and **WCAG 2.2**, level AA | W3C | accessibility of e-books and web pages | alt text required, e-book checks, web templates |

## DITA 1.3

**What we adopt**

- Every topic has **exactly one** type: `concept`, `task`, `reference`,
  `troubleshooting` (`troubleshooting` is new in 1.3). An "FAQ" is a view,
  not a type.
- Every topic has a `shortdesc`.
- A task has the parts `context`, `prereq`, `steps`, `result`, `postreq`; a
  troubleshooting topic has `condition`, `cause`, `remedy`.
- A manual is a bookmap. Topics exist once in the pool; manuals refer to them
  (`topicref`).
- Audience, platform and version are filter attributes (`audience`,
  `platform`, `rev`/`props`). A DITAVAL file per manual produces the edition
  for one audience.
- Notices are `note` with `@type`: `notice`, `note`, `other` with
  `othertype`.
- The `help_id` is the DITA `id` and the file name in the export.

**What we do differently**

DITA is the **model, not the storage format**. Topics are written in
Exponential content classes, not in DITA XML. Real DITA is produced by the
export (bookmap + DITAVAL, then DITA-OT 4.x). Specialisations, `conref` and
`keyref` are not used; reuse works through the references of the manuals to
the topic pool.

## IEC/IEEE 82079-1:2019

**What we adopt**

- **Prerequisites before the steps, the result after them.**
- **Notices where the action happens**: in the step, before the action that
  triggers them, not in an appendix and not in a collected chapter.
- **Graded marking** of notices.
- **Language that fits the audience**, consistent terms (glossary).
- **Validity**: which version a piece of information belongs to
  (`version_from`/`version_to`), next review (`review_date`).

**What we do differently**

The standard comes from product safety. Software without actuators does not
endanger persons; the levels for hazards to persons are therefore dropped
(see ISO 3864-2). They are replaced by three levels by consequence for data
and access: **Attention**, **Data protection**, **Note** ([help style guide](help-style-guide.md),
section 5).

## ISO/IEC/IEEE 26514:2022

**What we adopt**

- **Task-oriented**: instructions start from what readers want to achieve,
  not from the structure of the interface.
- **Minimalism**: action first, only what readers need for their task, plan
  for mistakes (a separate troubleshooting topic).
- **Steps**: imperative, one action per step, labels exact.
- **Figures** add to the text but never carry information alone.

**What we do differently**

Nothing fundamental. The standard also covers planning and managing the
documentation project; here that is done by object states, roles and the
validator ([help system plan](help-system.md)).

## ISO 3864-2:2016

DANGER, WARNING and CAUTION refer to **hazards to persons**. We do **not** use
them. Using them for data loss devalues them for the case in which they
matter.

## EPUB Accessibility 1.1 and WCAG 2.2 AA

**What we adopt**

- **Alt text is required** on every figure (`help_screenshot`), at most 150
  characters, describing what readers need for their step.
- A topic is complete **without** its figure.
- E-books are checked with **epubcheck** (validity) and **Ace by DAISY**
  (accessibility) before they are stored.
- The web templates follow WCAG 2.2 AA (heading order, contrast, no
  information by colour alone, operable by keyboard).

## Scope

- **Conformance is not claimed.** Content and model are aligned with these
  standards; a formal audit or certification is not planned.
- **The validator checks part of the rules** (one numbered list per task,
  alt text, `shortdesc`, `help_id`, glossary, review date, section).
  Language, minimalism and where notices stand are checked in the review.
- What DITA, EPUB Accessibility and WCAG require of the output can only be
  verified on generated files: the export and its checks ([help system plan](help-system.md),
  "Delivery paths") are where that happens.

## Sources

- OASIS: *Darwin Information Typing Architecture (DITA) Version 1.3*, 2015.
- IEC/IEEE 82079-1:2019 *Preparation of information for use (instructions
  for use) of products — Part 1: Principles and general requirements.*
- ISO/IEC/IEEE 26514:2022 *Systems and software engineering — Design and
  development of information for users.*
- ISO 3864-2:2016 *Graphical symbols — Safety colours and safety signs —
  Part 2: Design principles for product safety labels.*
- W3C: *EPUB Accessibility 1.1*, 2023; *Web Content Accessibility Guidelines
  (WCAG) 2.2*, 2023.

## Related pages

- [Help system plan](help-system.md)
- [Help style guide](help-style-guide.md)
