# Proposal: AI-Assisted Static Code Analysis for the Linux Kernel

## Motivation

Safety-critical systems built on top of the Linux kernel require evidence
that the kernel code meets coding standards such as MISRA C and
CERT-C. Running a static analysis tool like Coverity on the kernel
produces hundreds of thousands of violations — far too many for manual
review. The vast majority of these violations are technically correct per
the standard but cannot lead to a failure in practice. Identifying the small fraction that
represent real risks requires deep understanding of the code context:
type definitions, macro expansion chains, caller/callee relationships,
and kernel-specific patterns.

This proposal addresses the need for a scalable, auditable system that
classifies each violation as **deviated** (cannot cause a failure),
**potential-issue** (may cause a failure), or **unknown** (insufficient
evidence), with traceable reasoning for every decision.

## Proposal

Build an automated pipeline that processes static analysis
results for the Linux kernel and classifies each violation using a
combination of deterministic fast-path checks, script-based context
collection, and LLM-assisted analysis. The system is organized around
a per-rule analyzer architecture with the following stages:

### 1. Ingestion

Import static code analysis violations into a common ViolationDB (implemented as a MongoDB). Each violation
becomes a document with file path, line number, rule number, rule type
(Rule or Directive) and other properties.

### 2. Context Collection

For each non-fast-path violation, a rule-specific context collector
script gathers the source code evidence needed for classification.

### 3. Classification

The collected context is sent to an LLM with a rule-specific
classification prompt. The prompt instructs the LLM to evaluate only the
current implementation — not hypothetical future changes. The LLM returns
a classification (deviated/potential-issue/unknown), reasoning and other information.

### 4. Mitigation

Violations that are classified as Potential-issue require a mitigation. A violation can
be mitigated in one or more ways. Possible mitigations are:

* Issue an AoU that prevents the system from triggering the potential issue
* File a deviation record
* Prove that the potential issue is covered by safety mechanisms
* Fix the issue

Classifications are the result of the violation and the Linux kernel environment in which
it is found. Mitigations are done differently by each user of the system. Some may mitigate
a violation by fixing it, while others may issue an AoU for the same violation.

## Expected impact

The proposed system handles all static code analysis violations for the Linux kernel. The system
allows its users to claim full compliance with the ISO 26262 requirements for use of language subsets
and unit implementation guidelines.

The system can be used also for other pre-existing and complex software, such as glibc.

The system can be used by any member of ELISA and all can contribute to it by:

* Developing analyzers for rules
* Adding analyzers for additional rule sets beyond MISRA and CERT-C
* Contributing to Tool classification & qualification efforts of the system


## Additional considerations

The system classifies violations that are discovered by static code analyzers,
free (like Coccinelle, clang-tidy) or commercial.

The system requires a MongoDB for storing violations and all the evidence
gathered for their classification.

The system also requires access to an LLM. The system supports multiple models.

The presentation file Static_Code_Analysis_Framework-high_level_design.pdf provides
a high level explanation of the proposed system.
