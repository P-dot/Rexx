# REXX for z/OS — Automation Engineering

Hands-on engineering track for learning and progressively applying **REXX on z/OS**, from TSO/E EXEC fundamentals to batch execution and reusable operational automation.

> **Validated scope:** Labs 01–04
> **Primary role:** REXX language capability and z/OS automation patterns
> **Current boundary:** foundational language, decision logic, numeric processing and multiple execution contexts
> **Architecture:** Portfolio Navigation V2 / Engineering Control

## Navigate

- [Lab 01 — REXX Fundamentals and First TSO/E EXEC](labs/01-rexx-fundamentals-first-tso-exec/README.md)
- [Lab 02 — REXX Execution Methods](labs/02-rexx-execution-methods/README.md)
- [Lab 03 — Conditional Logic and Multi-Branch Decisions](labs/03-rexx-conditional-logic-multi-branch-decisions/README.md)
- [Lab 04 — Numeric Processing and Arithmetic Validation](labs/04-rexx-numeric-processing-arithmetic-validation/README.md)
- [Ecosystem Integration](docs/ECOSYSTEM-INTEGRATION.md)
- [MVS TSO/ISPF](https://github.com/P-dot/MVS_TSO_ISPF)
- [JCL Engineering Labs](https://github.com/P-dot/JCL_LABS)
- [z/OS Batch Scheduler](https://github.com/P-dot/zos-batch-scheduler)
- [Master z/OS Engineering Laboratory](https://github.com/P-dot/zos-adcd-hercules-engineering-lab)
- [IBM z/OS Engineering Portfolio](https://github.com/P-dot/P-dot)

## Repository Role

This repository owns **REXX language usage and REXX-based automation capability on z/OS**.

```text
TSO/E + ISPF
     |
     v
    REXX
     |
     +--> interactive EXECs
     +--> PDS member execution
     +--> conditional logic
     +--> numeric processing
     +--> JCL / IRXJCL batch execution
     +--> future dataset and command automation
     +--> future ISPF services
```

REXX is an automation layer. It consumes services provided by other z/OS domains rather than taking ownership of those domains.

## Validated Labs

| Lab | Capability | Evidence state |
| --- | --- | --- |
| [01](labs/01-rexx-fundamentals-first-tso-exec/README.md) | First TSO/E EXEC, `SAY`, `PULL`, variables and arithmetic | **VALIDATED LOCALLY** |
| [02](labs/02-rexx-execution-methods/README.md) | ISPF Option 6, PDS `EX`, TSO `EXEC`, JES2 batch through `IRXJCL` | **VALIDATED LOCALLY — RC=0000** |
| [03](labs/03-rexx-conditional-logic-multi-branch-decisions/README.md) | `IF / THEN / ELSE` and `SELECT / WHEN / OTHERWISE` | **VALIDATED LOCALLY** |
| [04](labs/04-rexx-numeric-processing-arithmetic-validation/README.md) | Numeric expressions: `+`, `-`, `*`, `/` | **VALIDATED LOCALLY** |

## Current Capability Path

```text
Lab 01: fundamentals / TSO/E
          |
          v
Lab 02: execution contexts
          |
          +--> ISPF Option 6
          +--> PDS EX
          +--> TSO EXEC
          +--> JCL / IRXJCL / JES2
          |
          v
Lab 03: conditional decision logic
          |
          v
Lab 04: numeric expression processing
```

Each lab advances a distinct capability instead of repeating an already validated execution path.

## Validated Execution Contexts

The interactive path is:

```text
TSO/E / ISPF
     |
     v
 REXX EXEC
```

Lab 02 also proves non-interactive execution:

```text
JCL
 |
 v
IRXJCL
 |
 +--> SYSEXEC   -> REXX EXEC library
 +--> SYSTSIN   -> input
 +--> SYSTSPRT  -> output
 |
 v
JES2
```

Observed result: `RUNADD2 - STEP WAS EXECUTED - COND CODE 0000`.

This proves the REXX batch execution path. General JCL and JES2 engineering remain owned by `JCL_LABS` and the z/OS platform domains.

## Language Capabilities Validated So Far

```text
Input / output       SAY, PULL
Variables            assignment, expression use
Arithmetic           +, -, *, /
Decision logic       IF / THEN / ELSE
                     SELECT / WHEN / OTHERWISE
Execution            TSO EXEC, ISPF Option 6, PDS EX, IRXJCL batch
```

Loops, parsing, functions, `EXECIO`, dataset automation and ISPF services are not presented as completed work.

## Automation Boundary

REXX can implement control logic in other repositories without transferring ownership of that repository's semantics to this one.

A current portfolio example is `zos-batch-scheduler`:

```text
REXX capability
      |
      v
scheduler implementation
      |
      +--> ZSCHVAL
      +--> ZSCHORD
      +--> ZSCHEVL
      |
      v
scheduler state / orchestration
```

Ownership remains:

```text
REXX language and automation mechanics
        -> Rexx

scheduler state machine and scheduling semantics
        -> zos-batch-scheduler
```

Scheduler capabilities are therefore **validated in the target repository**, not claimed as locally validated REXX labs.

## Domain Relationships

- **MVS_TSO_ISPF** — foundational TSO/E and ISPF environment consumed by REXX.
- **JCL_LABS** — broader JCL/JES2 batch foundation consumed by the IRXJCL path.
- **zos-batch-scheduler** — uses REXX as an implementation mechanism; scheduler semantics remain owned there.
- **Core z/OS Engineering** — provides the ADCD/Hercules platform and common system context.

See [Ecosystem Integration](docs/ECOSYSTEM-INTEGRATION.md) for the detailed ownership and evidence model.

## Next Development

Planned distinct REXX capabilities include:

- loops and `DO`;
- parsing and arguments;
- functions and subroutines;
- dataset processing and `EXECIO`;
- TSO command automation;
- ISPF services;
- reusable operator utilities;
- justified cross-repository automation.

These are roadmap targets, not completed capabilities.

## Validation Model

```text
VALIDATED LOCALLY
    proven by evidence in this repository

VALIDATED IN TARGET REPOSITORY
    REXX participates in a capability proven elsewhere

CROSS-DOMAIN / REQUIRES EVIDENCE
    architecture exists but complete integration is not yet proven

PLANNED
    roadmap capability, not completed work
```

## Engineering Method

```text
BUILD -> EXECUTE -> OBSERVE -> DIAGNOSE -> CORRECT -> VALIDATE -> DOCUMENT
```

Completed labs preserve the objective, implementation, execution path, observed result, evidence and scope boundary.

## Architecture V2

Portfolio lifecycle:

```text
Discover -> Baseline -> Configure -> Operate -> Observe
        -> Diagnose -> Recover -> Improve -> Automate -> Integrate
```

Maturity:

```text
M0 Exploratory -> M1 Foundational -> M2 Operational
               -> M3 Resilient -> M4 Automated -> M5 Integrated
```

Integration:

```text
I0 Standalone -> I1 Cross-component -> I2 Cross-repository -> I3 Production-like
```

Maturity is capability-scoped. Lab 04 explicitly classifies numeric expression processing as `M1 — Foundational` and `I0 — Standalone`.

## Repository Structure

```text
Rexx/
├── README.md
├── docs/
│   └── ECOSYSTEM-INTEGRATION.md
└── labs/
    ├── 01-rexx-fundamentals-first-tso-exec/
    ├── 02-rexx-execution-methods/
    ├── 03-rexx-conditional-logic-multi-branch-decisions/
    └── 04-rexx-numeric-processing-arithmetic-validation/
```

Each lab owns its detailed technical narrative and evidence. The root README remains the repository landing page.

## Publication Security

Before publication, review source, JCL, spool output, terminal captures and screenshots for credentials, secrets, private network information, MAC addresses, adapter identifiers, unnecessary hostnames, local workstation paths and terminal/session identifiers.

## Continue Through the Portfolio

```text
MVS_TSO_ISPF
      |
      +------> REXX <------ JCL_LABS
                  |
                  +--> operational automation
                  +--> zos-batch-scheduler
                  +--> future ISPF / dataset tooling
```

- [Ecosystem Integration](docs/ECOSYSTEM-INTEGRATION.md)
- [MVS TSO/ISPF](https://github.com/P-dot/MVS_TSO_ISPF)
- [JCL Engineering Labs](https://github.com/P-dot/JCL_LABS)
- [z/OS Batch Scheduler](https://github.com/P-dot/zos-batch-scheduler)
- [Master z/OS Engineering Laboratory](https://github.com/P-dot/zos-adcd-hercules-engineering-lab)
- [IBM z/OS Engineering Portfolio](https://github.com/P-dot/P-dot)


---

## z/OS Engineering Academy

**Academy role:** Automation School — turn repeatable operator and developer workflows into programs.

[Start the Academy](https://github.com/P-dot/P-dot/blob/main/docs/ACADEMY.md) · [Course Catalog](https://github.com/P-dot/P-dot/blob/main/docs/COURSES.md) · [Curriculum Graph](https://github.com/P-dot/P-dot/blob/main/docs/CURRICULUM.md) · [Cross-Domain Relationships](https://github.com/P-dot/P-dot/blob/main/docs/RELATIONSHIPS.md)

> Learn the concept → execute the lab → interpret the evidence → understand the subsystem boundary → continue to the next connected course.
