# REXX for z/OS

Practical laboratory track for learning and progressively applying **REXX on z/OS**, from basic TSO/E EXECs to batch execution and future ISPF-oriented automation.

This repository forms part of the broader **z/OS Engineering Laboratory** and focuses specifically on REXX as an automation and scripting layer around TSO/E, ISPF, JES2 and other z/OS services.

## Purpose

The objective is not only to learn REXX syntax, but to understand where REXX fits operationally in z/OS.

The progression starts with simple interactive EXECs and then expands toward different execution environments and, in later labs, reusable automation of repetitive mainframe tasks.

```text
TSO/E and ISPF
      |
      v
    REXX
      |
      +--> interactive EXECs
      +--> PDS member execution
      +--> JES2 batch execution
      +--> future ISPF services
      +--> future operational automation
```

## Environment

Current labs are built and validated on:

- z/OS ADCD 1.11
- Hercules
- TSO/E
- ISPF
- JES2
- REXX

The laboratory uses dedicated REXX and JCL libraries where required.

## Labs

| Lab | Title | Main focus | Status |
| --- | --- | --- | --- |
| 01 | [REXX Fundamentals and First TSO/E EXEC](labs/01-rexx-fundamentals-first-tso-exec/) | First REXX EXEC, `SAY`, `PULL`, variables, arithmetic and explicit TSO/E execution | Completed |
| 02 | [REXX Execution Methods](labs/02-rexx-execution-methods/) | ISPF Option 6, PDS `EX`, TSO execution and JES2 batch execution with `IRXJCL` | Completed / RC=0000 |

## Lab 01 — Fundamentals and First TSO/E EXEC

Lab 01 establishes the basic execution model.

A REXX member is stored in a PDS and executed explicitly under TSO/E. The program:

- requests interactive input with `PULL`;
- stores values in REXX variables;
- evaluates an arithmetic expression;
- displays output with `SAY`.

The validated EXEC performs a simple addition and demonstrates that the REXX environment is correctly installed and usable from TSO/E.

## Lab 02 — Execution Methods

Lab 02 deliberately reuses the EXEC from Lab 01 so that the focus remains on **execution context rather than new language syntax**.

The same EXEC is validated through:

- ISPF Option 6 / TSO Command Shell;
- the `EX` line command from a PDS member list;
- explicit TSO `EXEC`;
- JES2 batch execution through `IRXJCL`.

The batch path introduces the relationship between REXX and JCL:

```text
JCL
 |
 v
IRXJCL
 |
 +--> SYSEXEC   -> locates the REXX EXEC
 +--> SYSTSIN   -> supplies input
 +--> SYSTSPRT  -> captures output
 |
 v
JES2
```

The validated batch execution completed with `RC=0000`.

## Current Learning Path

```text
REXX fundamentals
       |
       v
TSO/E interactive execution
       |
       v
ISPF and PDS execution
       |
       v
JES2 / IRXJCL batch execution
       |
       v
control flow and reusable logic
       |
       v
ISPF services and operational automation
```

## Next Development

The next planned progression starts with REXX control-flow concepts already separated from Lab 02:

- `IF / THEN / ELSE`
- `SELECT / WHEN / OTHERWISE`

Later labs can progressively introduce:

- loops and reusable procedures;
- arguments and parsing;
- dataset processing;
- `EXECIO`;
- TSO command automation;
- ISPF services;
- reusable operator utilities;
- integration with other z/OS laboratory tracks where justified.

These items are roadmap targets and are not presented as completed work.

## Role in the z/OS Engineering Ecosystem

REXX provides the automation bridge between interactive z/OS operation and repeatable tooling.

Its architectural path in the wider laboratory is:

```text
MVS / TSO / ISPF
        |
        v
      REXX
        |
        v
ISPF and TSO services
        |
        v
Operational automation
```

This makes the repository complementary to:

- **MVS_TSO_ISPF** for terminal, TSO/E and ISPF fundamentals;
- **JCL_LABS** for JES2 and batch execution;
- **zos-batch-scheduler** for higher-level batch orchestration;
- the core **z/OS Engineering Laboratory** for system-level operational scenarios.

REXX should automate these environments rather than duplicate their individual subject matter.

## Engineering Methodology

Labs follow the same engineering cycle used across the wider laboratory:

```text
Build -> Execute -> Observe -> Diagnose -> Correct -> Validate -> Document
```

Each completed lab aims to preserve:

- the technical objective;
- execution steps;
- relevant source or JCL;
- observed result;
- evidence;
- security/publication review;
- references where applicable.

## Repository Structure

```text
Rexx/
├── README.md
└── labs/
    ├── 01-rexx-fundamentals-first-tso-exec/
    └── 02-rexx-execution-methods/
```

Individual labs contain their own detailed README, documentation, evidence, REXX source and supporting JCL where required.

---

## Part of the z/OS Engineering Laboratory

This repository is a specialized component of the broader **z/OS Engineering Laboratory** built on z/OS ADCD 1.11 / Hercules.

### Master architecture

https://github.com/P-dot/zos-adcd-hercules-engineering-lab

### Engineering methodology

```text
Build -> Execute -> Observe -> Diagnose -> Correct -> Validate -> Document
```
