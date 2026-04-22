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

## UI/UX QUALITY STANDARDS
Every user-facing output must meet ALL of the following before QA sign-off:

### Accessibility (WCAG 2.1 Level AA — non-negotiable)
- [ ] All text meets contrast ratio ≥ 4.5:1 (normal text) or ≥ 3:1 (large text / UI components)
- [ ] All interactive elements are keyboard-accessible (Tab, Enter, Space, Escape, arrow keys)
- [ ] Focus indicator is visible on every interactive element — never hidden or removed
- [ ] No information is conveyed by colour alone (always paired with text or icon)
- [ ] All images have appropriate alt text; decorative images have alt=""
- [ ] All form inputs have an associated visible label (not placeholder-only)
- [ ] Error messages describe the problem and the fix — not just "Invalid input"
- [ ] Heading hierarchy is logical (h1 → h2 → h3, no skipped levels)
- [ ] Page has a unique, descriptive <title> for every screen
- [ ] No content flashes more than 3 times per second

### Responsive Design
- [ ] Layout is verified at: 320px, 768px, 1024px, and 1440px viewport widths
- [ ] No horizontal scrollbar appears at any supported breakpoint (except intentional data tables)
- [ ] Touch targets on mobile are ≥ 44×44px (WCAG 2.5.5)
- [ ] Text does not overflow or overlap at any breakpoint

### Visual Consistency
- [ ] All colours reference design system tokens — no hardcoded hex values in component styles
- [ ] All spacing uses the design system spacing scale — no arbitrary pixel values
- [ ] Typography uses design system type tokens — no font-size or font-weight values set ad hoc
- [ ] All component variants (loading, empty, error, success) are implemented per wireframes

### Frontend Performance (Core Web Vitals targets)
- [ ] Largest Contentful Paint (LCP): < 2.5s on a simulated mid-range mobile device
- [ ] Cumulative Layout Shift (CLS): < 0.1 (no unexpected layout jumps)
- [ ] Interaction to Next Paint (INP): < 200ms
- [ ] JavaScript bundle size reviewed — no unnecessary large dependencies added without ADR

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

For features with user-facing UI, additionally:
  ✅ Implementation matches approved wireframes (no unexplained deviations)
  ✅ All design system tokens used correctly — no hardcoded style values
  ✅ All screen state variants implemented (loading, empty, error, success)
  ✅ WCAG 2.1 AA accessibility verified (automated scan + keyboard walkthrough)
  ✅ Responsive layout verified at all defined breakpoints
