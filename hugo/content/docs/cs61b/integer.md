---
title: "Integers"
weight: 4    
---
## Integers Types and Literals 
the range of values for signed types -2^N .. 2^N - 1 (there is 1 less value for posivite values to account for 0)
the range of values for unsigned types 0 .. 2^N - 1 

(N is the number of bits)

- how do we handle 'overflow', numbers that are so large they are outside the range, java employs modular arithmetic ('wrapping around')

- if some result of an arithmetic subexpression is supposed to be of type T; then we compute the mathematical value, x, which yields some number x', that is in the range of T. x' = x modulo 2^N   
    - x - x' is a multiple of 2^N

- 