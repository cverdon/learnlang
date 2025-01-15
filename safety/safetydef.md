# Language Safety

Objective is to better understand and define the taxonomy of language safety in order to be able to make comparisons between languages and understand the mitigations that need to put in place for different safety requirement scenarios.

What is software security? (IEEE definitions)

- Degree to which software protects information and system resources, providing access only to authorized users as intented
- Encompasses practices like threat modeling, secure coding, security testing, and vulnerability management applied throughout the software development life cycle.
- Goal to prevent, detect, and recover from attacks and unintended weaknesses that could compromise confidentiality, integrity and availability
- Software security seeks to build in protection proactively rather than reacting to threats

**Functional safety** defined as the systematic process used to ensure that failure doesn't occur

- Functional safety
  - Security
    - Type safety
    - Memory safety
    - Thread safety

With rare exceptions, all vulnerabilities can be thought of as input validation failures.

## Memory Leaks

Memory leaks are undesirable, however not considered a memory safety issue from a theoretical standpoint:

- Short-lived applications can intentionally leak memory with the intent that the OS will clean up after completion (ex. terminal app)
- Leaking memory will not result in misinterpretting that memory and thus will not cause a security issue.

## Taxonomy

| Type                       | Example                      |
|:---------------------------|:-----------------------------|
|- Memory safety             |                              |
|  1. Spacial memory safety  | No out of bounds             |
|  2. Temporal memory safety | - No uninitialized reads     |
|                            | - No use after free          |
|                            | - iterator invalidation      |
|  3. Undefined behavior     |                              |
|- Thread safety             | Data race condition          |
|- Type safety               | No interpreting as wrong type|
|- Memory leak               | Not freeing after done       |

## Evaluations

"All safety features must be on by default or they will not be used."

| Evaluation                          | Example | Color |
|:------------------------------------|:------------|:---------|
| 1. Built-in compile-time error      | | Green |
| 2. Compiler flag                    | like C -D_GLIBCXX_ASSERTIONS for range checking | Light green |
| 3. Compile-time tooling             | like static analysis        | Yellow |
| 4. Run-time error                   | assert, exception, panic    | Orange |
| 5. Defensive programming            | code must handle this       | Red |

## Reference

- [Memory Safety: Rust vs. C - Robert Seacord - NDC TechTown 2024](https://youtu.be/YofBgJ2zpBs?si=XFiFfJuVlgRLRl7M)
