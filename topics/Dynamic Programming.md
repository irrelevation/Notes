# Dynamic Programming
The term "Dynamic Programming" was coined by Richard Bellmann in the 1950s. Its etymologie has political reasons as described in Bellmann's biography "Eye of the hurricane: An autobiography".

## TL;DR
Dynamix Programming = Recursion + Memoization

## SORTBT - A recipe for recursive algorithms
1. **S**ubproblems
2. **O**riginal Problem
3. **R**elate
4. **T**opological Order
5. **B**ase Case
6. **T**ime Complexity Analysis

## Bottom-Up Solutions - non rekursive transformations
1. Base Case
2. Loop over Topological Order
  2.1. Relate
3. return Original Problem

## Tips & Tricks
Problems regarding a sequence `X` can often be split into subproblems of
1. Suffixes X(i;) with |Suffixes| = O(n)
2. Prefixes X(;i) with |Prefixes| = O(n)
3. Substrings(i;j) with |Substrings| = O(n<sup>2</sup>)

## Resources
- [Richard Bellman on the Birth of Dynamic Programming](https://www.researchgate.net/publication/220243993_Richard_Bellman_on_the_Birth_of_Dynamic_Programming)
- [Bellmann, R. - The Theory Of Dynamic Programming](https://www.rand.org/content/dam/rand/pubs/papers/2008/P550.pdf)
- [MIT 6.006 - Introduction to Algorithms (2020), Lecture 15-18](https://ocw.mit.edu/courses/electrical-engineering-and-computer-science/6-006-introduction-to-algorithms-spring-2020/)
