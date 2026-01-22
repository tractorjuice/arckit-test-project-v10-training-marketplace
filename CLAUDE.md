# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Overview

This is **ArcKit Test Project v10** - a demonstration repository showcasing ArcKit's Platform Design Toolkit capabilities for a **UK Government Training Marketplace Platform** (Civil Service Learning Platform).

**Purpose**: Demonstrate multi-sided platform design using all 8 Platform Design Toolkit (PDT) canvases, connecting training providers with civil servants seeking professional development.

## Using ArcKit Commands

ArcKit provides 40 slash commands for enterprise architecture governance. In this repository:

```bash
# Core workflow commands (run in order)
/arckit.principles Create cloud-first principles for UK Government
/arckit.stakeholders Analyze stakeholders for Civil Service Learning Platform
/arckit.requirements Create requirements for training marketplace
/arckit.platform-design Design Civil Service Learning Platform using 8 PDT canvases
/arckit.data-model Create data model for training marketplace
/arckit.diagram Generate container diagram for platform architecture

# Additional useful commands
/arckit.risk Create risk register for platform delivery
/arckit.sobc Create Strategic Outline Business Case
/arckit.wardley Build vs buy analysis for platform components
/arckit.tcop Technology Code of Practice assessment
```

## Project Structure

```
projects/001-ai-training-marketplace/
├── stakeholder-drivers.md     # Stakeholder analysis
├── requirements.md            # Business and technical requirements
├── platform-design.md         # 8 PDT canvases
├── data-model.md              # ERD with GDPR compliance
├── project-plan.md            # Delivery timeline
└── diagrams/                  # Architecture diagrams
```

## Key Patterns

**Token Limit Handling**: Large documents (requirements, platform-design) may exceed Claude's 32K output limit. Use Write tool strategy:
```
/arckit.requirements but write directly to file using Write tool, show me only a summary
```

**Template-Driven Generation**: All artifacts use templates from `.arckit/templates/`. Never generate freeform documents.

**Traceability Chain**: Stakeholders → Goals → Requirements (BR/FR/NFR/INT/DR) → Data Model → Platform Components

**UK Government Context**: This project targets UK public sector, so commands apply GDS Service Standard, TCoP, NCSC CAF, and GOV.UK service integration patterns.

## Requirement ID Prefixes

- BR-xxx: Business Requirements
- FR-xxx: Functional Requirements
- NFR-xxx: Non-Functional (NFR-P Performance, NFR-SEC Security, NFR-S Scalability, NFR-A Availability, NFR-C Compliance)
- INT-xxx: Integration Requirements
- DR-xxx: Data Requirements

## Platform Design Context

This is a **multi-sided ecosystem platform** with network effects:
- **Supply Side**: Training providers (private sector, universities, professional bodies)
- **Demand Side**: Civil servants seeking professional development
- **Supporting Entities**: Line managers, HR teams, L&D teams, Cabinet Office

The 8 PDT canvases cover: Ecosystem, Entity-Role Portraits, Motivations Matrix, Transactions Board, Learning Engine, Platform Experience, MVP, and Platform Design Canvas.
