# Numeric Processing

The tutorial arithmetic block is implemented as one focused Architecture V2 capability.

```rexx
ADDRES = NUM1 + NUM2
SUBRES = NUM1 - NUM2
MULRES = NUM1 * NUM2
DIVRES = NUM1 / NUM2
```

`PULL NUM1 NUM2` supplies two values in one terminal input. Input handling itself is not a new capability because it was established previously.

## Test A
Input `20 5` produced addition 25, subtraction 15, multiplication 100 and division 4.

## Test B
Input `7 2` produced addition 9, subtraction 5, multiplication 14 and division 3.5.

The second case intentionally validates division where the result is not an integer. Together the two executions cover every arithmetic operator implemented by the EXEC.
