# Template for `docs/states/<flow>.md`

```markdown
# <Flow> · state matrix

Scope: <surfaces in scope, routes>. Date: <YYYY-MM-DD>.
Global handling: <what the app already does everywhere, e.g. offline banner, toast on failed writes, retry policy>.

## Truths

| Surface | Source | Outcomes |
| --- | --- | --- |
| <surface> | <endpoint, query or mutation> | 200 · 404 · 409 · 5xx · network · timeout |

## Matrix

| Surface | Loading | Empty | Error | Success | Pending · slow | <axis columns> |
| --- | --- | --- | --- | --- | --- | --- |
| <surface> | <sees · copy · way out · motion> | … | … | … | … | … |

## Opens

| ID | Severity | Evidence | Fix |
| --- | --- | --- | --- |
| <FLOW>-E01 | high | <file:line> | <fix> |

## Decisions

### D1 · <question>
<options>
Recommend: <option>, because <one line>.

## Out of scope

- <item>
```
