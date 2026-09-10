# Execution and Results

## GRADE02

Command:

```text
TSO EXEC 'IBMUSER.REXX.EXEC(GRADE02)' EXEC
```

Validated cases:

```text
44 -> RESULT: FAIL
75 -> RESULT: PASS
```

## LEVEL02

Command:

```text
TSO EXEC 'IBMUSER.REXX.EXEC(LEVEL02)' EXEC
```

Validated cases:

```text
95 -> LEVEL: EXCELLENT
75 -> LEVEL: GOOD
55 -> LEVEL: PASS
25 -> LEVEL: FAIL
```

## Acceptance criteria
The lab passes only when both branches of `GRADE02` and every branch of `LEVEL02` produce the expected output.

**Result: PASS**
