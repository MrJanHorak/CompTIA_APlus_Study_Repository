# Contributing to the CompTIA A+ Study Repository

Thank you for taking the time to contribute. This repository is a community effort, and every improvement — from a typo fix to a full domain rewrite — helps fellow students succeed.

---

## Ways to Contribute

- **Fix errors** — Incorrect facts, outdated specifications, or broken links
- **Add content** — Expand existing notes with additional objective coverage
- **Create flashcard decks** — Export Anki or Quizlet decks and share them in `Resources/Flashcards/`
- **Write lab guides** — Step-by-step exercises that reinforce specific exam objectives
- **Improve clarity** — Simplify explanations, add examples, or improve formatting

---

## Guidelines

### Accuracy

All technical content must align with the current **CompTIA A+ Version 15** objectives (220-1201 / 220-1202). When referencing Version 14 (220-1101 / 220-1102) differences, label them clearly:

```
> **v14 Note:** In 220-1101, this objective covered X. In 220-1201, it now includes Y.
```

### Formatting

- Use Markdown for all documentation files.
- Tables should use standard Markdown pipe syntax.
- Code blocks should specify the language for syntax highlighting (e.g., ` ```bash `).
- Keep headings consistent with the existing hierarchy in each file (H1 for title, H2 for sections, H3 for sub-topics).

### Citing Sources

If you add content derived from a specific resource (book, video, official objective document), add a brief inline note:

```
> Source: CompTIA A+ Exam Objectives v15, Domain 3.0
```

### Review and Maintenance

- Link to a primary source for factual corrections and record the review date for exam metadata and external resources.
- Keep the [objective coverage map](Resources/Objective_Coverage.md) aligned with note changes. Coverage means introductory notes, not complete mastery.
- For labs, specify application/guest versions, host architecture, exact addressing and expected results. Record whether the workflow was actually run; do not label a lab tested from document inspection alone.
- Describe free, account-required and paid access separately. Disclose complimentary reviewer access when used, avoid fixed promotional counts, and evaluate providers by the same criteria.
- Recheck exam status, source links, operating-system support, resource access and book editions before each release and at least every six months.

---

### Scope

- Focus on A+ objectives. Clearly label supporting professional practices (such as the troubleshooting methodology) that are useful but not directly tested.
- Do not include exam dumps, leaked questions, or content from paid exams.
- Do not add affiliate links.

---

## How to Submit Changes

1. Fork the repository.
2. Create a descriptive branch: `fix/ram-pin-counts` or `add/lab-03-disk-management`.
3. Make your changes.
4. Open a Pull Request with a clear title and description of what was changed and why.
5. A maintainer will review and merge or request adjustments.

---

## Reporting Issues

If you find an error but cannot fix it yourself, open an Issue describing:

- The file and section where the error appears
- What is incorrect
- What the correct information should be (with a source if possible)

---

_Thank you for helping other students pass their A+ exams._
