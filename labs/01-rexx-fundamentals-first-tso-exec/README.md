# Lab 01 — REXX Fundamentals and First TSO/E EXEC

## Objective
Create and execute a first REXX EXEC under TSO/E on z/OS, using interactive input, variables, arithmetic and terminal output.

## Environment
- z/OS ADCD 1.11 on Hercules
- TSO/E and ISPF
- REXX EXEC library: `IBMUSER.REXX.EXEC`
- Member: `ADD2`

## Dataset
The lab library was allocated as a partitioned data set suitable for REXX EXEC members.

Observed allocation:
- DSORG: PO / PDS
- RECFM: FB
- LRECL: 80
- BLKSIZE: 3120
- Primary: 5 tracks
- Secondary: 2 tracks
- Directory blocks: 10

## Program
`ADD2` requests two numbers, stores them in REXX variables, calculates their sum and displays the result.

```rexx
/* REXX */
SAY 'ENTER FIRST NUMBER:'
PULL INP1
SAY 'ENTER SECOND NUMBER:'
PULL INP2
SUM = INP1 + INP2
SAY 'THE SUM OF TWO VALUES IS' SUM
```

## Execution
The EXEC was invoked explicitly from TSO/E:

```text
TSO EXEC 'IBMUSER.REXX.EXEC(ADD2)' EXEC
```

Test input:

```text
15
20
```

Observed result:

```text
THE SUM OF TWO VALUES IS 35
```

## Result
**PASS**

The evidence demonstrates:
- successful REXX library allocation;
- execution of a REXX member under TSO/E;
- interactive input with `PULL`;
- variable assignment;
- arithmetic expression evaluation;
- output with `SAY`;
- correct result for 15 + 20.

## Scope
This lab deliberately remains introductory. Dataset I/O with EXECIO, ISPF services, batch REXX, DB2/DSNREXX and more advanced automation are reserved for later labs.
