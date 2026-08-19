# Before / after — three real processes

The person never disappears from any of them. In orders and invoicing they approve before
anything posts; in the mailbox they handle only what needs their judgement.

> Accuracy figures come from each system's built-in telemetry; time savings compare against
> the baseline the client's team reports for the manual process. Client names and internals
> are never published; the diagrams show the process pattern only.

---

## 1. Email orders → ERP (the process this demo replicates)

```mermaid
flowchart LR
    subgraph BEFORE1 [Before — manual]
        direction LR
        a1[Order email arrives] --> a2["Read & decipher<br/>by hand"] --> a3["Search catalog<br/>reference by reference"] --> a4[Type into ERP] --> a5["Errors →<br/>rework & returns"]
    end
```

```mermaid
flowchart LR
    subgraph AFTER1 [After — with the system]
        direction LR
        b1[Order email arrives] --> b2[LLM interprets] --> b3[Automatic catalog match] --> b4[Order proposal] --> b5[["HUMAN<br/>approves"]] --> b6[(ERP)]
    end
    style b5 fill:#2f6f4f,color:#fff
```

**Results:** 1,300+ real orders · 96% accuracy from telemetry · 55% less time vs the
team-reported baseline. Status: advanced live pilot, final ERP go-live in progress.

---

## 2. Executive mailbox triage

```mermaid
flowchart LR
    subgraph BEFORE2 [Before — manual]
        direction LR
        e1["Exec mailbox<br/>hundreds of emails"] --> e2["Read everything<br/>to find what matters"] --> e3["Forward, file,<br/>create tasks by hand"] --> e4["Important emails<br/>slip through"]
    end
```

```mermaid
flowchart LR
    subgraph AFTER2 [After — with the system]
        direction LR
        f1[Exec mailbox] --> f2["AI classifies<br/>& routes"] --> f3["Documents filed,<br/>tasks created"] --> f4[["HUMAN handles<br/>only what needs them"]]
    end
    style f4 fill:#2f6f4f,color:#fff
```

**Results:** 190+ hours saved, tracked operation by operation · 98.7% accuracy. Status: in
daily production.

---

## 3. Supplier invoicing (civil & geotechnical engineering)

```mermaid
flowchart LR
    subgraph BEFORE3 [Before — manual]
        direction LR
        c1["Supplier invoice arrives<br/>(PDF, email)"] --> c2["Type the data<br/>by hand"] --> c3["Reconcile against bank<br/>movements by hand"]
    end
```

```mermaid
flowchart LR
    subgraph AFTER3 [After — with the system]
        direction LR
        d1[Supplier invoice arrives] --> d2["OCR + AI<br/>extract the data"] --> d3[Records created] --> d4[Reconciliation proposed] --> d5[["HUMAN reviews<br/>before posting"]]
    end
    style d5 fill:#2f6f4f,color:#fff
```

**Results:** 323 operations · zero recorded errors. Status: in daily production.
