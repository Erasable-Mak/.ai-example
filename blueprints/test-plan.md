# QA Test Plan - [TICKET_ID]
> Mode: test_plan | Date: [date] | Summary: [summary]

## Feature Scope & Overview
[Brief overview of what is tested]

## Test Environment & Pre-Conditions
- Browser versions / viewports (Desktop: 1440px, Tablet: 768px, Mobile: 375px)
- Auth session state (Logged in as Admin / Member)
- Test database seeding requirements

## Test Scenarios
| TC ID | Scenario Description | Pre-conditions | User Steps | Test Data | Expected Outcome | Pass/Fail |
|---|---|---|---|---|---|---|
| TC-01 | Happy path creation | User on `/new` | Fill form, click Submit | Valid inputs | Success toast + redirect | |
| TC-02 | Form validation error | Empty required field | Click Submit | Empty field | Inline validation error | |
| TC-03 | Network failure handling | Disconnect network | Click Action | Standard data | Retry banner shown | |
| TC-04 | Empty state verification | Zero records exist | Open list view | Empty DB | Empty state illustration | |

## Regression Impact Areas
| Area / Screen | Potential Impact | Verification Required |
|---|---|---|
