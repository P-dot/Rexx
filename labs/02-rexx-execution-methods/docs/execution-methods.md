# Execution Methods

This lab follows the tutorial's execution-method sequence.

## ISPF Option 6
ISPF Option 6 provides a TSO command shell. The REXX EXEC was launched with:

```text
EXEC 'IBMUSER.REXX.EXEC(ADD2)' EXEC
```

The successful `12 + 8 = 20` result demonstrates interactive execution from the command shell.

## EX from member list
The `EX` line command was entered beside member `ADD2` in the partitioned data set member list. The successful `30 + 12 = 42` result demonstrates direct member execution through ISPF.

## TSO EXEC
The fully qualified `TSO EXEC` method had already been proven in Lab 01. Reusing that evidence avoids duplicating an already validated exercise.

## Batch
The fourth method changes execution context: JES2 processes a JCL job and `IRXJCL` provides the REXX batch environment. Details are documented in `batch-irxjcl.md`.
