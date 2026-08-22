# Execution and Verification

## 1. Allocate the EXEC library
The lab uses:

`IBMUSER.REXX.EXEC`

Observed characteristics:

```text
DSORG/Type       PDS
RECFM            FB
LRECL            80
BLKSIZE          3120
Primary tracks   5
Secondary tracks 2
Directory blocks 10
```

## 2. Create member
Create member:

`IBMUSER.REXX.EXEC(ADD2)`

and store the source from `rexx/ADD2.rexx`.

## 3. Execute
From ISPF/TSO:

```text
TSO EXEC 'IBMUSER.REXX.EXEC(ADD2)' EXEC
```

## 4. Functional test
Enter:

```text
15
20
```

Expected and observed result:

```text
THE SUM OF TWO VALUES IS 35
```

## 5. Acceptance criteria
The lab passes when the EXEC accepts both values and returns `35` without an execution error.

**Status: PASS**
