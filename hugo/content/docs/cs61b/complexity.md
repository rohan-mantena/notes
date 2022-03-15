---
title: "Complexity and Algoritmic Analysis!"
weight: 2
---

https://joshhug.gitbooks.io/hug61b/content/chap8/chap82.html

# Considerations 
- in regards to an engineer, there are some crucial things to consider -> 
    - operational cost, the development costs, the maintenacne costs, and costs of failure 
    - is the program fast enough (purpose + input data factor in)
    - the space - memory, disk space - dephends on input data as well 
    - and, scale (as input gets big)

execution cost, that is, the cost of execution in terms of time and space/memory, is referred to as time complexity and space complexity 

we are currently focused on time complexity: 
    while there are multiple ways to take the cost measure (in time), the main one 61b focuses on is symbolic execution times => gives formula for the execution time as a function of input size and allows us to see the **shape** of the cost function 

# Asymptotic Cost 
- given that with inputs with relatively low size will not take too much memory or time, we choose to focus on the behavior of an algorithm for very large input, N. : asymptotic behavior
- when analyzing an algorithm;
    1.  consider the worst case only
    2. ignore mulitiplicative constants 
    3. ... 
    4. ...