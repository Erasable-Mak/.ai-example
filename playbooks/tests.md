# Playbook: Test Generation (--mode=tests)

**Goal:** Generate comprehensive automated test suites strictly following engineering standards.

## 1. Input Flexibility
Requirements or target files to test can be supplied directly in the user's chat prompt or via `.ai/local/`. Creating local files is strictly optional.

## 2. Test Standards & Requirements
- **Framework:** Use Vitest for native TypeScript compilation, execution speed, and type safety.
- **Pattern:** Always organize test cases using the Arrange-Act-Assert (AAA) pattern within `describe` and `it` blocks.
- **Strict Typing:** Maintain complete type definitions throughout the test file. Avoid `any` under all circumstances.
- **Mocking:** Only mock external dependencies when real values or network instances cannot be safely fetched or executed. When mocking, use type-safe mocking (`vi.fn<T>()`, `vi.mocked()`) preserving full TypeScript interfaces.
- **Naming Conventions:** Ensure `it` statements read like clear, descriptive sentences detailing the expected behavioral outcome (e.g. `it('should throw a ValidationError when the email is missing')`).
- **Focus Areas:** Target dynamic business logic, asynchronous operations, state changes, and runtime edge cases. Do not write tests for static type validations that the TypeScript compiler already enforces.
- **Quality:** Write robust and strong unit and integration tests. Do not generate bogus or superficial test cases.
- **No Emojis:** Do not include emojis in comments, assertions, or test titles.

## 3. Test Matrix & Code Authoring
1. Build a test matrix per requirement:
   | Test Name | Target Behavior | Input / Setup (Arrange) | Action (Act) | Assertions (Assert) |
2. Cover:
   - Happy Path: Standard user flow, valid inputs, expected state mutations.
   - Dynamic Edge Cases: Boundary conditions, empty datasets, debounce/timer logic.
   - Asynchronous & Error States: Network timeouts, rejected promises, error toasts.
3. Emit complete, executable Vitest code with top-level imports and file/function docstrings.
4. Output the proposal directly in chat (or in `.ai/local/[TICKET_ID]/[TICKET_ID]-tests.md`) following [.ai/blueprints/test-report.md](file:///.ai/blueprints/test-report.md).
