# REXX — Ecosystem Integration

## Purpose

This document defines how `Rexx` participates in the IBM z/OS Engineering Portfolio, which capabilities are owned locally, and which integrations are evidenced elsewhere.

The repository provides the **REXX language and automation layer**.

```text
z/OS services and operator environments
              |
              v
             REXX
              |
              v
repeatable automation and control logic
```

Central rule:

```text
Use REXX to automate services provided elsewhere.
Do not transfer ownership of those services into the REXX track.
```

## Current Validated Boundary

```text
REXX fundamentals
      |
      +--> input / output
      +--> variables
      +--> arithmetic
      |
      v
execution contexts
      |
      +--> TSO/E
      +--> ISPF Option 6
      +--> PDS EX
      +--> JCL / IRXJCL / JES2
      |
      v
decision logic
      |
      +--> IF / THEN / ELSE
      +--> SELECT / WHEN / OTHERWISE
      |
      v
numeric expression processing
```

Dataset I/O, `EXECIO`, command automation, ISPF services and reusable operational utilities remain beyond the current local evidence boundary.

## Ownership

### Owned here

- REXX EXEC fundamentals;
- `SAY` and `PULL`;
- variables and expression evaluation;
- arithmetic operators;
- TSO/E execution;
- ISPF Option 6 and PDS `EX` execution;
- JCL/IRXJCL batch execution of REXX;
- binary and multi-branch conditional logic;
- numeric-processing validation;
- REXX automation patterns introduced by dedicated labs.

### Owned elsewhere

- TSO/E and ISPF fundamentals;
- general JCL syntax and JES2 engineering;
- scheduler state and scheduling policy;
- RACF administration;
- Communications Server networking;
- USS fundamentals;
- COBOL, Db2, VSAM, CICS, PL/I and HLASM domain semantics;
- core z/OS system engineering.

## Validated Local Labs

| Lab | Capability | Classification |
| --- | --- | --- |
| [01 — Fundamentals](../labs/01-rexx-fundamentals-first-tso-exec/README.md) | TSO/E EXEC, `SAY`, `PULL`, variables, arithmetic | **VALIDATED LOCALLY** |
| [02 — Execution Methods](../labs/02-rexx-execution-methods/README.md) | ISPF, PDS, TSO and IRXJCL/JES2 execution | **VALIDATED LOCALLY** |
| [03 — Conditional Logic](../labs/03-rexx-conditional-logic-multi-branch-decisions/README.md) | Binary and ordered multi-branch decisions | **VALIDATED LOCALLY** |
| [04 — Numeric Processing](../labs/04-rexx-numeric-processing-arithmetic-validation/README.md) | `+`, `-`, `*`, `/`, integer and non-integer cases | **VALIDATED LOCALLY** |

Lab 04 explicitly classifies its capability as `M1 — Foundational` and `I0 — Standalone`.

## MVS TSO/ISPF Relationship

```text
MVS_TSO_ISPF
      |
      v
TSO/E / ISPF
      |
      v
    REXX
```

The REXX labs prove execution within this environment; they do not re-own TSO/E or ISPF engineering.

Classification: **FOUNDATIONAL DEPENDENCY**

## JCL / JES2 Relationship

Lab 02 proves:

```text
JCL -> IRXJCL -> REXX -> RC=0000
```

The distinction is:

```text
REXX-through-IRXJCL execution
        -> VALIDATED LOCALLY

general JCL / JES2 engineering
        -> OWNED BY JCL_LABS / z/OS platform
```

Classification: **CROSS-DOMAIN FOUNDATION + LOCAL EXECUTION EVIDENCE**

## Scheduler Relationship

`zos-batch-scheduler` uses REXX for scheduler control logic. Target-repository evidence includes:

```text
ZSCHVAL
ZSCHORD
ZSCHEVL
```

Therefore this relationship is no longer merely planned:

```text
REXX
 |
 | implementation mechanism
 v
zos-batch-scheduler
 |
 +--> definition validation
 +--> ORDER processing
 +--> eligibility evaluation
 |
 v
scheduler runtime state
```

Ownership remains separated:

```text
REXX syntax / execution / automation mechanics
        -> Rexx

scheduler state machine / orchestration semantics
        -> zos-batch-scheduler
```

Classification: **VALIDATED IN TARGET REPOSITORY**

This does not turn scheduler capabilities into locally validated REXX labs.

## Consumes and Produces

Current labs consume TSO/E, ISPF interaction, partitioned datasets, JCL, JES2, `IRXJCL`, `SYSEXEC`, `SYSTSIN` and `SYSTSPRT`.

Current local evidence produces validated REXX source, interactive and batch execution evidence, conditional-control-flow evidence, numeric-processing evidence, and documented capability boundaries.

Future labs should progressively produce reusable automation components rather than isolated syntax demonstrations.

## Integration Matrix

| Integration | Classification | Evidence owner |
| --- | --- | --- |
| TSO/E -> REXX | **VALIDATED LOCALLY** | Rexx Lab 01 |
| ISPF/PDS -> REXX | **VALIDATED LOCALLY** | Rexx Lab 02 |
| JCL/IRXJCL -> REXX | **VALIDATED LOCALLY** | Rexx Lab 02 |
| JES2 batch completion of REXX | **VALIDATED LOCALLY** | Rexx Lab 02 |
| REXX conditional logic | **VALIDATED LOCALLY** | Rexx Lab 03 |
| REXX numeric processing | **VALIDATED LOCALLY** | Rexx Lab 04 |
| REXX used by scheduler control logic | **VALIDATED IN TARGET REPOSITORY** | zos-batch-scheduler |
| REXX -> ISPF services | **PLANNED** | Future REXX lab |
| REXX -> dataset automation / EXECIO | **PLANNED** | Future REXX lab |
| REXX -> broader operational utilities | **CROSS-DOMAIN / REQUIRES EVIDENCE** | Future integration |

## Learning Progression

```text
Lab 01 fundamentals
       |
       v
Lab 02 execution contexts
       |
       v
Lab 03 decision logic
       |
       v
Lab 04 numeric processing
       |
       v
next distinct language capability
       |
       v
dataset / command automation
       |
       v
ISPF services
       |
       v
reusable operational tooling
```

## Cross-Repository Targets

Dataset automation, TSO command automation and ISPF services remain **PLANNED** until dedicated evidence exists.

Scheduler implementation is different: REXX is already used by validated scheduler control programs, so that relationship is **VALIDATED IN TARGET REPOSITORY** while scheduler behavior remains owned by `zos-batch-scheduler`.

## Validation Model

| State | Meaning |
| --- | --- |
| `VALIDATED LOCALLY` | Proven by evidence in this repository |
| `VALIDATED IN TARGET REPOSITORY` | REXX participates in a capability proven by another repository |
| `CROSS-DOMAIN / REQUIRES EVIDENCE` | Integration is justified but not completely proven |
| `PLANNED` | Roadmap capability, not completed work |

## Architecture V2

Primary architectural domain:

```text
Automation and Modern Operations
```

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

Levels apply to specific evidenced capabilities, not automatically to the entire repository.

## Engineering Method

```text
BUILD -> EXECUTE -> OBSERVE -> DIAGNOSE -> CORRECT -> VALIDATE -> DOCUMENT
```

Future automation evidence should make clear the automated operation, the underlying z/OS service owner, the REXX control logic, the observed result, the tested boundary, and ownership of the final operational semantics.

## Publication Security

Before publication, inspect REXX source, JCL, spool output, ISPF captures and screenshots for credentials, secrets, private IP addresses, MAC addresses, adapter identifiers, unnecessary hostnames, local workstation paths, terminal/session identifiers and unrelated system details.

## Repository Navigation

```text
IBM z/OS Engineering Portfolio
              |
              v
             Rexx
          /    |    \
         v     v     v
      Labs  Ecosystem  Related domains
       |                 |
       v                 +--> MVS_TSO_ISPF
    Evidence             +--> JCL_LABS
                         +--> zos-batch-scheduler
                         +--> Core z/OS Engineering
```

## Continue Through the Portfolio

- [Repository README](../README.md)
- [Lab 01 — Fundamentals](../labs/01-rexx-fundamentals-first-tso-exec/README.md)
- [Lab 02 — Execution Methods](../labs/02-rexx-execution-methods/README.md)
- [Lab 03 — Conditional Logic](../labs/03-rexx-conditional-logic-multi-branch-decisions/README.md)
- [Lab 04 — Numeric Processing](../labs/04-rexx-numeric-processing-arithmetic-validation/README.md)
- [MVS TSO/ISPF](https://github.com/P-dot/MVS_TSO_ISPF)
- [JCL Engineering Labs](https://github.com/P-dot/JCL_LABS)
- [z/OS Batch Scheduler](https://github.com/P-dot/zos-batch-scheduler)
- [Master z/OS Engineering Laboratory](https://github.com/P-dot/zos-adcd-hercules-engineering-lab)
- [IBM z/OS Engineering Portfolio](https://github.com/P-dot/P-dot)
