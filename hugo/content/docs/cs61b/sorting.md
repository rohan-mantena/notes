---
title: "Sorting"
weight: 6
---

why sorting? supports searching (binary, equal items, same val for property, what are my nearest neighbor, etc) -- see convex hull (cs 170)

*formal definition:* a soring algorithm (or sort) permutes (re-arranges) a sequece of elements to bring them into order, according to some total order.
    - a total order <see symbol> is :
        Total: All items can be compared with one another
        Reflexive: An item can be compared to itself
        Antisymmetric: x <= y AND y <= x IFF y == x
        Transitive: If x <= y and y <= z, then x must be <= z 
    - a sort that does not change the relative order of equivalent entries (compared to input) is called stable (consider sorting dictionary defs for same word, ignoring defition - unstable)

## Classifications 
- *Internal sorts* keeps all data in primary memory 
- *External sorts* process large amounts of data in batches, keeping what won't fit in secondary storage (in the old days, tapes)  
- *Comparison-based* sorting assumes only thing we know about keys is their order. 
- *Radix sorting* uses more info about key structure 
- *Insertion sorting* works by repeatedly inserting items at appropriate position in the sorted sequence being constructed 
- *Selection sorting* works by repeatedly selecting the next larger / smaller item in order and adding it to one of the sorted sequence being constructed 

- inversion are a measure of how sorted a list is ; 0 inversion = perfectly sorted , N*(N-1)/2 inversions = reversed


## Sorting by Insertion
- start with empty sequence of data, add each item from input, inserting it into the output sequecne at the right point
- good for small data sets,
    with vector or linked list, time for finding + inserting one item is at worst $\Theta(k)$, where k is the number of outputs so far => gives us $\Theta(N^{2})$ 
