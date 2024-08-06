---
layout: page
title: Mini Compiler for C++
description: Lexx and Yacc based C++ compiler built from scratch
img: assets/img/Designer.jpg
importance: 8
category: work
related_publications: false
---

[[Project Report]]({{ '/assets/pdf/MiniCompilerReport.pdf' | relative_url }})
[[Code]](https://github.com/Spielerr/Mini-Compiler-for-CPP)


### Summary
A project aimed at implementing a mini compiler which implements most language construct that C++ has to offer.  The compiler aims to cover the basic syntax, grammar, intermediate code generation and some optimisation techniques. This project was developed and implemented as part of the Compiler Design Course during my Undergraduate Study.


### Implementation Details
In terms of syntax, the following cases have been handled:
* Single line and multiline comments
* Incomplete multiline comments resulting in error message generation
* Recognition of multiple keywords like return, void, class, public, private, protected, int, float, double, bool, if, else, for, cin, cout, printf, scanf, break, continue, exit, string, char, true, false, etc.
* Recognition of valid identifiers (limited to maximum 32 characters) 
* Conversion of exponential notation floating point numbers (like 3.14E10) to standard decimal notation floating point numbers
* Preprocessor directives
* Functions (with prototype, declaration and definition)
* Single-line if construct
* Block if constructs
* Block if else construct
* Single line for construct
* Block for construct
* All arithmetic operators (+, -, *, /, %)
* All bitwise operators (&, |, ^)
* All logical and relational operators
* Multiple cases of Assignment expressions
* Jump statements

In terms of semantics, the following cases have been handled:
* Usage of undeclared variables
* Implicit type casting between primitive data types
* Incompatible type assignments
* Incompatible type operations
* Illegal redeclarations
* Occurence of break statements at only appropriate places (inside loop bodies)

### Design Strategy

#### Symbol Table Creation
The symbol table is implemented as a hash table for constant time ( O(1) ) access. Chaining is done to avoid collision. A unique hash function based on the name of the identifier is calculated and the location in the symbol table is determined based on that.

#### Intermediate Code Generation
A stack based approach is used to generate Three Address Code which is then converted to quadruple format as specified.

#### Code Optimization
The quadruple data structure created by the generation of intermediate code is taken as input for the optimization phase. This phase performs the different optimizations and gives the resulting quadruple data structure as the output. The following code optimizations have been performed:
1. Constant Folding
2. Constant Propagation
3. Common Subexpression Elimination
4. Strength Reduction

#### Error Handling
Some of the error handling strategies implemented are shown below. For a full comprehensive list, refer to the project report.
* Length of identifier greater than 32 characters
* Non terminating comments are flagged as erroneous
* Redeclaration of variables
* Usage of undefined functions
* Invalid assignment of incompatible types (Semantic error)
