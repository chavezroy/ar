---
name: jsx
description: Create, refactor, and debug React components in .jsx files with maintainable structure, accessible markup, predictable state flow, and clear props contracts. Use when tasks mention JSX, React UI components, .jsx files, component extraction, event handling, conditional rendering, list rendering, form handling, or client-side UI bug fixes.
---

# JSX

## Overview

Build and modify React `.jsx` components with fast, reliable patterns that reduce regressions. Keep code readable, accessible, and easy to test while preserving existing project conventions.

## Quick Workflow

1. Identify the component boundary before editing.
2. Confirm data flow:
   - props in
   - local state where needed
   - callbacks out
3. Implement or refactor JSX with semantic HTML first.
4. Add guardrails for loading, empty, and error states when relevant.
5. Validate behavior with existing tests or targeted manual checks.
6. Keep diffs focused; do not mix unrelated cleanup.

## Component Rules

- Keep component responsibilities narrow.
- Prefer small composable components over deeply nested JSX blocks.
- Destructure props at the top of the component.
- Avoid derived state when a value can be computed directly from props/state.
- Keep side effects out of render logic.
- Extract repeated chunks into child components when duplication appears twice or more.

## Accessibility Rules

- Use semantic elements (`button`, `label`, `nav`, `main`) before adding ARIA.
- Ensure interactive elements are keyboard reachable.
- Pair form inputs with labels.
- Provide `alt` text for meaningful images.
- Preserve visible focus indicators.

## Rendering and State

- Prefer early returns for loading/empty/error states.
- Keep conditional rendering simple; extract complex conditions into named variables.
- Use stable keys for list rendering; do not use array index if order can change.
- Normalize event handlers (`handleClick`, `handleSubmit`) and keep them close to usage.
- For forms, keep controlled inputs consistent unless the project intentionally uses uncontrolled patterns.

## Refactor Patterns

- Split large components by responsibility:
  - presentation component
  - stateful wrapper/container
- Replace nested ternaries with helper variables or subcomponents.
- Convert repeated inline callbacks in hot paths into memoized handlers only when profiling or clear rerender issues justify it.
- Remove dead props and unused branches during edits.

## Debug Checklist

- Verify props arriving at the component match expected shape.
- Confirm event handlers fire and update state as intended.
- Inspect conditional branches with representative test data.
- Check browser console for key warnings and controlled/uncontrolled input warnings.
- Confirm no accessibility regressions in edited interactive areas.
