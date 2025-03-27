# Systematic Review Assistant

## Open Questions
- [ ] MVP priority: screening, extraction, or another step? (what do we build first)
- [ ] Focus scope: Bell's Palsy only or different ENT condition?
- [ ] Most appropriate LLM for medical domain tasks?
- [ ] Optimal automation vs. human oversight balance? Specific researcher pain points in systematic reviews?
- [ ] Available validation benchmarks from existing reviews?
- [ ] Success metrics for MVP evaluation?
- [ ] Strategies for addressing LLM hallucinations in medical contexts? (Auditability)

## Action Items
To be tackled after scope definition.
- [ ] Next meeting with Dr. Song to refine scope
- [ ] Review landscape of existing tools for systematic review
- [ ] Review best practices for systematic review (Cochrane? Other?)
- [ ] Sketch technical specifications

## Background
Systematic reviews are notorious time-sinks. Researchers frequently spend months manually parsing literature - a process ripe for intelligent assistance. Our goal: build an AI tool that meaningfully reduces workload without compromising research standards.

## Validation Strategy

We'll validate by replicating a published systematic review:
- Compare results, time investment, and accuracy
- Document discrepancies and system improvements
- Measure against defined success metrics (time reduction, accuracy)

## Systematic Review Process

```mermaid
flowchart LR
    subgraph Phase1[Planning Phase]
        direction TB
        A[Protocol Development]
        B[Literature Search]
        C[Abstract Screening]
    end

    subgraph Phase2[Analysis Phase]
        direction TB
        D[Full-Text Review]
        E[Data Extraction]
        F[Quality Assessment]
    end

    subgraph Phase3[Synthesis Phase]
        direction TB
        G[Data Synthesis]
        H[Meta-Analysis]
        I[Report Generation]
    end

    Phase1 --> Phase2
    Phase2 --> Phase3

    style Phase1 fill:#d0f0c0
    style Phase2 fill:#d0e0ff
    style Phase3 fill:#ffe0d0

    style A fill:#b8e4b8
    style B fill:#b8e4b8
    style C fill:#b8e4b8
    style D fill:#b8d4ff
    style E fill:#b8d4ff
    style F fill:#b8d4ff
    style G fill:#ffd4b8
    style H fill:#ffd4b8
    style I fill:#ffd4b8

    A --> B
    B --> C
    D --> E
    E --> F
    G --> H
    H --> I

    classDef subgraphLabel fill:none,stroke:none,color:black
    class Phase1,Phase2,Phase3 subgraphLabel

    classDef arrow fill:none,stroke:#000000,color:#000000,stroke-width:2
    class Phase1,Phase2,Phase3,A,B,C,D,E,F,G,H,I arrow
```

### Key Process Steps
1. **Protocol Development**: PICO framework, inclusion/exclusion criteria, search strategy
2. **Literature Search**: Database queries, citation export, duplicate removal
3. **Abstract Screening**: Title/abstract review against criteria, multiple reviewers
4. **Full-Text Review**: Detailed assessment, reference list checking
5. **Data Extraction**: Study characteristics, methods, outcomes, statistical data
6. **Quality Assessment**: Risk of bias evaluation using validated tools
7. **Data Synthesis**: Organization and summarization of findings
8. **Meta-Analysis**: Statistical combination of results, heterogeneity assessment
9. **Report Generation**: PRISMA-compliant documentation, findings summary

## Technical Approach

We'll implement a hybrid approach combining AI capabilities with human oversight:

1. **Key Requirements**
   - Auditability: Traceable decisions with source text support
   - Human verification: Review interface with override capabilities
   - Integration: Compatibility with tools researchers currently use

2. **MVP Options**

   | Option | Focus | Priority |
   |--------|-------|----------|
   | Abstract Screening | Automate screening of hundreds/thousands of abstracts | High |
   | Data Extraction | Extract structured data from full-text articles | High |
   | Protocol Development | Guide researchers in designing robust protocols | Medium |
