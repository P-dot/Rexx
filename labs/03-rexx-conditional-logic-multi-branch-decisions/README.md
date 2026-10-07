# Lab 03 — REXX Conditional Logic and Multi-Branch Decisions

## Objective
Extend the REXX foundation from Labs 01 and 02 by validating binary and multi-branch decision logic under TSO/E.

## Environment
- z/OS ADCD 1.11 on Hercules
- TSO/E and ISPF
- EXEC library: `IBMUSER.REXX.EXEC`
- Members: `GRADE02`, `LEVEL02`

## Progression
This lab does not repeat the input/output and execution-method concepts already proven in Labs 01 and 02. It focuses on control flow.

### Part 1 — IF / THEN / ELSE
`GRADE02` implements a binary decision:

```text
score >= 50 -> PASS
otherwise   -> FAIL
```

Evidence validates both branches:

```text
44 -> RESULT: FAIL
75 -> RESULT: PASS
```

### Part 2 — SELECT / WHEN / OTHERWISE
`LEVEL02` extends the decision model to several ordered conditions:

```text
90-100 -> EXCELLENT
70-89  -> GOOD
50-69  -> PASS
0-49   -> FAIL
```

Evidence validates all four branches:

```text
95 -> LEVEL: EXCELLENT
75 -> LEVEL: GOOD
55 -> LEVEL: PASS
25 -> LEVEL: FAIL
```

## Why condition order matters
`SELECT` evaluates the `WHEN` clauses from top to bottom. Therefore the most restrictive threshold is tested first. A score of 95 must be evaluated against `>= 90` before the broader `>= 70` and `>= 50` conditions.

## Execution
Both EXECs are run from TSO/E using the established execution method:

```text
TSO EXEC 'IBMUSER.REXX.EXEC(GRADE02)' EXEC
TSO EXEC 'IBMUSER.REXX.EXEC(LEVEL02)' EXEC
```

## Validation
- `GRADE02`: both IF/ELSE paths exercised — PASS
- `LEVEL02`: all SELECT/WHEN/OTHERWISE paths exercised — PASS
- Overall lab status: **COMPLETED / PASS**

## Scope boundary
Loops, `DO`, parsing, functions/subroutines, `EXECIO`, external TSO commands and ISPF services are intentionally deferred to later labs.


---
### Continue learning

**Previous:** [02-rexx-execution-methods](../02-rexx-execution-methods/)  
**Course:** [Course home](../../README.md)  
**Next:** [04-rexx-numeric-processing-arithmetic-validation](../04-rexx-numeric-processing-arithmetic-validation/)  
**Academy:** [z/OS Engineering Academy](https://github.com/P-dot/P-dot/blob/main/docs/ACADEMY.md) · [Curriculum](https://github.com/P-dot/P-dot/blob/main/docs/CURRICULUM.md)
