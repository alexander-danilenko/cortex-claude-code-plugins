# Full format

The complete handoff: the context a tester needs to understand the change, a summary for the lead, and Given/When/Then steps for every scenario.

## Shape

Put this between the title and the shared _Automated tests_ section from SKILL.md:

```markdown
## Summary

- **<flow or scenario name>** — <one to three sentences: what to test there and why, no steps> · <test keys, only when covered: `[T1]` `[T3]`>
- <up to 5 items>

---

## What changed

- <1–3 bullets: the behaviour a user sees now, in product words>

## Decisions from the ticket comments

- <decision, and what it means for testing>

## In scope

- <page or flow> — <what to check there>

## Out of scope

- <what looks related but did not change, so QA does not spend time on it>

## Test scenarios

### <group: New / Changed / Fixed / Existing data / Regression>

#### Scenario: <short name> · <test keys, only when covered: `[T1]`>

- **Given** <who the tester is and the account state, e.g. a signed-in user with the `{user_role}` role>
- **And** <extra setup, if needed>
- **When** <one action the tester takes, e.g. opens `/search?q={search_term}`>
- **Then** <what they must see>
- **And** <extra check, if needed>
```

_Summary_ is never left out, even for a small change.

## Rules for the summary

- It is the part a busy reader reads alone: a lead planning the test run, or a tester deciding where to start. They must see the whole scope in 30 seconds, without scrolling to the details.
- Write at most 5 items. Each item names one flow or scenario group in bold, then says in plain words what to test there. No Given/When/Then, no steps, no variables.
- Group scenarios to fit the limit. Several scenarios on one flow become one item. A regression check gets its own item only when it is a real risk.
- Order the items as the detailed part orders them: the main change first, regression checks last.
- Write the summary after the detailed part, so the two agree. The horizontal line (`---`) separates them.
- An item lists the test keys of all its scenarios, once each, in key order.

## Rules for the steps

- Write each step as a Markdown list item. Separate lines without list markers merge into one paragraph in Jira and in most Markdown viewers.
- Write each value the tester picks as a variable in backticks and curly brackets: `{user_role}`, `{search_term}`, `{user_email}`. Use snake_case names that say what goes there. The tester then knows which values are theirs to choose, and the same scenario works on every environment.
- `Given` sets up an account state a tester can create or find. When the state is hard to reach (a suspended account, a specific role), say so — they may need an admin or a developer to set it up.
- `Then` is visible: text on a page, a button that appears or goes away, an email, a new row in a list. "The system updates the record" is not a check.
- Stay high level — steps like "click Save" belong to QA.
