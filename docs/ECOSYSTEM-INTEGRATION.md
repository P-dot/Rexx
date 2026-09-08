# REXX Ecosystem Integration

## Role

This repository provides the REXX automation layer within the broader z/OS Engineering Laboratory.

Its purpose is to move from interactive TSO/E scripting toward reusable operational automation without duplicating the responsibilities of the repositories that provide the underlying services.

REXX sits between operator-facing environments such as TSO/E and ISPF and higher-level operational workflows such as JES2 batch processing, scheduler-driven execution and future ISPF tooling.

```text
MVS / TSO / ISPF
        |
        v
      REXX
      /   \
     v     v
   JCL    ISPF services
     |        |
     v        v
   JES2    Automation
      \      /
       v    v
  z/OS operational workflows
```

## Upstream Dependencies

### MVS_TSO_ISPF

Provides the operator-facing environment in which REXX EXECs are edited, launched and later integrated with ISPF services.

```text
MVS_TSO_ISPF -> REXX
```

Status: **Validated foundation**

### JCL_LABS

Provides the batch-execution model used when REXX is launched through JCL and JES2.

```text
JCL_LABS -> IRXJCL -> REXX
```

Status: **Validated in REXX Lab 02**

### z/OS Engineering Laboratory

Provides the common ADCD/Hercules system context, engineering methodology and cross-repository architecture.

Status: **Active architectural dependency**

## Downstream Consumers

### zos-batch-scheduler

Future scheduler labs can use REXX for control logic, operator utilities, metadata handling and execution support where REXX is technically appropriate.

```text
REXX -> zos-batch-scheduler
```

Status: **Planned integration**

### ISPF-oriented operational tooling

Future REXX labs can provide command wrappers, utilities and repeated operator workflows through ISPF services.

```text
REXX -> ISPF services -> operator automation
```

Status: **Planned**

### Cross-repository automation

REXX can later simplify repeated tasks around datasets, batch jobs, diagnostics and other z/OS services exposed by the wider lab ecosystem.

Status: **Planned**

## Consumes

The REXX track currently consumes:

- TSO/E command execution;
- ISPF interaction;
- partitioned datasets for EXEC storage;
- JCL;
- JES2;
- `IRXJCL`;
- `SYSEXEC`;
- `SYSTSIN`;
- `SYSTSPRT`.

## Produces

The repository currently produces:

- validated REXX EXEC source;
- interactive TSO/E execution examples;
- PDS member execution evidence;
- JES2 batch execution through `IRXJCL`;
- documented execution methods;
- evidence and validation results.

Future labs are expected to produce reusable automation components rather than standalone demonstrations only.

## Validated Cross-Repository Paths

### Interactive execution path

```text
MVS_TSO_ISPF
     |
     v
TSO/E / ISPF
     |
     v
REXX EXEC
```

Validated by REXX Lab 01 and Lab 02.

### Batch execution path

```text
JCL_LABS concepts
      |
      v
     JCL
      |
      v
   IRXJCL
      |
      v
   REXX EXEC
      |
      v
    JES2
```

Validated in REXX Lab 02 with successful batch completion and `RC=0000`.

## Planned Cross-Repository Paths

The following are architectural targets and must not be interpreted as completed integrations.

### ISPF automation track

```text
MVS_TSO_ISPF
     |
     v
   REXX
     |
     v
ISPF services
     |
     v
Operator automation
```

### Scheduler automation track

```text
REXX
 |
 v
zos-batch-scheduler
 |
 v
JCL / JES2
 |
 v
Batch workloads
```

### Operational utility track

```text
REXX
 |
 +--> dataset automation
 +--> TSO command automation
 +--> operator utilities
 +--> job-control helpers
 +--> future cross-repository workflows
```

## Integration Status

| Integration | Status | Evidence |
| --- | --- | --- |
| TSO/E -> REXX | Validated | Lab 01 |
| ISPF/PDS execution -> REXX | Validated | Lab 02 |
| JCL/JES2 -> IRXJCL -> REXX | Validated | Lab 02 / RC=0000 |
| REXX -> ISPF services | Planned | Future labs |
| REXX -> zos-batch-scheduler | Planned | Future integration |
| REXX -> cross-repository operations | Planned | Future integration |

## Scope Boundaries

This repository owns REXX language usage and REXX-based automation patterns.

It does **not** replace:

- `MVS_TSO_ISPF` for TSO/E and ISPF fundamentals;
- `JCL_LABS` for general JCL and JES2 batch concepts;
- `zos-batch-scheduler` for scheduling policy, active-job state and orchestration;
- RACF repositories for security administration;
- Communications Server repositories for TCP/IP services;
- the core z/OS Engineering Laboratory for system-level engineering.

The integration rule is:

```text
Use REXX to automate services provided elsewhere.
Do not duplicate the service itself inside the REXX track.
```

## Development Direction

```text
REXX fundamentals
       |
       v
TSO/E execution
       |
       v
ISPF / PDS execution
       |
       v
IRXJCL / JES2 batch
       |
       v
control flow
       |
       v
dataset and command automation
       |
       v
ISPF services
       |
       v
cross-repository operational tooling
```

Near-term work should remain focused on building the REXX capabilities required for later integrations rather than prematurely coupling the repository to multiple external tracks.

## Engineering and Publication Rules

Cross-repository work should follow the common engineering cycle:

```text
Build -> Execute -> Observe -> Diagnose -> Correct -> Validate -> Document
```

Before publication:

- validate technical results;
- preserve evidence where appropriate;
- distinguish validated functionality from roadmap targets;
- avoid publishing host-side network details, credentials or other sensitive information;
- use short-lived integration branches and merge completed work into `main`.

## Master Architecture

The broader ecosystem architecture is maintained in:

https://github.com/P-dot/zos-adcd-hercules-engineering-lab
