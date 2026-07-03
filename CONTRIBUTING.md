# Contributing Guide

## Purpose

This guide defines how we collaborate across Kinetech Labs repositories.

---

## Branching Strategy

- main → production-ready code
- develop → integration branch (optional, use if needed)
- feature/\* → new features
- fix/\* → bug fixes
- chore/\* → maintenance tasks

---

## Workflow

1. Create a branch from `main` or `develop`
2. Implement changes
3. Test locally
4. Open a Pull Request (draft allowed)
5. Request review
6. Merge after approval and CI pass

---

## Pull Requests

- Keep changes focused and small
- Include clear context:
  - What changed
  - Why it changed
- Link related issues if available
- Add screenshots for UI changes

---

## Code Quality

- Prefer simple solutions
- Keep functions small and readable
- Avoid unnecessary abstractions
- Remove unused code

---

## Reviews

- At least one approval required
- Focus on correctness, maintainability, and clarity
- Feedback must be actionable

---

## Testing

- All changes must be tested locally
- Do not rely only on CI

---

## Commit Convention

We follow Conventional Commits.

### Format

type(scope): short description

### Examples

feat(auth): add login flow
fix(api): resolve timeout issue
chore(ci): update workflows
refactor(db): simplify query logic

### Rules

- Use present tense ("add", not "added")
- Keep messages short and meaningful
- One change per commit when possible
