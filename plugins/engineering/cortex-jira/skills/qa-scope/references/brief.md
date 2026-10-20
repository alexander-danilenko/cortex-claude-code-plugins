# Brief format

A short list a tester scans in one minute: what to check, and which checks a test already covers. It leaves out the context sections and the steps; the tester picks the clicks.

## Shape

Put this between the title and the shared _Automated tests_ section from SKILL.md:

```markdown
## Test scenarios

### <group: New / Changed / Fixed / Existing data / Regression>

- **<short name>** — <one or two sentences: who the tester is, what they do, what they must see> · <test keys, only when covered: `[T1]` `[T3]`>
```

## Rules

- One list item per scenario. No Given/When/Then, no steps, no variables.
- Each item still names the account state, the action and the visible result, so the tester knows what passing looks like.
- When the state is hard to reach (a suspended account, a specific role), say so in the item.
