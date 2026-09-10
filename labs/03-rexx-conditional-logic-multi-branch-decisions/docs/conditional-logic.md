# Conditional Logic

## IF / THEN / ELSE
`IF` evaluates a condition. When the expression is true, the `THEN` instruction is selected; otherwise the `ELSE` path is selected.

In `GRADE02`, the threshold is 50. The lab deliberately tests one value below and one above the threshold so both execution paths are evidenced.

## SELECT / WHEN / OTHERWISE / END
`SELECT` is used when more than two outcomes are required. Each `WHEN` supplies a condition, `OTHERWISE` provides the fallback path, and `END` closes the selection structure.

`LEVEL02` uses descending thresholds so that the first matching branch represents the correct classification.

## Engineering validation
A control-flow program is not considered validated merely because one input succeeds. This lab exercises every defined branch so the evidence demonstrates the complete decision structure.
