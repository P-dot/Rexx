# Lab 02 - REXX Execution Methods: ISPF, PDS, TSO and Batch

## Objective
Demonstrate the execution methods introduced by the tutorial sequence without repeating language concepts already validated in Lab 01.

## Environment
- z/OS ADCD 1.11 on Hercules
- TSO/E and ISPF
- JES2
- REXX
- EXEC library: `IBMUSER.REXX.EXEC`
- JCL library: `IBMUSER.REXX.JCL`

## Reused EXEC
The existing `ADD2` EXEC from Lab 01 is intentionally reused. This isolates the new learning objective: execution context.

## Execution methods validated

### 1. ISPF Option 6 / TSO Command Shell
Command:

```text
EXEC 'IBMUSER.REXX.EXEC(ADD2)' EXEC
```

Observed functional test:

```text
12 + 8 = 20
```

Status: **PASS**

### 2. EX from the PDS member list
`ADD2` was invoked with the `EX` line command from the member list.

Observed functional test:

```text
30 + 12 = 42
```

Status: **PASS**

### 3. TSO EXEC
The explicit TSO invocation was already demonstrated in Lab 01:

```text
TSO EXEC 'IBMUSER.REXX.EXEC(ADD2)' EXEC
```

It is referenced here rather than needlessly repeated.

Status: **PASS - previously evidenced in Lab 01**

### 4. Batch execution with IRXJCL
Member:

```text
IBMUSER.REXX.JCL(RUNADD2)
```

The job invokes `IRXJCL`, locates `ADD2` through `SYSEXEC`, supplies input through `SYSTSIN`, and captures REXX output through `SYSTSPRT`.

Observed JES2 result:

```text
RUNADD2 - STEP WAS EXECUTED - COND CODE 0000
```

Observed REXX result:

```text
ENTER FIRST NUMBER:
ENTER SECOND NUMBER:
THE SUM OF TWO VALUES IS 20
```

Status: **PASS / RC=0000**

## Result
**COMPLETED - RC=0000**

The lab proves that the same REXX EXEC can be launched interactively from ISPF/TSO and non-interactively through JES2 batch processing.

## Scope boundary
REXX language branching (`IF/THEN/ELSE`, `SELECT/WHEN/OTHERWISE`) is not part of this lab. Work already performed on those concepts continues in Lab 03.
