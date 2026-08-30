# Batch REXX with IRXJCL

## Flow

```text
JES2
  |
  +-- RUNADD2
        |
        +-- PGM=IRXJCL
              |
              +-- SYSEXEC -> IBMUSER.REXX.EXEC
              |              |
              |              +-- ADD2
              |
              +-- SYSTSIN  -> 12, 8
              |
              +-- SYSTSPRT -> REXX output
```

## JCL roles

- `PGM=IRXJCL` starts REXX in batch.
- `PARM='ADD2'` identifies the EXEC to run.
- `SYSEXEC` points to the library containing `ADD2`.
- `SYSTSPRT` captures REXX output.
- `SYSTSIN` provides the two input values without an interactive terminal.

## Validation
JES2 reported:

```text
RUNADD2 - STEP WAS EXECUTED - COND CODE 0000
```

`SYSTSPRT` showed:

```text
ENTER FIRST NUMBER:
ENTER SECOND NUMBER:
THE SUM OF TWO VALUES IS 20
```

This validates both job completion and application-level behavior.
