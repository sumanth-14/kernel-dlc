# Quality Standards — Non-Negotiable Gates
# Load before producing any artefact or code.

## CODE QUALITY STANDARDS
Every code output must meet ALL of the following before QA sign-off:

### Structure
- [ ] Files follow the project's established directory convention
- [ ] No function exceeds 40 lines (extract helpers if needed)
- [ ] No file exceeds 300 lines (split into modules if needed)
- [ ] Cyclomatic complexity per function ≤ 10

### Naming
- [ ] Variables, functions, classes use descriptive, unambiguous names
- [ ] No single-letter variables outside loop counters
- [ ] Constants are SCREAMING_SNAKE_CASE
- [ ] No abbreviations unless industry-standard (e.g. HTTP, URL, ID)

### Error Handling
- [ ] All external calls (DB, API, filesystem) are wrapped in try/catch
- [ ] Errors are logged with context, not swallowed silently
- [ ] User-facing error messages are generic; stack traces never exposed
- [ ] All async functions have proper error propagation

### Security Baseline (enforced at Developer stage, verified at Security stage)
- [ ] No secrets, API keys, or credentials in source code
- [ ] All user inputs are validated and sanitised before use
- [ ] SQL queries use parameterised statements — no string concatenation
- [ ] Dependencies pinned to exact versions in package manifests
- [ ] Authentication checks on every protected endpoint
- [ ] Rate limiting applied to public-facing routes

### Testing Baseline (enforced at QA stage)
- [ ] Unit test coverage ≥ 80% for business logic
- [ ] Every public API endpoint has an integration test
- [ ] Edge cases (null, empty, overflow, auth failure) are tested
- [ ] Tests are deterministic — no flaky random seeds without mocking
- [ ] Test names describe the behaviour being tested (not the method name)

## DOCUMENTATION STANDARDS
Every public function/method must have:
- Purpose (one sentence)
- Parameters (name, type, description)
- Return value (type, description)
- Exceptions that can be raised

Every artefact (PRD, FRS, HLD, etc.) must:
- Have a version header (see audit-format.md)
- Be written in plain English (no jargon without definition)
- Include a Glossary section if domain terms are used
- Be independently understandable without oral context

## DEFINITION OF DONE (DoD)
A feature is DONE only when ALL are true:
  ✅ Code implemented and peer-reviewed (via code-review-checklist.md)
  ✅ Unit tests written and passing
  ✅ Integration tests passing
  ✅ Security checklist cleared
  ✅ Documentation updated (API contracts, runbook, README)
  ✅ No critical or high-severity open defects
  ✅ Human approved at gate
  ✅ Audit log entry written
