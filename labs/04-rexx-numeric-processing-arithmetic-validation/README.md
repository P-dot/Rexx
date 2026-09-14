# Lab 04 — REXX Numeric Processing and Arithmetic Validation

## Objective
Validate numeric expression processing in REXX using the arithmetic operators introduced by the tutorial sequence, without repeating terminal I/O concepts already proven in earlier labs.

## Architecture V2 Classification

| Attribute | Classification |
|---|---|
| Primary domain | Automation and Modern Operations |
| Capability | Numeric expression processing |
| Lifecycle | Baseline → Operate → Validate |
| Maturity | M1 — Foundational |
| Integration | I0 — Standalone |
| Dependencies | Lab 01 fundamentals and established TSO/E execution |
| Validation status | VALIDATED |

## Environment
- z/OS ADCD 1.11 on Hercules
- TSO/E and ISPF
- `IBMUSER.REXX.EXEC(ARITH04)`

## Capability in Scope
`ARITH04` validates addition (`+`), subtraction (`-`), multiplication (`*`) and division (`/`). `SAY`, `PULL`, variables and TSO/E invocation are reused dependencies rather than new capabilities.

## Execution
```text
TSO EXEC 'IBMUSER.REXX.EXEC(ARITH04)' EXEC
```

## Validation Matrix

| Test | Input | Add | Subtract | Multiply | Divide | Result |
|---|---|---:|---:|---:|---:|---|
| A | `20 5` | 25 | 15 | 100 | 4 | PASS |
| B | `7 2` | 9 | 5 | 14 | 3.5 | PASS |

## Validation Summary
```text
Execution validation      : PASS
Arithmetic operator cover : 4/4
Integer arithmetic case   : PASS
Non-integer division case : PASS
Functional validation     : PASS
Overall status            : VALIDATED
```

## Scope Boundary
Division-by-zero handling, controlled exceptions, loops, parsing, functions, dataset I/O and ISPF services are deliberately deferred to later capabilities.

## Next Capability
Continue with the next distinct capability introduced by the tutorial sequence. New labs should advance an engineering capability rather than duplicate already validated syntax.
