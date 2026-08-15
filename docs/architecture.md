# Architecture — email to approved order

```mermaid
flowchart LR
    A[Incoming email\n(demo: paste into form)] --> B[Normalize text\nstrip signatures & noise]
    B --> C[LLM: interpret order\nstructured JSON extraction]
    C --> D[Validate JSON schema]
    D --> E[Match against catalog\nexact ref → fuzzy description]
    E --> F{Any uncertain\nlines?}
    F -- all clear --> G[Build order proposal\nlines + prices + warnings]
    F -- doubts --> G
    G --> H[[HUMAN GATE\nreview · correct · approve]]
    H -- approved --> I[(Write to ERP\norders-log.csv)]
    H -- rejected --> J[Log rejection\n+ reason]
    I --> K[Telemetry\nlines resolved · corrections · cycle time]
    J --> K
```

## Design notes

- **The LLM extracts, code matches, a human decides.** The LLM never touches the catalog:
  matching a reference to a product is deterministic code, because an LLM that "helpfully"
  corrects a reference ships the wrong pallet. Uncertain lines are marked, never guessed.
- **The human gate is not a fallback — it is the product.** Every order, clean or doubtful,
  passes through a person before it reaches the ERP. Doubtful lines arrive pre-flagged with
  the candidate matches, so the review takes seconds, not minutes.
- **Telemetry on outcomes.** The system logs how many lines were resolved automatically and
  how many the human corrected. That is how the real-world accuracy figure is *measured*,
  not estimated.
- In the demo, the trigger is an n8n form (paste one of the sample emails and watch it run).
  In production this same flow hangs off a real mailbox trigger; the form makes the demo
  runnable live in interviews with zero credentials.
