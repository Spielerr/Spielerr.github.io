---
layout: page
title: Cross-Platform Transpilation of Packet-Processing Programs using Program Synthesis
description: with compiler optimisations and switch hardware constraint handling
img: assets/img/switch.jpeg
importance: 1
category: work
related_publications: false
---

### Abstract

The diversity of programmable switch hardware architectures and associated domain-specific languages poses significant challenges for developers who need to implement and test their programs across multiple platforms. This research proposes a novel approach to address this issue by designing and implementing a transpiler that can automatically convert switch programs from one hardware architecture to another, bridging the gap between different programming languages and hardware constraints.

The proposed transpiler leverages program synthesis techniques to aid the conversion process. It follows a three-stage pipeline: (1) converting the source program to an intermediate representation (IR), (2) using program synthesis to transform the source IR into the target IR while considering target language constraints and hardware architecture constraints, and (3) converting the target IR to the final program. This approach reduces the need for one-to-one mappings between every language and hardware pair, making the transpilation process more scalable and maintainable.

The research focuses on addressing the complexities of the parser stage in switch programs, formulating hardware constraints and using program synthesis to generate target parsers that satisfy these constraints while preserving program semantics. Subsequently, the approach will be extended to handle the pipeline stage of PISA switches, incorporating additional hardware constraints and language-specific constructs.

The expected outcomes include an implemented transpiler capable of converting switch programs across hardware architectures, performance metrics and semantic checking of transpiled programs against benchmarks, and a research paper detailing the transpilation approach, implementation, and results. The proposed transpiler will contribute to efficient development and deployment cycles in the networking industry by enabling cross-platform testing and informed design choices.


### Introduction

* Motivation: The networking industry is witnessing a rapid proliferation of programmable switch hardware architectures and associated domain-specific languages (DSLs). However, the diversity of these languages and architectures poses significant challenges for developers, who often need to implement and test their switch programs across multiple platforms. This process is time-consuming and error-prone, hindering efficient development and deployment cycles.

* Problem Statement: This research aims to design and implement a transpiler that can automatically convert switch programs written for one hardware architecture to another, addressing the differences in programming languages and hardware constraints. The transpilation process will be aided by leveraging program synthesis techniques, which can automatically generate target programs that adhere to the specified constraints and semantics.

* Proposed Approach: The proposed approach involves a three-stage pipeline: (1) converting the source program to an intermediate representation (IR), (2) using program synthesis to transform the source IR into the target IR while considering the target language constraints and hardware architecture constraints, and (3) converting the target IR to the final target program. This approach reduces the need for one-to-one mappings between every language and hardware pair, making the transpilation process more scalable and maintainable.

### Background and Literature Review

* Overview of switch programming languages (e.g., NPL, P4) and hardware architectures (e.g., Trident 4, Tofino), their characteristics, and differences.

* Program synthesis techniques: Provide an in-depth analysis of existing program synthesis approaches, including enumerative synthesis, constraint-based synthesis, and machine learning-based synthesis, highlighting their strengths and limitations in the context of switch program transpilation.

* Existing work and limitations: Discuss previous efforts in switch program transpilation, if any, and their limitations in addressing the complexities of handling diverse programming languages, hardware constraints, and scalability.

### Methodology

* Three-stage pipeline:
1. Source program to IR: Develop a parser and converter to translate the source program into a language-agnostic IR representation, capturing the program's semantics and structure.
2. IR to target IR (using program synthesis): Leverage program synthesis techniques to transform the source IR into the target IR, considering the target language syntax, semantics, and hardware constraints (e.g., bit length comparisons, variable limitations, table entries). Explore and evaluate different synthesis approaches, such as enumerative synthesis, constraint-based synthesis, and machine learning-based synthesis, for their suitability in this context.
3. Target IR to target program: Develop a code generator to convert the target IR into the final target program, adhering to the target language's syntax and semantics.

<div class="row">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.liquid loading="eager" path="assets/img/ir.png" title="example image" class="img-fluid rounded z-depth-1" %}
    </div>
</div>
<div class="caption">
    3-stage pipeline
</div>

* Handling parser complexity: As an initial step, focus on addressing the complexities in the parser stage of switch programs. Identify and formulate hardware constraints relevant to the parser stage, such as maximum bit length comparisons, maximum number of variables that can be compared inside transition statements, and maximum table entries. Use program synthesis techniques to generate target parsers that satisfy these constraints while preserving the original program's semantics.

* Extending to pipeline stage: After successfully addressing the parser stage, extend the transpilation approach to handle the complexities of the pipeline stage in switch programs. This stage may involve additional hardware constraints and language-specific constructs, requiring further refinement of the synthesis techniques and IR representations.


### Expected Outcomes and Evaluation:
* Implemented transpiler capable of converting switch programs across hardware architectures: Develop a robust and scalable transpiler that can automatically convert switch programs from one target hardware to another, addressing differences in programming languages and hardware constraints.

* Performance metrics and semantic checking of transpiled programs against benchmarks: Evaluate the transpiled programs using a comprehensive set of benchmarks, measuring performance metrics such as execution time, resource utilization, and correctness. Perform semantic checking to ensure that the transpiled programs preserve the original program's behavior and semantics.

* Research paper detailing the transpilation approach, implementation, and results: Publish a research paper in a relevant conference or journal, describing the proposed transpilation approach, implementation details, experimental results, and analysis. The paper will contribute to the body of knowledge in the field of program synthesis and network programming.
