# Before / after — three real processes, same design principle

The person never disappears. They stop typing data and start approving decisions.

> Figures shown are from the real systems these patterns come from, measured by built-in
> telemetry. Client names and internals are never published; the diagrams show the process
> pattern only.

---

## 1. Email orders → ERP (the process this demo replicates)

```mermaid
flowchart LR
    subgraph BEFORE [Before — manual]
        direction LR
        a1[Order email arrives] --> a2[Read & decipher\nby hand] --> a3[Search catalog\nreference by reference] --> a4[Type into ERP] --> a5[Errors →\nrework & returns]
    end
```

```mermaid
flowchart LR
    subgraph AFTER [After — with the system]
        direction LR
        b1[Order email arrives] --> b2[LLM interprets] --> b3[Automatic catalog match] --> b4[Order proposal] --> b5[[HUMAN\napproves]] --> b6[(ERP)]
    end
    style b5 fill:#2f6f4f,color:#fff
```

**Measured:** 1,300+ real orders · 96% measured accuracy · 55% less time — advanced live
pilot, final ERP go-live in progress.

---

## 2. Executive mailbox triage (in daily production)

> ⚠️ Draft — process steps and published figure pending final validation.

```mermaid
flowchart LR
    subgraph BEFORE3 [Before — manual]
        direction LR
        e1[Exec mailbox\nhundreds of emails] --> e2[Read everything\nto find what matters] --> e3[Forward, file,\ncreate tasks by hand] --> e4[Important emails\nslip through]
    end
```

```mermaid
flowchart LR
    subgraph AFTER3 [After — with the system]
        direction LR
        f1[Exec mailbox] --> f2[AI classifies\n& routes] --> f3[Documents filed,\ntasks created] --> f4[[HUMAN handles\nonly what needs them]]
    end
    style f4 fill:#2f6f4f,color:#fff
```

**Measured:** 190+ hours saved, tracked operation by operation · 98.7% accuracy — in daily
production.
