# Project Requirements: AI Training Marketplace

> **Template Status**: Live | **Version**: 0.11.1 | **Command**: `/arckit.requirements`

## Document Control

| Field | Value |
|-------|-------|
| **Document ID** | ARC-001-REQ-v1.2 |
| **Document Type** | Business and Technical Requirements |
| **Project** | AI Training Marketplace (Project 001) |
| **Classification** | OFFICIAL |
| **Status** | DRAFT |
| **Version** | 1.2 |
| **Created Date** | 2025-11-09 |
| **Last Modified** | 2026-01-26 |
| **Review Cycle** | Monthly |
| **Next Review Date** | 2026-02-26 |
| **Owner** | Chief Product Officer, AI Training Marketplace |
| **Reviewed By** | [PENDING] |
| **Approved By** | [PENDING] |
| **Distribution** | Project Team, Architecture Team, Compliance Team |

## Revision History

| Version | Date | Author | Changes | Approved By | Approval Date |
|---------|------|--------|---------|-------------|---------------|
| 1.0 | 2025-11-09 | ArcKit AI | Initial creation from `/arckit.requirements` command | [PENDING] | [PENDING] |
| 1.1 | 2026-01-26 | ArcKit AI | Updated to match latest template structure (Document Control fields) | [PENDING] | [PENDING] |
| 1.2 | 2026-01-26 | ArcKit AI | Added Template Status metadata line per latest template | [PENDING] | [PENDING] |

## Document Purpose

This document defines comprehensive business, functional, non-functional, data, and integration requirements for the AI Training Marketplace platform. It serves as the foundation for:
- Technology research and vendor evaluation (`/arckit.research`)
- Architecture and design decisions (`/arckit.hld-review`, `/arckit.dld-review`)
- Data modeling (`/arckit.data-model`)
- Compliance assessments (`/arckit.secure`, `/arckit.tcop`, `/arckit.dpia`)
- Traceability and testing (`/arckit.traceability`)

Requirements are directly traceable to stakeholder drivers and goals documented in `stakeholder-drivers.md` (ARC-001-STKE-v1.0).

---

## Executive Summary

### Business Context

The AI Training Marketplace is a multi-sided platform connecting training providers (universities, private institutions, independent trainers) with organizations and individuals seeking AI/ML training. The platform addresses a critical market need: the UK AI skills gap threatens digital transformation initiatives across enterprise and public sectors, with hiring AI talent expensive (£80-120K salaries) and slow (6-12 month cycles).

The platform creates value for three stakeholder groups: (1) Training providers gain access to enterprise customers and reduce customer acquisition costs from £500 to £50 per customer, (2) Enterprise customers upskill workforces at £2-5K per person (vs £80K+ recruitment), achieving 3:1 ROI and 75%+ completion rates, and (3) Individual learners advance careers with 20-40% salary increases (£50K → £70K) through affordable, flexible AI/ML training.

UK Government AI Strategy commits £2.5B to AI skills development, creating significant public sector procurement opportunity. However, government sales require compliance with Technology Code of Practice (13 points), GDS Service Standard (14 points), WCAG 2.2 Level AA accessibility, UK GDPR/DPA 2018, and Cyber Essentials Plus certification.

### Objectives

- **Platform Liquidity**: Achieve 200+ active training providers and 50+ enterprise customers by Month 12, enabling network effects and sustainable marketplace dynamics (supports stakeholder goal G-1)
- **Quality Assurance**: Maintain 4.2+ average course rating and 75%+ completion rate to build trust and ensure customer retention (supports stakeholder goal G-2)
- **Regulatory Compliance**: Achieve UK GDPR, GDS Service Standard (alpha), and Cyber Essentials Plus certification by Month 6 to enable public sector sales (supports stakeholder goal G-3)
- **Revenue Sustainability**: Generate £2M Annual Recurring Revenue by Month 24 through platform commission (20% of GMV), enterprise subscriptions, and premium services (supports stakeholder goal G-4)
- **Operational Excellence**: Deliver 99.9% platform uptime, <200ms API response times (p95), and <2 second page load times to ensure positive user experience

### Expected Outcomes

- **O-1: Platform Network Effects** - 10,000 monthly course enrollments by Month 18, with 80% organic growth (search, recommendations, word-of-mouth) reducing customer acquisition costs
- **O-2: Enterprise Customer Satisfaction** - 70% enterprise renewal rate and +20 Net Promoter Score by Month 18, creating predictable recurring revenue
- **O-3: Regulatory Compliance** - Zero ICO enforcement actions and £500K annual revenue from UK public sector customers by Month 24
- **Financial Outcome** - £1.5M Gross Merchandise Value (GMV) by Month 12, scaling to £8M GMV by Month 24

### Project Scope

**In Scope**:
- Multi-sided marketplace platform (web and mobile-responsive)
- Provider onboarding and course publishing tools
- Enterprise customer portals with subscription management
- Individual learner accounts with course enrollment and progress tracking
- Course search, discovery, and recommendation engine
- Payment processing (GOV.UK Pay, Stripe, enterprise invoicing)
- Learning Management System (LMS) integrations (SCORM, xAPI export)
- Content quality review and approval workflows
- Analytics dashboards (providers, enterprises, platform operations)
- UK GDPR compliance (data subject rights, encryption, audit logging)
- WCAG 2.2 Level AA accessibility
- Cyber Essentials Plus security controls
- Identity federation (GOV.UK One Login, Azure AD, SAML SSO)

**Out of Scope (Future Phases)**:
- Live instructor-led training delivery (Phase 2)
- Built-in video conferencing (integrate with Zoom/Teams in Phase 2)
- Mobile native apps (iOS/Android) - Phase 2, mobile-responsive web sufficient for Phase 1
- White-label marketplace for individual providers (Phase 3)
- Internationalization beyond UK (English language only in Phase 1)
- AI-powered course content generation (Phase 3)
- Blockchain-based credentials (Phase 3)

---

## Stakeholders

| Stakeholder | Role | Organization | Involvement Level | Stakeholder Driver Reference |
|-------------|------|--------------|-------------------|------------------------------|
| CEO/Founder | Executive Sponsor | AI Training Marketplace | Decision maker | SD-1: Market leadership, £2M ARR |
| Chief Product Officer | Product Owner | AI Training Marketplace | Requirements definition | Requirement ownership |
| Chief Technology Officer | Technical Lead | AI Training Marketplace | Architecture decisions | SD-7: Platform reliability |
| Chief Commercial Officer | Sales & Partnerships | AI Training Marketplace | Provider/customer acquisition | Provider and customer needs |
| Head of Content Quality | Quality Assurance | AI Training Marketplace | Course approval | SD-8: 4.2+ course rating |
| Head of Compliance | Compliance Officer | AI Training Marketplace | Regulatory compliance | SD-5, SD-6: GDPR, GDS compliance |
| Training Providers | Suppliers | External | Content creators, revenue beneficiaries | SD-2: Revenue and market reach |
| Enterprise Customers | Customers | External | Procurement, L&D teams | SD-3: Workforce AI capability, ROI |
| Individual Learners | End Users | External | Course participants | SD-4: Career advancement |
| ICO | Regulator | External | Data protection oversight | SD-5: UK GDPR compliance |
| GDS | Standards Body | External | Service Standard assessment | SD-6: TCoP compliance |

---

## Business Requirements

### BR-001: Platform Liquidity - Provider Onboarding

**Description**: Onboard 200+ active training providers (publishing ≥1 course, ≥1 enrollment in last 90 days) by Month 12 to establish course catalog variety and enable customer choice.

**Rationale**: Addresses stakeholder goal G-1 (Platform Liquidity) and driver SD-2 (Provider revenue). Multi-sided platforms require critical mass of supply to attract demand. Without sufficient course variety, enterprise customers cannot find relevant AI/ML training for their workforce needs, preventing platform adoption.

**Success Criteria**:
- 50 providers onboarded by Month 6 (curated, high-quality institutions)
- 120 providers onboarded by Month 9 (expanded onboarding with automated pre-screening)
- 200+ providers onboarded by Month 12 (target achieved)
- 80% provider retention rate (providers remain active after 12 months)
- Average 2 courses per provider (400 total courses in catalog)

**Priority**: MUST_HAVE

**Stakeholder**: Chief Commercial Officer (provider acquisition), Training Providers (market access)

**Traceability**:
- Stakeholder Driver: SD-2 (Training Providers - Revenue & Reach)
- Stakeholder Goal: G-1 (Platform liquidity: 200 providers, 50 enterprises)
- Stakeholder Outcome: O-1 (10K monthly enrollments, 80% organic)

---

### BR-002: Platform Liquidity - Enterprise Customer Acquisition

**Description**: Acquire 50+ enterprise customers (≥10 licenses each) by Month 12 to establish demand side of marketplace and create revenue foundation.

**Rationale**: Addresses stakeholder goal G-1 (Platform Liquidity) and driver SD-3 (Enterprise workforce development). Platform needs both supply (providers) and demand (customers) simultaneously. Enterprise customers provide bulk enrollments and recurring revenue, reducing dependence on individual learner purchases.

**Success Criteria**:
- 10 pilot enterprise customers by Month 6 (prove value, establish case studies)
- 30 enterprise customers by Month 9 (scale sales team, leverage case studies)
- 50+ enterprise customers by Month 12 (target achieved)
- 70% enterprise renewal rate by Month 18 (customers renew annual subscriptions)
- £1.5M GMV from enterprise customers by Month 12 (75% of total GMV)

**Priority**: MUST_HAVE

**Stakeholder**: Chief Commercial Officer (enterprise sales), Enterprise Customers (workforce training), Finance Director (revenue targets)

**Traceability**:
- Stakeholder Driver: SD-3 (Enterprise Customers - AI Workforce Development)
- Stakeholder Goal: G-1 (Platform liquidity: 200 providers, 50 enterprises)
- Stakeholder Outcome: O-2 (70% renewal rate, +20 NPS)

---

### BR-003: Course Quality Standards

**Description**: Maintain 4.2+ average course rating (5-point scale) and 75%+ course completion rate across all courses by Month 9, ensuring quality standards that drive customer satisfaction and retention.

**Rationale**: Addresses stakeholder goal G-2 (Course Quality) and drivers SD-3 (Enterprise ROI), SD-4 (Learner career advancement), SD-8 (Content quality). Course quality is the primary differentiator from competitors. Low-quality courses waste learner time and training budgets, leading to customer churn and reputational damage.

**Success Criteria**:
- Course quality rubric defined and published by Month 2 (transparent, objective criteria)
- All new courses reviewed against rubric before publication
- 4.0+ average rating by Month 6 (initial baseline with curated providers)
- 4.2+ average rating by Month 9 (target sustained through growth phase)
- 75%+ completion rate by Month 9 (learners complete ≥80% of course content)
- <5% courses rated below 3.5 (continuous monitoring, provider improvement or removal)

**Priority**: MUST_HAVE

**Stakeholder**: Head of Content Quality (quality standards), Enterprise Customers (ROI expectations), Individual Learners (learning experience)

**Traceability**:
- Stakeholder Driver: SD-8 (Content Quality - Course Standards)
- Stakeholder Goal: G-2 (4.2+ rating, 75% completion)
- Stakeholder Outcome: O-2 (70% renewal rate, +20 NPS)

---

### BR-004: UK GDPR and Data Protection Compliance

**Description**: Achieve full UK GDPR and Data Protection Act 2018 compliance by Month 6, including Data Protection Impact Assessment (DPIA), data subject rights implementation, encryption, and audit logging, enabling lawful processing of learner personal data.

**Rationale**: Addresses stakeholder goal G-3 (Compliance) and driver SD-5 (ICO data protection). UK GDPR compliance is non-negotiable - violations trigger fines up to £17.5M or 4% global revenue, reputational damage, and potential shutdown. Enterprise customers require GDPR compliance for procurement (data processing agreements mandatory). Public sector sales require DPIA completion.

**Success Criteria**:
- DPIA completed and submitted to ICO by Month 4 (high-risk processing identified and mitigated)
- Data subject rights automated (access, rectification, erasure, portability, objection) with <30 day response time
- Encryption at rest for all data stores (databases, object storage, backups)
- Encryption in transit for all network communication (TLS 1.3)
- Audit logging of all data access and modifications (SIEM integration)
- Data Processing Agreements (DPAs) with all processors (cloud providers, payment gateways)
- Zero ICO enforcement actions (no fines, warnings, or breach notifications)

**Priority**: MUST_HAVE

**Stakeholder**: Head of Compliance (regulatory liaison), ICO (data protection regulator), Enterprise Customers (procurement requirements)

**Traceability**:
- Stakeholder Driver: SD-5 (ICO - Data Protection Compliance)
- Stakeholder Goal: G-3 (UK GDPR compliance by Month 6)
- Stakeholder Outcome: O-3 (Zero enforcement actions)

---

### BR-005: GDS Service Standard and TCoP Compliance

**Description**: Pass GDS Service Standard alpha assessment and demonstrate Technology Code of Practice compliance (13 points) by Month 6, enabling UK public sector procurement and £500K annual public sector revenue target.

**Rationale**: Addresses stakeholder goal G-3 (Compliance) and driver SD-6 (GDS standards). UK public sector represents £3B+ training market opportunity. Government procurement requires TCoP and Service Standard compliance (mandatory for spend >£100K). Non-compliance excludes platform from G-Cloud framework and Digital Marketplace.

**Success Criteria**:
- GDS Service Standard alpha assessment passed by Month 6 (14 points reviewed, remediation actions completed)
- Technology Code of Practice self-assessment completed (13 points documented):
  - Point 1: User needs defined (user research, personas)
  - Point 2: Accessibility (WCAG 2.2 AA)
  - Point 3: Open source considered
  - Point 4: Open standards (APIs, data formats)
  - Point 5: Cloud first (cloud-native architecture)
  - Point 6: Security (Cyber Essentials Plus)
  - Point 7: Privacy (UK GDPR, DPIA)
  - Point 8: Share and reuse (API-first, integrations)
  - Point 9: Integration (LMS, HR, identity systems)
  - Point 10: Data governance
  - Point 11: Procurement strategy
  - Point 12: Digital Spend Controls process
  - Point 13: Responsible AI (ATRS for recommendations)
- Cyber Essentials Plus certification achieved by Month 6
- WCAG 2.2 Level AA compliance validated (automated and manual testing)
- £500K public sector revenue by Month 24 (government departments, agencies, local authorities)

**Priority**: MUST_HAVE (for public sector sales), SHOULD_HAVE (for commercial-only strategy)

**Stakeholder**: Head of Compliance (GDS liaison), GDS (service assessment), Public Sector Customers (procurement requirements)

**Traceability**:
- Stakeholder Driver: SD-6 (GDS - Public Sector Standards)
- Stakeholder Goal: G-3 (GDS Service Standard pass by Month 6)
- Stakeholder Outcome: O-3 (£500K public sector revenue)

---

### BR-006: Revenue Target - £2M ARR by Month 24

**Description**: Generate £2M Annual Recurring Revenue (ARR) by Month 24 through platform commission (20% of GMV), enterprise subscriptions, and premium services, demonstrating revenue sustainability and supporting Series B fundraising.

**Rationale**: Addresses stakeholder goal G-4 (Revenue) and driver SD-1 (CEO market leadership). Revenue validates product-market fit and enables platform operations, engineering, sales, and marketing investment. Investors expect 3x annual growth trajectory (£2M Year 2 → £6M Year 3) to justify Series A investment and enable Series B funding (target £10M at £50M valuation).

**Success Criteria**:
- £500K ARR by Month 12 (£1.5M GMV, 20% platform commission = £300K + £200K enterprise subscriptions)
- £1.2M ARR by Month 18 (£4M GMV, revenue mix diversification)
- £2M ARR by Month 24 (£8M GMV, sustainable growth)
- Customer Lifetime Value (LTV) : Customer Acquisition Cost (CAC) ratio ≥3:1
- Gross margin 60-70% (after platform commission, payment processing, hosting)
- Revenue churn <30% annually (customer retention drives recurring revenue)

**Priority**: MUST_HAVE

**Stakeholder**: CEO/Founder (market leadership, fundraising), Finance Director (revenue forecasting), Investors/Board (growth expectations)

**Traceability**:
- Stakeholder Driver: SD-1 (CEO - Market Leadership)
- Stakeholder Goal: G-4 (£2M ARR by Month 24)
- Stakeholder Outcome: O-1 (10K enrollments drives GMV), O-2 (70% renewal sustains ARR)

---

### BR-007: Platform Uptime and Reliability

**Description**: Deliver 99.9% platform uptime (43.8 minutes downtime per month), automated health checks and failover, and <15 minute Recovery Time Objective (RTO) for critical services, ensuring reliable access to training courses and minimizing revenue loss from outages.

**Rationale**: Addresses stakeholder goal G-3 (Compliance) and driver SD-7 (CTO platform reliability). Platform downtime directly impacts revenue (lost enrollments, payment failures) and reputation. Enterprise customers require uptime SLAs in contracts. Public sector procurement evaluates service reliability. Outages during peak periods (course launches, government training initiatives) cause significant business damage.

**Success Criteria**:
- 99.9% uptime measured monthly (excludes planned maintenance windows)
- Automated health checks and failover configured (multi-AZ deployment)
- Recovery Time Objective (RTO): 15 minutes for Tier 1 services (enrollment, payment, authentication)
- Recovery Point Objective (RPO): 0 minutes for Tier 1 (synchronous replication)
- Incident response runbooks tested quarterly (tabletop exercises)
- Disaster recovery plan validated annually (full failover test)
- Zero critical outages >1 hour in first 12 months

**Priority**: MUST_HAVE

**Stakeholder**: CTO (platform operations), Enterprise Customers (service reliability), Finance Director (revenue protection)

**Traceability**:
- Stakeholder Driver: SD-7 (CTO - Platform Reliability)
- Stakeholder Goal: G-3 (Compliance, operational excellence)
- Stakeholder Outcome: O-2 (Uptime supports 70% renewal rate)

---

## Functional Requirements

### User Personas

#### Persona 1: Training Provider (Provider Admin)
- **Role**: Course creator, training institution administrator
- **Goals**: Publish courses, reach new customers, maximize revenue, understand learner demand
- **Pain Points**: High customer acquisition costs (£500/customer), limited geographic reach, manual payment processing, lack of customer insights
- **Technical Proficiency**: Medium (comfortable with web tools, course authoring, basic analytics)
- **Key Workflows**: Provider onboarding, course creation, pricing configuration, enrollment tracking, revenue reporting

#### Persona 2: Enterprise L&D Manager
- **Role**: Learning & Development manager at enterprise organization
- **Goals**: Upskill workforce in AI/ML, measure training ROI, manage training budget, track completion rates
- **Pain Points**: Fragmented vendor landscape, quality variability, difficult ROI measurement, lack of integration with HR/LMS systems
- **Technical Proficiency**: Medium (comfortable with enterprise software, reporting tools, procurement processes)
- **Key Workflows**: Course discovery, bulk licensing, learner assignment, progress tracking, ROI reporting, vendor management

#### Persona 3: Enterprise Procurement Officer
- **Role**: Procurement specialist responsible for vendor due diligence
- **Goals**: Ensure value for money, validate security/compliance, negotiate contracts, minimize procurement risk
- **Pain Points**: Lengthy security reviews, compliance documentation requests, contract negotiations
- **Technical Proficiency**: Low (focused on contracts, not technology)
- **Key Workflows**: Vendor assessment, security review, contract negotiation, purchase order processing

#### Persona 4: Individual Learner (Employee)
- **Role**: Employee seeking to upskill in AI/ML for career advancement
- **Goals**: Learn practical AI/ML skills, earn recognized credentials, apply skills to job projects, advance career
- **Pain Points**: Limited study time, difficult course content, lack of employer recognition, expensive courses
- **Technical Proficiency**: Medium (comfortable with online learning, basic tech tools)
- **Key Workflows**: Course search, enrollment, learning, assessment, certificate download, skill showcase

#### Persona 5: Individual Learner (Career Changer)
- **Role**: Professional transitioning from non-AI role to AI career
- **Goals**: Acquire foundational AI/ML skills, build portfolio projects, gain credentials recognized by employers
- **Pain Points**: No prior AI experience, unsure where to start, expensive university programs, need flexible learning
- **Technical Proficiency**: Low to Medium (varies by background)
- **Key Workflows**: Learning path discovery, prerequisite guidance, foundational courses, portfolio building, job search support

#### Persona 6: Platform Administrator
- **Role**: AI Training Marketplace operations team member
- **Goals**: Manage providers, review course quality, resolve customer issues, monitor platform health, prevent fraud
- **Pain Points**: Manual review bottlenecks, provider disputes, fraud detection challenges
- **Technical Proficiency**: High (technical operations, data analysis, fraud investigation)
- **Key Workflows**: Provider vetting, course quality review, customer support escalation, fraud investigation, platform monitoring

---

### Use Cases

#### UC-001: Provider Onboarding and Course Publishing

**Actor**: Training Provider (Provider Admin)

**Preconditions**:
- Provider has training content ready to publish
- Provider has business information (legal entity, bank account, contact details)

**Main Flow**:
1. Provider navigates to platform homepage and clicks "Become a Provider"
2. System presents provider registration form (business details, contact, banking info)
3. Provider completes form and submits (KYC/AML validation triggered)
4. System validates provider information and sends email verification
5. Provider verifies email and logs into provider portal
6. System presents course creation wizard
7. Provider creates course: title, description, learning objectives, category, pricing
8. Provider uploads course content (videos, documents, assessments, prerequisites)
9. System validates content format and completeness (automated checks: plagiarism, accessibility, file formats)
10. Provider submits course for quality review
11. System queues course for manual review by content quality team
12. Content quality team reviews course against quality rubric (1-3 business days)
13. System sends approval notification to provider (or rejection with feedback)
14. Provider publishes approved course to marketplace
15. System indexes course in search engine and recommendation algorithm

**Postconditions**:
- Provider account created and verified
- Course published and discoverable in marketplace
- Course available for enrollment by learners
- Provider can track enrollments and revenue in provider dashboard

**Alternative Flows**:
- **Alt 7a**: If provider pricing violates platform policy (e.g., <£10 or >£5000), system displays pricing guidance and prevents submission
- **Alt 9a**: If automated checks fail (plagiarism detected, accessibility violations, malware in uploads), system rejects submission with specific feedback
- **Alt 12a**: If course quality review identifies issues, content quality team rejects with improvement feedback; provider revises and resubmits

**Exception Flows**:
- **Ex 1**: If KYC/AML validation fails (provider on sanctions list, fraudulent information), system suspends registration and triggers manual review
- **Ex 2**: If course upload exceeds storage quota, system displays quota message and prompts upgrade or content reduction

**Business Rules**:
- BR-001: Support 200+ provider onboarding by Month 12
- Providers must pass KYC/AML validation before publishing courses
- Courses must achieve ≥3.5 rating to remain published (continuous monitoring)
- Platform commission: 30% for first £10K GMV, 25% for £10-50K, 20% for £50K+

**Functional Requirements Derived**:
- FR-001 through FR-010 (see detailed FR section below)

---

#### UC-002: Enterprise Bulk Course Enrollment

**Actor**: Enterprise L&D Manager

**Preconditions**:
- Enterprise has active subscription or contract with platform
- Enterprise has employee roster uploaded to platform
- Courses selected for employee training

**Main Flow**:
1. L&D Manager logs into enterprise portal
2. System displays enterprise dashboard (enrolled learners, completion rates, skill reports)
3. L&D Manager navigates to "Assign Training" section
4. System displays course catalog with search and filtering
5. L&D Manager searches for AI/ML courses (filters: topic, level, duration, provider)
6. System returns relevant courses with ratings, reviews, prerequisites
7. L&D Manager selects course and clicks "Assign to Learners"
8. System displays employee roster with skill levels and enrollment history
9. L&D Manager selects employees (individual selection or CSV upload)
10. System validates employee eligibility (license availability, prerequisites met)
11. L&D Manager confirms assignment and optional deadline
12. System creates enrollments, sends email notifications to employees, reserves licenses
13. Employees receive email with course link and access instructions
14. L&D Manager monitors progress in enterprise dashboard (real-time updates)

**Postconditions**:
- Employees enrolled in selected course
- Licenses consumed from enterprise subscription
- Progress tracking enabled in enterprise dashboard
- Email notifications sent to employees

**Alternative Flows**:
- **Alt 10a**: If enterprise has insufficient licenses, system displays license shortage message and prompts license purchase
- **Alt 10b**: If employee missing prerequisites, system displays prerequisite warning; L&D Manager can override or assign prerequisite courses first
- **Alt 12a**: If LMS integration enabled, system synchronizes enrollment to enterprise LMS (SCORM/xAPI export)

**Exception Flows**:
- **Ex 1**: If employee email invalid (bounced notification), system flags enrollment as failed and prompts L&D Manager to update employee information

**Business Rules**:
- BR-002: Support 50+ enterprise customers by Month 12
- Enterprise subscriptions include bulk licenses (10, 50, 100, 500, unlimited tiers)
- License consumption tracked in real-time; auto-renewal or overage billing configured
- Enterprise dashboard updates within 5 minutes of learner activity (near-real-time sync)

**Functional Requirements Derived**:
- FR-020 through FR-030 (see detailed FR section below)

---

#### UC-003: Learner Course Discovery and Enrollment

**Actor**: Individual Learner (Employee or Career Changer)

**Preconditions**:
- Learner has platform account (or creates account during checkout)
- Learner has payment method (credit card, or employer-sponsored enrollment)

**Main Flow**:
1. Learner navigates to platform homepage
2. System displays course catalog homepage (featured courses, categories, search bar)
3. Learner enters search query (e.g., "machine learning for beginners")
4. System returns ranked search results (relevance, ratings, popularity)
5. Learner filters results (level: beginner/intermediate/advanced, duration, price, provider)
6. System refines results based on filters
7. Learner clicks course to view details page
8. System displays course details (title, description, learning objectives, syllabus, instructor, reviews, prerequisites, pricing)
9. Learner reviews course information and decides to enroll
10. Learner clicks "Enroll Now"
11. System checks authentication (if not logged in, prompts login or registration)
12. System displays checkout page (course summary, pricing, payment method)
13. Learner enters payment information (or confirms employer sponsorship)
14. System processes payment via payment gateway (GOV.UK Pay, Stripe)
15. System creates enrollment, grants course access, sends confirmation email
16. Learner accesses course content immediately

**Postconditions**:
- Learner enrolled in course
- Payment processed and recorded
- Course content accessible to learner
- Enrollment tracked for progress reporting
- Provider credited with revenue (minus platform commission)

**Alternative Flows**:
- **Alt 11a**: If employer-sponsored enrollment, system validates learner eligibility (employee roster check) and bypasses payment
- **Alt 14a**: If payment fails (insufficient funds, fraud detection), system displays error message and offers retry or alternative payment method
- **Alt 9a**: If course has prerequisites not met, system displays prerequisite warning and recommends foundational courses

**Exception Flows**:
- **Ex 1**: If course has limited seats and all seats taken, system displays waitlist option
- **Ex 2**: If course no longer available (provider removed, quality violation), system displays apology message and recommends similar courses

**Business Rules**:
- Individual course pricing: £50-£500 per course (provider sets, platform suggests based on market data)
- Platform commission: 20-30% of course price (tiered based on provider GMV)
- Enrollment confirmation email sent within 1 minute of payment success
- Course access granted immediately upon enrollment (no delay)

**Functional Requirements Derived**:
- FR-040 through FR-055 (see detailed FR section below)

---

### Functional Requirements (Detailed)

#### Provider Onboarding and Course Management (FR-001 to FR-015)

**FR-001: Provider Self-Service Registration**

**Description**: Platform MUST provide self-service provider registration workflow enabling training providers to register, submit business information, and undergo KYC/AML validation without manual intervention.

**Acceptance Criteria**:
- Registration form captures: legal entity name, business type, tax ID, contact person, email, phone, address, banking details
- Email verification sent immediately upon registration (verify email ownership)
- KYC/AML validation triggered automatically (sanctions list check, fraud detection)
- Provider account activated within 24 hours (if validation passes)
- Rejection notification sent if validation fails (with appeal process)

**Priority**: MUST_HAVE

**Traceability**: Supports UC-001 (Provider Onboarding), BR-001 (200+ providers), SD-2 (Provider revenue)

---

**FR-002: Course Creation Wizard**

**Description**: Platform MUST provide intuitive course creation wizard enabling providers to create courses with metadata, content uploads, pricing, and prerequisites.

**Acceptance Criteria**:
- Course metadata fields: title, description, learning objectives, category, subcategory, tags, level (beginner/intermediate/advanced), duration, language
- Content upload support: video (MP4, max 5GB per file), documents (PDF, max 100MB), assessments (quiz JSON format), SCORM packages
- Pricing configuration: one-time purchase, subscription, enterprise licensing, free preview options
- Prerequisites specification: required prior courses or skill levels
- Progress save functionality: draft courses can be saved and resumed
- Preview mode: providers can preview course as learners see it

**Priority**: MUST_HAVE

**Traceability**: Supports UC-001 (Course Publishing), BR-001 (Course catalog growth), SD-2 (Provider content creation)

---

**FR-003: Automated Content Validation**

**Description**: Platform MUST perform automated validation of course content during upload to detect plagiarism, accessibility violations, malware, and format issues before manual quality review.

**Acceptance Criteria**:
- Plagiarism detection: check course content against public web and existing platform courses (flagging >30% similarity)
- Accessibility validation: check videos for captions, PDFs for alt text, content for color contrast (WCAG 2.2 AA automated checks)
- Malware scanning: scan all uploaded files for viruses and malicious code
- Format validation: verify file formats, encoding, playback compatibility
- Automated checks complete within 5 minutes of upload
- Provider receives validation report with pass/fail status and remediation guidance

**Priority**: MUST_HAVE

**Traceability**: Supports UC-001 (Content validation), BR-003 (Course quality), SD-8 (Quality standards)

---

**FR-004: Manual Course Quality Review Workflow**

**Description**: Platform MUST provide quality review workflow enabling content quality team to review courses against quality rubric, approve/reject, and provide feedback to providers.

**Acceptance Criteria**:
- Quality review queue displays pending courses (FIFO order, priority flags for curated providers)
- Quality rubric checklist: clear learning objectives, accurate content, engaging delivery, fair assessments, professional production
- Reviewer actions: approve (publish course), reject with feedback (provider revises), flag for escalation
- Review SLA: 80% of courses reviewed within 3 business days
- Provider notification: email sent immediately upon review decision (approval or rejection with specific feedback)
- Approval workflow: single reviewer for low-risk courses, dual reviewers for high-risk (e.g., medical AI content)

**Priority**: MUST_HAVE

**Traceability**: Supports UC-001 (Quality review), BR-003 (4.2+ rating), SD-8 (Quality standards), conflict resolution (quality vs speed)

---

**FR-005: Provider Revenue Dashboard**

**Description**: Platform MUST provide provider dashboard displaying enrollments, revenue, learner progress, reviews, and analytics to enable providers to track performance and optimize offerings.

**Acceptance Criteria**:
- Dashboard metrics: total enrollments, active learners, completion rate, average rating, total revenue (gross and net of commission)
- Time filters: today, last 7 days, last 30 days, custom date range
- Course-level breakdown: enrollments per course, revenue per course, rating per course
- Learner demographics: enterprise vs individual, geographic distribution, skill levels
- Revenue payout tracking: pending, paid, payment schedule (net 30 days)
- Export functionality: CSV/Excel export for accounting integration

**Priority**: MUST_HAVE

**Traceability**: Supports UC-001 (Provider onboarding), SD-2 (Provider analytics), BR-001 (Provider retention)

---

#### Enterprise Customer Portal (FR-020 to FR-035)

**FR-020: Enterprise Subscription Management**

**Description**: Platform MUST enable enterprise customers to purchase subscriptions, manage licenses, assign learners, and track utilization.

**Acceptance Criteria**:
- Subscription tiers: 10, 50, 100, 500, unlimited licenses with tiered pricing
- License management: view available/consumed licenses, purchase additional licenses, auto-renewal configuration
- Billing options: credit card, purchase order, invoice (net 30 days)
- Contract management: view active contracts, renewal dates, terms and conditions
- Multi-currency support: GBP, USD, EUR pricing display
- Overage handling: automatic billing for license overages or block enrollment (configurable)

**Priority**: MUST_HAVE

**Traceability**: Supports UC-002 (Bulk enrollment), BR-002 (50+ enterprises), SD-3 (Enterprise ROI)

---

**FR-021: Bulk Learner Assignment**

**Description**: Platform MUST enable L&D managers to assign courses to multiple learners simultaneously via UI selection or CSV upload.

**Acceptance Criteria**:
- UI selection: multi-select learners from employee roster, assign to single course or learning path
- CSV upload: template provided (employee email, course ID, deadline), batch processing (up to 1000 learners per upload)
- Validation: check employee eligibility (active account, license availability, prerequisites met)
- Assignment confirmation: summary screen showing successful/failed assignments with reasons
- Email notifications: automated emails sent to assigned learners with course access link
- Deadline enforcement: optional completion deadlines with reminder emails (7 days before, 1 day before)

**Priority**: MUST_HAVE

**Traceability**: Supports UC-002 (Bulk enrollment), BR-002 (Enterprise adoption), SD-3 (Workforce training)

---

**FR-022: Enterprise Progress Tracking and Reporting**

**Description**: Platform MUST provide enterprise dashboard with real-time learner progress tracking, completion rates, skill acquisition, and ROI reporting.

**Acceptance Criteria**:
- Dashboard metrics: enrolled learners, active learners (logged in last 7 days), completion rate, average time-to-complete
- Course-level breakdown: enrollment count per course, completion rate per course, average rating per course
- Skill tracking: skills acquired by learners (mapped from course learning objectives), skill distribution across organization
- ROI metrics: training investment (course costs), estimated business value (skills applied to projects - self-reported)
- Filters: department, location, job role, time period
- Scheduled reports: weekly/monthly email reports to L&D managers (PDF/CSV attachments)
- Export functionality: raw data export for custom analysis

**Priority**: MUST_HAVE

**Traceability**: Supports UC-002 (Progress tracking), BR-002 (Enterprise retention), SD-3 (ROI measurement), O-2 (70% renewal)

---

#### Learner Experience (FR-040 to FR-060)

**FR-040: Course Search and Discovery**

**Description**: Platform MUST provide course search engine enabling learners to discover relevant courses through keyword search, filters, and recommendations.

**Acceptance Criteria**:
- Search input: free-text keyword search (course title, description, instructor, provider)
- Search results: ranked by relevance (TF-IDF or semantic search), rating, popularity, recency
- Filters: category, level, duration, price range, provider, language, rating (≥4.0)
- Autocomplete: suggest course titles and topics as user types (improving UX and search success)
- Search performance: p95 latency <200ms for search queries (as per NFR-P-002)
- Result display: course thumbnail, title, provider, rating, price, duration, level (beginner/intermediate/advanced)
- Pagination: 20 courses per page, infinite scroll or page navigation

**Priority**: MUST_HAVE

**Traceability**: Supports UC-003 (Course discovery), O-1 (10K enrollments), SD-4 (Learner career advancement)

---

**FR-041: Course Recommendation Engine**

**Description**: Platform SHOULD provide personalized course recommendations based on learner profile, enrollment history, skill gaps, and career goals.

**Acceptance Criteria**:
- Recommendation algorithms: collaborative filtering (users like you enrolled in), content-based (similar courses), skill gap analysis
- Personalization inputs: learner job role, skill level, completed courses, browsing history, search queries
- Recommendation display: "Recommended for You" section on homepage, "Similar Courses" on course detail pages
- Transparency: brief explanation of why course recommended ("Based on your interest in X")
- Performance: recommendations updated daily (batch processing), displayed <200ms (cached)
- Algorithmic transparency: comply with UK GDPR Article 22 (automated decision-making), provide ATRS record for public sector customers (as per SD-6)

**Priority**: SHOULD_HAVE

**Traceability**: Supports O-1 (Organic growth), SD-4 (Learner experience), SD-6 (Responsible AI), alignment with principle "Responsible AI and Algorithmic Transparency"

---

**FR-042: Course Enrollment and Payment**

**Description**: Platform MUST enable learners to enroll in courses with payment processing via multiple payment methods (GOV.UK Pay, Stripe, enterprise sponsorship).

**Acceptance Criteria**:
- Payment methods: credit/debit card (Stripe), GOV.UK Pay (for public sector users), enterprise sponsorship (employer-paid)
- Checkout flow: course summary → payment method selection → payment details → confirmation
- Payment security: PCI DSS compliant (tokenization, no card storage), 3D Secure authentication
- Payment confirmation: immediate enrollment upon successful payment, confirmation email within 1 minute
- Payment failure handling: clear error messages, retry functionality, alternative payment method prompts
- Refund policy: 14-day money-back guarantee (automated refund processing, provider revenue reversal)

**Priority**: MUST_HAVE

**Traceability**: Supports UC-003 (Enrollment), BR-006 (Revenue), SD-3/SD-4 (Customer/learner value)

---

**FR-043: Learning Content Delivery**

**Description**: Platform MUST deliver course content (videos, documents, assessments) with adaptive streaming, progress tracking, and accessibility features.

**Acceptance Criteria**:
- Video streaming: adaptive bitrate (HLS/DASH), CDN delivery, <2 second startup time, playback resume
- Document viewer: in-browser PDF/document viewer, download option, print option
- Assessment engine: multiple choice, true/false, short answer, automatic grading, instant feedback
- Progress tracking: track video completion (% watched), document opens, assessment scores
- Accessibility: video captions (closed captions, multiple languages), transcript downloads, keyboard navigation, screen reader compatibility
- Offline support (SHOULD_HAVE): downloadable content for offline viewing (mobile app feature, Phase 2)

**Priority**: MUST_HAVE (streaming, assessment), SHOULD_HAVE (offline)

**Traceability**: Supports UC-003 (Learning), BR-003 (Completion rate), SD-4 (Learner experience)

---

**FR-044: Learner Progress and Certificate Management**

**Description**: Platform MUST track learner progress through courses and issue certificates upon completion.

**Acceptance Criteria**:
- Progress tracking: % course completed, lessons completed, assessments passed, time spent
- Completion criteria: 80% content consumed AND passing assessment score (≥70%)
- Certificate generation: automated upon completion, PDF format, includes course title, learner name, completion date, platform logo, provider logo
- Certificate verification: unique certificate ID, public verification URL (employers can verify authenticity)
- Transcript: learner transcript showing all completed courses, certificates earned, skills acquired
- Badge integration (SHOULD_HAVE): digital badges (Open Badges standard) for skill achievements

**Priority**: MUST_HAVE

**Traceability**: Supports BR-003 (75% completion), SD-3 (Enterprise ROI), SD-4 (Learner credentials), O-2 (Learner satisfaction)

---

**FR-045: Course Reviews and Ratings**

**Description**: Platform MUST enable learners to rate and review courses, with ratings displayed publicly to inform future learners and drive quality improvement.

**Acceptance Criteria**:
- Rating scale: 5-star rating (1-5 stars), required upon course completion
- Review text: optional text review (max 500 characters), moderation for inappropriate content
- Review display: course detail page shows average rating, rating distribution (5-star histogram), recent reviews
- Review sorting: sort by most helpful, most recent, highest/lowest rating
- Review moderation: automated profanity filter, manual review for flagged reviews, provider cannot delete reviews (only respond)
- Verified purchase badge: display "Verified Learner" badge for reviews from enrolled learners

**Priority**: MUST_HAVE

**Traceability**: Supports BR-003 (4.2+ rating), SD-3 (Enterprise quality assurance), SD-8 (Quality feedback loop), O-2 (Customer trust)

---

#### Platform Administration (FR-070 to FR-080)

**FR-070: Provider Vetting and Approval Workflow**

**Description**: Platform MUST provide administrator workflow to vet new providers, review business documentation, and approve/reject provider registrations.

**Acceptance Criteria**:
- Provider application queue: pending applications displayed with submission date, business details
- KYC/AML results integration: automated sanctions check results displayed, fraud risk score
- Manual review checklist: business legitimacy, website verification, sample course review (for curated providers)
- Approval actions: approve (activate provider account), reject (with reason), request additional information
- Provider notification: email sent with approval decision, next steps for approved providers
- Escalation: high-risk providers (e.g., international, high GMV projections) flagged for senior review

**Priority**: MUST_HAVE

**Traceability**: Supports BR-001 (Provider onboarding), conflict resolution (quality vs growth), SD-8 (Quality standards)

---

**FR-071: Fraud Detection and Prevention**

**Description**: Platform SHOULD implement fraud detection for fake accounts, fake reviews, payment fraud, and enrollment fraud.

**Acceptance Criteria**:
- Fake account detection: behavioral analysis (rapid account creation, suspicious email domains), device fingerprinting, CAPTCHA on registration
- Fake review detection: review patterns (multiple 5-star reviews from same IP, rapid reviews), language analysis (generic reviews, copy-paste)
- Payment fraud detection: payment gateway fraud signals (AVS mismatch, CVV failure, velocity checks), high-risk country blocking (configurable)
- Enrollment fraud detection: bulk enrollments from single account, rapid enrollment/refund cycles
- Administrator alerts: fraud alerts displayed in admin dashboard, email notifications for high-risk events
- Action enforcement: suspend accounts, remove reviews, block payment methods, investigate patterns

**Priority**: SHOULD_HAVE (Month 9+)

**Traceability**: Supports BR-003 (Quality protection), SD-7 (Platform integrity), SD-8 (Review authenticity)

---

**FR-072: Platform Analytics and Reporting**

**Description**: Platform MUST provide administrator dashboards with operational metrics, business KPIs, and compliance reporting.

**Acceptance Criteria**:
- Operational metrics: platform uptime, API response times, error rates, active users (DAU/MAU), enrollment volume
- Business KPIs: GMV, ARR, MRR, provider count, customer count, course count, average rating, completion rate
- Financial reporting: revenue by course, provider payouts pending/paid, payment success rate, refund rate
- Compliance reporting: data subject rights requests (access/deletion), security incidents, audit logs
- Real-time dashboards: Grafana or similar tool with customizable dashboards
- Scheduled reports: daily/weekly/monthly executive summaries (email to CEO, CPO, CTO)

**Priority**: MUST_HAVE

**Traceability**: Supports BR-001/002/003/006 (Goal tracking), SD-1 (CEO visibility), principle "Observability and Operational Excellence"

---

## Non-Functional Requirements

### Performance Requirements (NFR-P-xxx)

**NFR-P-001: API Response Time**

**Description**: Platform APIs MUST achieve p95 latency <200ms and p99 latency <500ms under normal load to ensure responsive user experience.

**Rationale**: Slow APIs degrade user experience, reduce conversion rates, and increase bounce rates. Enterprise customers expect performant systems. Aligns with architecture principle "Performance and Efficiency".

**Acceptance Criteria**:
- p50 latency: <100ms (median user experience)
- p95 latency: <200ms (95% of requests)
- p99 latency: <500ms (worst-case acceptable)
- Measurement: continuous monitoring with Prometheus/Grafana, SLO alerting if p95 exceeds 200ms for >5 minutes
- Load testing: validated at 2x expected load (20K concurrent users, 1000 requests/second)

**Priority**: MUST_HAVE

**Traceability**: Architecture Principle "Performance and Efficiency", BR-007 (Platform reliability), SD-7 (CTO performance targets)

---

**NFR-P-002: Search Performance**

**Description**: Course search MUST return results with p95 latency <200ms to enable fast course discovery and high search conversion rates.

**Rationale**: Search is critical user journey - slow search causes user abandonment. Aligns with O-1 outcome (10K enrollments) by enabling effective discovery.

**Acceptance Criteria**:
- Search p95 latency: <200ms (from query submission to results displayed)
- Search throughput: support 1000 queries per second (peak load)
- Search relevance: >80% of searches result in click-through to course detail page (indicates relevant results)
- Index update latency: new courses appear in search within 5 minutes of publication

**Priority**: MUST_HAVE

**Traceability**: FR-040 (Search), O-1 (Enrollment volume), SD-4 (Learner experience)

---

**NFR-P-003: Page Load Time**

**Description**: Platform pages MUST load within 2 seconds (p75) and 4 seconds (p95) to meet user experience expectations and search engine optimization requirements.

**Rationale**: Page load time directly impacts bounce rate, conversion rate, and SEO rankings. Google uses page speed as ranking factor. Aligns with SD-4 (learner experience).

**Acceptance Criteria**:
- p75 page load time: <2 seconds (75% of page loads)
- p95 page load time: <4 seconds (95% of page loads)
- Measurement: Real User Monitoring (RUM) with client-side instrumentation
- Optimization: bundle size <500KB (gzip), image optimization, lazy loading, CDN delivery
- Mobile performance: same targets for mobile devices (3G/4G networks)

**Priority**: MUST_HAVE

**Traceability**: SD-4 (Learner experience), O-1 (Conversion rate), principle "Performance and Efficiency"

---

**NFR-P-004: Video Streaming Performance**

**Description**: Course video content MUST stream with <2 second startup time and <1% buffering ratio to ensure smooth learning experience.

**Rationale**: Video is primary course content delivery method. Buffering and startup delays frustrate learners and reduce completion rates (threatens BR-003: 75% completion).

**Acceptance Criteria**:
- Startup time: <2 seconds from play button click to video playback start
- Buffering ratio: <1% of playback time spent buffering (99%+ smooth playback)
- Adaptive bitrate: automatic quality adjustment based on network conditions (360p, 720p, 1080p)
- CDN delivery: 95%+ cache hit rate, multi-region CDN for global performance
- Peak load support: 10,000 concurrent video streams without degradation

**Priority**: MUST_HAVE

**Traceability**: FR-043 (Content delivery), BR-003 (Completion rate), SD-4 (Learner experience)

---

**NFR-P-005: Concurrent User Support**

**Description**: Platform MUST support 10,000 concurrent users (Month 12) and 50,000 concurrent users (Month 24) without performance degradation.

**Rationale**: Aligns with BR-001/002 (platform liquidity: 200 providers, 50 enterprises = 10K+ learners) and growth projections. Platform must scale to support success.

**Acceptance Criteria**:
- Concurrent users (Month 12): 10,000 concurrent users with <200ms p95 API latency
- Concurrent users (Month 24): 50,000 concurrent users with <200ms p95 API latency
- Load testing: quarterly load tests at 2x projected concurrent users
- Auto-scaling: horizontal scaling configured to add capacity automatically when CPU >70%
- Database capacity: connection pooling, read replicas, query optimization to support load

**Priority**: MUST_HAVE

**Traceability**: BR-001/002 (Growth targets), architecture principle "Scalability and Elasticity", SD-7 (CTO scalability)

---

### Security Requirements (NFR-SEC-xxx)

**NFR-SEC-001: Authentication and Access Control**

**Description**: Platform MUST implement secure authentication with multi-factor authentication (MFA) for administrators and support identity federation for enterprise customers.

**Rationale**: Aligns with architecture principle "Security by Design" and BR-004 (UK GDPR). Account takeover threatens user data, revenue, and reputation.

**Acceptance Criteria**:
- Password policy: minimum 12 characters, complexity requirements (uppercase, lowercase, number, symbol), password history (no reuse of last 10 passwords)
- MFA: mandatory for platform administrators, optional for providers and enterprise admins, SMS/authenticator app support
- Identity federation: support SAML 2.0, OAuth 2.0, OpenID Connect for enterprise SSO (Azure AD, Okta, GOV.UK One Login)
- Session management: 24-hour session timeout for learners, 4-hour timeout for administrators, secure session cookies (HttpOnly, Secure, SameSite)
- Account lockout: 5 failed login attempts trigger 30-minute lockout (prevent brute force)

**Priority**: MUST_HAVE

**Traceability**: Architecture principle "Security by Design", BR-004 (GDPR), SD-5 (ICO security), SD-7 (CTO security)

---

**NFR-SEC-002: Data Encryption**

**Description**: Platform MUST encrypt all data at rest and in transit to protect sensitive information (learner PII, payment data, course content).

**Rationale**: UK GDPR requires appropriate technical measures to protect personal data. Encryption at rest and in transit are baseline security controls. Aligns with architecture principle "Security by Design".

**Acceptance Criteria**:
- Encryption at rest: AES-256 encryption for all databases, object storage, backups
- Encryption in transit: TLS 1.3 for all network communication (APIs, web pages, admin interfaces)
- Key management: encryption keys stored in dedicated key management service (AWS KMS, Azure Key Vault), key rotation every 90 days
- Certificate management: TLS certificates from trusted CA, automated renewal before expiration
- Encryption validation: quarterly penetration testing validates encryption implementation

**Priority**: MUST_HAVE

**Traceability**: Architecture principle "Security by Design", BR-004 (UK GDPR Article 32), SD-5 (ICO encryption), NFR-C-002 (PCI DSS)

---

**NFR-SEC-003: Secrets Management**

**Description**: Platform MUST store all secrets (API keys, database passwords, encryption keys) in secure vault and never in code or configuration files.

**Rationale**: Hardcoded secrets in code/config are common vulnerability leading to breaches. Aligns with architecture principle "Security by Design" (secrets management via secure vault).

**Acceptance Criteria**:
- Secrets vault: use dedicated secrets management service (HashiCorp Vault, AWS Secrets Manager, Azure Key Vault)
- No secrets in code: automated scanning (git-secrets, truffleHog) prevents secrets in source control
- No secrets in config: environment variables or vault injection at runtime (no plaintext secrets in config files)
- Secret rotation: database passwords rotated every 90 days, API keys rotated every 180 days
- Access control: secrets accessible only to authorized services/administrators (least privilege)

**Priority**: MUST_HAVE

**Traceability**: Architecture principle "Security by Design", SD-7 (CTO security), security best practices

---

**NFR-SEC-004: Security Testing and Vulnerability Management**

**Description**: Platform MUST undergo quarterly penetration testing and continuous vulnerability scanning to identify and remediate security weaknesses.

**Rationale**: Proactive security testing identifies vulnerabilities before attackers exploit them. Required for Cyber Essentials Plus certification (BR-005). Aligns with architecture principle "Security by Design".

**Acceptance Criteria**:
- Penetration testing: quarterly external penetration testing by certified third party (CREST or equivalent)
- Vulnerability scanning: continuous automated vulnerability scanning (dependency scanning, container scanning, SAST, DAST)
- Remediation SLA: critical vulnerabilities remediated within 7 days, high within 30 days, medium within 90 days
- Dependency management: automated dependency updates (Dependabot, Snyk), no dependencies with known critical vulnerabilities
- Security audit findings: zero critical findings, <5 high findings before production deployment

**Priority**: MUST_HAVE

**Traceability**: Architecture principle "Security by Design", BR-005 (Cyber Essentials Plus), SD-7 (CTO security)

---

**NFR-SEC-005: Audit Logging and SIEM**

**Description**: Platform MUST log all security-relevant events (authentication, authorization, data access, configuration changes) and integrate with Security Information and Event Management (SIEM) system.

**Rationale**: Audit logs required for UK GDPR compliance (Article 32), security incident investigation, and regulatory audits. Aligns with architecture principle "Observability and Operational Excellence".

**Acceptance Criteria**:
- Audit events logged: authentication attempts (success/failure), authorization decisions, data access (PII reads/writes), configuration changes, privilege escalation
- Log retention: 7 years for security/audit logs (UK GDPR requirement), 90 days for application logs
- Log integrity: logs immutable (append-only), cryptographic signing to prevent tampering
- SIEM integration: logs forwarded to SIEM (Splunk, ELK, Azure Sentinel) for correlation and alerting
- Alerting: security alerts for anomalous patterns (brute force attempts, privilege escalation, unusual data access)

**Priority**: MUST_HAVE

**Traceability**: Architecture principle "Observability", BR-004 (UK GDPR Article 32), SD-5 (ICO audit), SD-7 (Security monitoring)

---

### Availability and Reliability Requirements (NFR-A-xxx)

**NFR-A-001: Platform Uptime SLA**

**Description**: Platform MUST achieve 99.9% uptime (43.8 minutes downtime per month) excluding planned maintenance windows.

**Rationale**: Directly addresses BR-007 (Platform reliability) and SD-7 (CTO uptime target). Downtime impacts revenue (lost enrollments, payment failures) and reputation.

**Acceptance Criteria**:
- Uptime measurement: 99.9% measured monthly (excludes planned maintenance, maximum 4 hours/month during low-traffic windows)
- Redundancy: multi-AZ deployment (availability zones), automated failover for databases and application servers
- Health checks: liveness/readiness probes configured, automated health monitoring every 30 seconds
- Incident response: on-call rotation defined, incident response runbooks tested quarterly
- Uptime reporting: monthly uptime reports published to enterprise customers (transparency)

**Priority**: MUST_HAVE

**Traceability**: BR-007 (99.9% uptime), SD-7 (CTO reliability), O-2 (Customer retention depends on reliability)

---

**NFR-A-002: Disaster Recovery**

**Description**: Platform MUST implement disaster recovery with Recovery Time Objective (RTO) 15 minutes and Recovery Point Objective (RPO) 0 minutes for Tier 1 services.

**Rationale**: Disaster recovery ensures business continuity after catastrophic failures (data center outage, regional disaster). Aligns with architecture principle "Resilience and Fault Tolerance".

**Acceptance Criteria**:
- RTO (Recovery Time Objective): 15 minutes for Tier 1 services (enrollment, payment, authentication), 1 hour for Tier 2 (catalog, dashboard)
- RPO (Recovery Point Objective): 0 minutes for Tier 1 (synchronous replication), 5 minutes for Tier 2 (asynchronous replication)
- Backup strategy: automated daily backups, 30-day retention, monthly backup restore testing
- DR testing: annual disaster recovery drill (full regional failover test), documented runbooks
- Multi-region: active-passive deployment across 2 cloud regions (primary UK, secondary EU)

**Priority**: MUST_HAVE

**Traceability**: BR-007 (RTO/RPO), architecture principle "Resilience and Fault Tolerance", SD-7 (CTO disaster recovery)

---

**NFR-A-003: Graceful Degradation**

**Description**: Platform SHOULD gracefully degrade when non-critical services fail, allowing core workflows (enrollment, learning, payment) to continue.

**Rationale**: Aligns with architecture principle "Resilience and Fault Tolerance". Prevents cascading failures where one service outage brings down entire platform.

**Acceptance Criteria**:
- Circuit breakers: implemented for external dependencies (payment gateway, email service, analytics, recommendation engine)
- Degraded mode behaviors:
  - If recommendation engine fails: fall back to popular courses / category browsing
  - If analytics service fails: continue enrollment but queue analytics events for later processing
  - If email service fails: queue notifications for retry (up to 24 hours), display in-app message
- Timeout configuration: all external calls have <5 second timeout, prevent hanging requests
- Monitoring: degraded mode events logged and alerted (engineering investigates and remediates)

**Priority**: SHOULD_HAVE

**Traceability**: Architecture principle "Resilience and Fault Tolerance", SD-7 (CTO fault tolerance)

---

### Scalability Requirements (NFR-S-xxx)

**NFR-S-001: Horizontal Scaling**

**Description**: Platform MUST support horizontal scaling to handle growth from 10K concurrent users (Month 12) to 50K concurrent users (Month 24) without architectural changes.

**Rationale**: Aligns with architecture principle "Scalability and Elasticity" and BR-001/002 (platform liquidity growth). Vertical scaling (bigger servers) is limited; horizontal scaling (more servers) is required for marketplace growth.

**Acceptance Criteria**:
- Stateless application tier: no session state in application servers (use distributed cache or database for session storage)
- Auto-scaling: configured to add instances when CPU >70% or request queue depth >100
- Load balancing: distribute traffic across application instances with health checks
- Database scalability: support read replicas for read-heavy operations (course catalog, search), connection pooling
- Testing: quarterly load testing validates horizontal scaling at 2x projected load

**Priority**: MUST_HAVE

**Traceability**: Architecture principle "Scalability and Elasticity", BR-001/002 (Growth), NFR-P-005 (Concurrent users)

---

**NFR-S-002: Multi-Tenancy Scalability**

**Description**: Platform MUST support 200+ providers and 50+ enterprise customers as separate tenants with data isolation and independent scaling.

**Rationale**: Aligns with architecture principle "Multi-Tenancy and Data Isolation". Each provider and enterprise is logical tenant requiring data boundaries and potentially different resource allocations.

**Acceptance Criteria**:
- Tenant identification: tenant ID in all API requests (JWT claims), request headers
- Tenant-scoped queries: all database queries filtered by tenant ID (row-level security or application-level filtering)
- Tenant isolation testing: automated tests validate no cross-tenant data leakage (query provider A data while authenticated as provider B should fail)
- Tenant-specific configuration: branding, feature flags, pricing tiers configurable per tenant
- Performance: platform performs acceptably with 1000+ tenants (10x target for future growth)

**Priority**: MUST_HAVE

**Traceability**: Architecture principle "Multi-Tenancy and Data Isolation", BR-001/002 (Provider/customer count), SD-5 (GDPR data boundaries)

---

### Compliance Requirements (NFR-C-xxx)

**NFR-C-001: UK GDPR and DPA 2018 Compliance**

**Description**: Platform MUST comply with UK GDPR and Data Protection Act 2018, including data subject rights, lawful basis, data minimization, and breach notification.

**Rationale**: Directly addresses BR-004 (GDPR compliance) and SD-5 (ICO). Non-compliance risks fines up to £17.5M or 4% global revenue.

**Acceptance Criteria**:
- Lawful basis: documented lawful basis for all data processing (consent, contract, legitimate interest)
- Data subject rights: automated workflows for access (SAR), rectification, erasure, portability, objection (<30 day response time)
- Data minimization: collect only necessary data, retention policies enforce automatic deletion
- Breach notification: incident response plan includes <72 hour ICO notification (if high risk to individuals)
- Privacy by Design: DPIA completed (BR-004), privacy controls built into architecture
- Data Processing Agreements (DPAs): signed with all processors (cloud providers, payment gateways, email service)

**Priority**: MUST_HAVE

**Traceability**: BR-004 (UK GDPR), SD-5 (ICO compliance), architecture principle "Data Sovereignty and Governance", O-3 (Zero enforcement)

---

**NFR-C-002: PCI DSS Compliance (If Handling Payment Cards)**

**Description**: Platform SHOULD achieve PCI DSS compliance if storing, processing, or transmitting payment card data. If using tokenization (recommended), reduce PCI scope to SAQ-A.

**Rationale**: Payment card data is highly sensitive. PCI DSS compliance reduces fraud risk and is required by payment processors. Tokenization (outsourcing card handling to payment gateway) minimizes compliance burden.

**Acceptance Criteria**:
- Tokenization: use payment gateway tokenization (Stripe, GOV.UK Pay) to avoid storing card data on platform (reduces PCI scope to SAQ-A)
- If storing card data (NOT RECOMMENDED): achieve PCI DSS Level 2 (processing <6M transactions annually), quarterly vulnerability scanning, annual audit
- Network segmentation: cardholder data environment (CDE) isolated from other systems
- Access control: restrict access to CDE to authorized personnel only (least privilege)

**Priority**: SHOULD_HAVE (if handling cards directly), NOT_APPLICABLE (if full tokenization)

**Traceability**: FR-042 (Payment processing), SD-5 (Data protection), security best practices

---

**NFR-C-003: WCAG 2.2 Level AA Accessibility**

**Description**: Platform MUST achieve WCAG 2.2 Level AA accessibility compliance to enable UK public sector procurement and ensure inclusive access for learners with disabilities.

**Rationale**: Directly addresses BR-005 (GDS Service Standard) and SD-6 (GDS accessibility). UK Public Sector Bodies Accessibility Regulations 2018 mandate WCAG 2.2 AA. Also aligns with architecture principle "Accessibility and Inclusive Design".

**Acceptance Criteria**:
- Automated testing: WCAG 2.2 AA automated checks integrated in CI/CD (axe-core, pa11y), zero critical violations before deployment
- Manual testing: quarterly manual accessibility testing with screen readers (JAWS, NVDA, VoiceOver) and keyboard-only navigation
- Accessibility features:
  - All images have alt text (informative, not decorative)
  - All videos have captions and transcripts
  - Color contrast ≥4.5:1 for normal text, ≥3:1 for large text
  - Keyboard navigation for all interactive elements (no keyboard traps)
  - Screen reader compatibility (ARIA labels, semantic HTML)
- Accessibility statement: published statement disclosing compliance status, known issues, feedback mechanism

**Priority**: MUST_HAVE

**Traceability**: BR-005 (GDS Service Standard Point 2), SD-6 (GDS accessibility), architecture principle "Accessibility and Inclusive Design", O-3 (Public sector sales)

---

**NFR-C-004: Cyber Essentials Plus Certification**

**Description**: Platform MUST achieve Cyber Essentials Plus certification by Month 6 to enable UK public sector sales and demonstrate security posture to enterprise customers.

**Rationale**: Directly addresses BR-005 (GDS compliance) and SD-6. Cyber Essentials Plus is baseline security certification for UK Government suppliers. Demonstrates proactive security controls.

**Acceptance Criteria**:
- Cyber Essentials Plus assessment: external certification body conducts assessment (technical controls + penetration testing)
- Certification requirements:
  - Firewalls and network security configured
  - Secure configuration of systems (hardened servers, minimal services)
  - User access control (strong passwords, least privilege)
  - Malware protection (antivirus, endpoint detection)
  - Patch management (security patches applied within 14 days)
- Certification renewal: annual recertification required (maintain current certification)

**Priority**: MUST_HAVE

**Traceability**: BR-005 (Cyber Essentials Plus), SD-6 (GDS security), O-3 (Public sector sales), architecture principle "Security by Design"

---

**NFR-C-005: Algorithmic Transparency (ATRS for Public Sector)**

**Description**: Platform SHOULD publish Algorithmic Transparency Recording Standard (ATRS) record for course recommendation and search ranking algorithms when serving UK public sector customers.

**Rationale**: Addresses SD-6 (GDS responsible AI, TCoP Point 13) and architecture principle "Responsible AI and Algorithmic Transparency". UK Government requires ATRS for algorithmic decision-making systems affecting public sector users.

**Acceptance Criteria**:
- ATRS record published: includes algorithm purpose, data inputs, decision logic, performance metrics, bias testing, human oversight
- Transparency requirements:
  - Explain why course recommended ("Because you completed X, we recommend Y")
  - Disclose when AI is used (search ranking, recommendations)
  - Provide opt-out or manual alternatives (disable recommendations, use manual search)
- Bias testing: quarterly fairness audits (do certain providers get unfairly advantaged? do all user demographics receive equitable recommendations?)
- Human oversight: provider suspension, content removal require human review (algorithm flags, human decides)

**Priority**: SHOULD_HAVE (for public sector customers), MAY_HAVE (for commercial only)

**Traceability**: SD-6 (GDS TCoP Point 13, responsible AI), architecture principle "Responsible AI and Algorithmic Transparency", FR-041 (Recommendations)

---

## Data Requirements

### DR-001: Learner Personal Data

**Description**: Platform MUST store learner personal data (name, email, job role, employer) with UK GDPR compliance including encryption, access controls, and data subject rights.

**Data Elements**:
- Learner ID (UUID, primary key)
- Email (unique, required for authentication)
- First Name, Last Name (required)
- Job Role, Department (optional, for analytics and recommendations)
- Employer (optional, for enterprise-sponsored learners)
- Account Creation Date, Last Login Date

**Classification**: CONFIDENTIAL (PII under UK GDPR)

**Retention**: 7 years after last activity OR immediate deletion upon data subject request (right to erasure)

**Access Control**: Learners (own data), enterprise L&D managers (employee data if employer-sponsored), platform administrators (support, fraud investigation)

**Encryption**: AES-256 at rest, TLS 1.3 in transit

**Priority**: MUST_HAVE

**Traceability**: BR-004 (UK GDPR), NFR-C-001 (Data protection), NFR-SEC-002 (Encryption)

---

### DR-002: Enrollment and Progress Data

**Description**: Platform MUST store enrollment and learning progress data to track course completion, issue certificates, and enable enterprise reporting.

**Data Elements**:
- Enrollment ID (UUID, primary key)
- Learner ID (foreign key to DR-001)
- Course ID (foreign key to DR-004)
- Enrollment Date, Completion Date (nullable until completed)
- Progress (% course completed, 0-100%)
- Assessment Scores (JSON: quiz scores, timestamps)
- Time Spent (minutes, tracked per lesson)
- Certificate ID (generated upon completion)

**Classification**: CONFIDENTIAL (linked to learner identity)

**Retention**: 7 years (support credential verification, audit trails)

**Access Control**: Learners (own data), providers (aggregated data only, no individual learner identity), enterprise L&D (employee data), platform administrators

**Encryption**: AES-256 at rest, TLS 1.3 in transit

**Priority**: MUST_HAVE

**Traceability**: FR-043/044 (Progress tracking, certificates), BR-003 (Completion rate), SD-3 (Enterprise ROI)

---

### DR-003: Payment Transaction Data

**Description**: Platform MUST store payment transaction data for revenue tracking, provider payouts, refunds, and financial reporting. Comply with PCI DSS via tokenization (no card storage).

**Data Elements**:
- Transaction ID (UUID, primary key)
- Enrollment ID (foreign key to DR-002, nullable for non-enrollment payments)
- Learner ID / Enterprise ID (payer)
- Provider ID (payee)
- Amount (GBP, with currency code for multi-currency)
- Payment Method (card token, GOV.UK Pay reference, invoice reference)
- Transaction Status (pending, succeeded, failed, refunded)
- Payment Gateway Transaction ID (for reconciliation)
- Transaction Date, Refund Date (nullable)

**Classification**: CONFIDENTIAL (financial data)

**Retention**: 7 years (UK financial regulations, tax audit)

**Access Control**: Learners/enterprises (own transactions), providers (own revenue), finance team (all transactions), platform administrators (support, fraud investigation)

**Encryption**: AES-256 at rest, TLS 1.3 in transit

**Tokenization**: Payment card data NOT stored; use payment gateway tokens only

**Priority**: MUST_HAVE

**Traceability**: FR-042 (Payment), BR-006 (Revenue), NFR-C-002 (PCI DSS), SD-5 (Data protection)

---

### DR-004: Course Catalog and Content Metadata

**Description**: Platform MUST store course metadata (title, description, pricing, provider) and content references (video URLs, document URLs) for course discovery and delivery.

**Data Elements**:
- Course ID (UUID, primary key)
- Provider ID (foreign key to DR-005)
- Title, Description, Learning Objectives (text)
- Category, Subcategory, Tags (controlled vocabulary)
- Level (beginner, intermediate, advanced)
- Duration (hours), Language (ISO 639-1 code)
- Pricing (GBP, nullable for free courses)
- Content References (JSON: video URLs, document URLs, assessment URLs)
- Publication Status (draft, under review, published, unpublished)
- Average Rating, Total Enrollments (denormalized for performance)
- Created Date, Updated Date

**Classification**: PUBLIC (course catalog is public), INTERNAL (draft courses)

**Retention**: Indefinite (active courses), 2 years after unpublish (for analytics)

**Access Control**: Public (published courses), providers (own courses), platform administrators (all courses)

**Encryption**: TLS 1.3 in transit (at rest encryption optional for public data)

**Priority**: MUST_HAVE

**Traceability**: FR-002 (Course creation), FR-040 (Search), BR-001 (Course catalog growth)

---

### DR-005: Provider Business Data

**Description**: Platform MUST store provider business data (legal entity, tax ID, bank account) for KYC/AML validation, revenue payouts, and compliance.

**Data Elements**:
- Provider ID (UUID, primary key)
- Legal Entity Name, Business Type (limited company, sole trader, charity)
- Tax ID (UK VAT number, company registration number)
- Contact Person (name, email, phone)
- Address (street, city, postcode, country)
- Bank Account Details (account number, sort code, IBAN - encrypted)
- KYC/AML Status (pending, approved, rejected)
- Provider Status (active, suspended, terminated)
- Commission Tier (30%, 25%, 20% based on GMV)
- Created Date, Verification Date

**Classification**: CONFIDENTIAL (business PII, financial data)

**Retention**: 7 years after account termination (financial regulations, audit)

**Access Control**: Providers (own data), finance team (payout processing), compliance team (KYC/AML), platform administrators

**Encryption**: AES-256 at rest (especially bank account details), TLS 1.3 in transit

**Priority**: MUST_HAVE

**Traceability**: FR-001 (Provider registration), BR-001 (Provider onboarding), SD-2 (Provider revenue), SD-5 (Data protection)

---

### DR-006: Enterprise Customer and Employee Data

**Description**: Platform MUST store enterprise customer data (organization, contacts, contracts) and employee roster for subscription management and learner assignment.

**Data Elements**:
- Enterprise ID (UUID, primary key)
- Organization Name, Industry, Size (employees)
- Primary Contact (name, email, phone)
- Contract Details (subscription tier, license count, start date, end date, renewal terms)
- Billing Details (payment method, billing address, invoice recipient)
- Employee Roster (CSV import or API sync):
  - Employee Email (unique per enterprise)
  - Employee Name, Job Role, Department
  - Manager Email (for reporting hierarchy)
- License Utilization (consumed/available licenses)

**Classification**: CONFIDENTIAL (business data, employee PII)

**Retention**: 7 years after contract termination (financial regulations, audit)

**Access Control**: Enterprise admins (own organization data), sales team (contract management), finance team (billing), platform administrators

**Encryption**: AES-256 at rest, TLS 1.3 in transit

**Data Processing Agreement**: Platform is data processor for employee data; enterprise is data controller

**Priority**: MUST_HAVE

**Traceability**: FR-020/021 (Enterprise subscription, learner assignment), BR-002 (Enterprise customers), SD-3 (Workforce training), SD-5 (GDPR processor role)

---

### DR-007: Audit Logs

**Description**: Platform MUST store comprehensive audit logs for security monitoring, compliance audits, incident investigation, and data subject rights verification.

**Data Elements**:
- Log ID (UUID, primary key)
- Timestamp (ISO 8601 UTC)
- Event Type (authentication, authorization, data_access, configuration_change, data_subject_request)
- Actor (user ID, administrator ID, system process)
- Action (login_success, login_failure, read_learner_data, delete_user, change_permission)
- Resource (affected entity: learner ID, course ID, provider ID)
- IP Address, User Agent
- Result (success, failure, error code)
- Additional Context (JSON: request parameters, before/after values for changes)

**Classification**: CONFIDENTIAL (contains PII references)

**Retention**: 7 years (UK GDPR Article 32, security incident investigation, regulatory audit)

**Access Control**: Security team (SIEM analysis), compliance team (audit reviews), platform administrators (incident investigation)

**Encryption**: AES-256 at rest, TLS 1.3 in transit

**Immutability**: Append-only logs, no deletion/modification (cryptographic signing to prevent tampering)

**Priority**: MUST_HAVE

**Traceability**: NFR-SEC-005 (Audit logging), BR-004 (UK GDPR Article 32), SD-5 (ICO audit), architecture principle "Observability"

---

## Integration Requirements

### INT-001: GOV.UK Pay Integration

**Description**: Platform MUST integrate with GOV.UK Pay for payment processing from UK public sector users (civil servants, government employees).

**Rationale**: GOV.UK Pay is preferred payment gateway for UK public sector. Enables public sector sales (O-3: £500K public sector revenue). Simplifies procurement (pre-approved supplier).

**Integration Details**:
- Protocol: REST API (HTTPS)
- Authentication: API key authentication (secure vault storage)
- Payment flow: redirect to GOV.UK Pay hosted payment page → return to platform with transaction ID → webhook notification for payment confirmation
- Payment methods supported: debit/credit cards (UK-issued), Apple Pay, Google Pay
- Transaction fees: 1.5% + £0.05 per transaction (lower than commercial processors)

**Acceptance Criteria**:
- Payment initiation: create payment intent via GOV.UK Pay API, redirect learner to hosted payment page
- Payment confirmation: webhook handles payment status updates (success, failure, pending), updates enrollment status
- Refund processing: refund API integration, 14-day money-back guarantee support
- Reporting: reconciliation report integration (daily transaction export)
- Sandbox testing: integration tested in GOV.UK Pay sandbox environment
- Error handling: payment failures displayed to user with clear error messages, retry functionality

**Priority**: MUST_HAVE (for public sector sales), SHOULD_HAVE (for commercial-only)

**Traceability**: FR-042 (Payment), BR-005 (GDS compliance), O-3 (Public sector revenue)

---

### INT-002: Stripe Payment Integration

**Description**: Platform MUST integrate with Stripe for payment processing from commercial customers (enterprises, individual learners).

**Rationale**: Stripe is leading payment processor for online platforms, supporting wide range of payment methods, currencies, and fraud detection. Enables global expansion (Phase 2).

**Integration Details**:
- Protocol: REST API (HTTPS), Stripe.js client-side library
- Authentication: API key authentication (publishable key client-side, secret key server-side in vault)
- Payment flow: Stripe.js tokenizes card client-side → server creates payment intent → 3D Secure authentication (if required) → webhook confirms payment
- Payment methods: credit/debit cards, Apple Pay, Google Pay, bank transfers (future), subscriptions (for enterprise recurring billing)
- PCI compliance: Stripe handles card data (SAQ-A compliance for platform)

**Acceptance Criteria**:
- Payment tokenization: Stripe.js tokenizes cards client-side, platform never sees raw card data (PCI compliance)
- 3D Secure authentication: automatic triggering for transactions requiring SCA (Strong Customer Authentication per PSD2)
- Subscription billing: recurring billing for enterprise subscriptions (monthly/annual), automatic invoice generation
- Webhook handling: payment succeeded, payment failed, subscription renewed, subscription canceled, dispute created
- Fraud detection: Stripe Radar fraud signals integrated, high-risk transactions flagged for review
- Multi-currency (Phase 2): support GBP, USD, EUR pricing

**Priority**: MUST_HAVE

**Traceability**: FR-042 (Payment), BR-006 (Revenue), NFR-C-002 (PCI DSS), SD-2/3/4 (Stakeholder payment needs)

---

### INT-003: LMS Integration (SCORM/xAPI Export)

**Description**: Platform SHOULD support SCORM 1.2, SCORM 2004, and xAPI (Tin Can) export to enable enterprise customers to integrate course enrollments and completion data into their existing Learning Management Systems.

**Rationale**: Enterprise customers use existing LMS platforms (Cornerstone, SuccessFactors, Moodle). LMS integration eliminates manual data entry, enables consolidated reporting, and reduces enterprise IT burden. Supports SD-3 (enterprise ROI).

**Integration Details**:
- SCORM export: course packages exported as SCORM-compliant ZIP files, importable into enterprise LMS
- xAPI export: enrollment and completion events published as xAPI statements (JSON format), sent to enterprise Learning Record Store (LRS)
- Data exported: course title, learner ID, enrollment date, completion date, completion status (completed/incomplete), assessment scores, time spent

**Acceptance Criteria**:
- SCORM 1.2/2004 package generation: courses packaged with manifest (imsmanifest.xml), SCO files, completion tracking
- xAPI statement generation: enrollment events, progress events (% complete), completion events, assessment events
- LRS integration: xAPI statements sent to enterprise LRS endpoint (configurable per enterprise)
- Testing: SCORM packages validated in ADL SCORM test suite, xAPI statements validated with xAPI validator
- Documentation: integration guide for enterprise IT teams (how to import SCORM, configure LRS endpoint)

**Priority**: SHOULD_HAVE (Month 9+)

**Traceability**: FR-022 (Enterprise reporting), SD-3 (Enterprise integration), BR-002 (Enterprise adoption)

---

### INT-004: Identity Federation (SAML, OAuth, OIDC)

**Description**: Platform MUST support identity federation (SAML 2.0, OAuth 2.0, OpenID Connect) to enable enterprise SSO and GOV.UK One Login integration.

**Rationale**: Enterprise customers require SSO (Single Sign-On) for security and user experience. GOV.UK One Login is identity provider for UK public sector. Eliminates password management, reduces account takeover risk.

**Integration Details**:
- SAML 2.0: support for enterprise identity providers (Azure AD, Okta, ADFS)
- OAuth 2.0 / OpenID Connect: support for GOV.UK One Login, Google, Microsoft
- SSO flow: learner redirected to identity provider → authentication → SAML assertion or OAuth token returned → platform creates session
- Just-In-Time (JIT) provisioning: user account created automatically on first SSO login (if not exists)

**Acceptance Criteria**:
- SAML 2.0 SP (Service Provider) implementation: metadata exchange, assertion consumption, signed assertions
- OAuth 2.0 / OIDC implementation: authorization code flow, token validation, userinfo endpoint integration
- Multi-IDP support: platform supports multiple identity providers simultaneously (enterprise A uses Azure AD, enterprise B uses Okta)
- GOV.UK One Login: certified integration with GOV.UK One Login (for public sector users)
- Attribute mapping: identity provider attributes (email, name, department) mapped to platform user profile
- Testing: integration tested with major IDPs (Azure AD, Okta, Google, GOV.UK One Login)

**Priority**: MUST_HAVE (for enterprise and public sector sales)

**Traceability**: NFR-SEC-001 (Authentication), BR-002/005 (Enterprise and public sector sales), SD-3 (Enterprise security)

---

### INT-005: Email Service Integration (GOV.UK Notify, SendGrid)

**Description**: Platform MUST integrate with email service for transactional emails (enrollment confirmations, password resets, notifications) with GOV.UK Notify for public sector users and SendGrid for commercial users.

**Rationale**: Transactional emails are critical for user experience and security. GOV.UK Notify is preferred for public sector (pre-approved, free). SendGrid provides deliverability, analytics, and templates for commercial users.

**Integration Details**:
- GOV.UK Notify: REST API integration for public sector users (email templates managed in Notify portal)
- SendGrid: REST API integration for commercial users (email templates managed via SendGrid UI or API)
- Email types: enrollment confirmation, payment receipt, course completion, certificate issued, password reset, MFA codes, marketing (opt-in)

**Acceptance Criteria**:
- Email templates: professional HTML templates with platform branding, mobile-responsive
- Personalization: templates include learner name, course title, provider name, enrollment details
- Deliverability: SPF, DKIM, DMARC configured for email authentication (reduce spam risk)
- Bounce handling: hard bounces (invalid email) trigger account flag, soft bounces (mailbox full) retry
- Unsubscribe: marketing emails include one-click unsubscribe (GDPR requirement)
- Analytics: open rates, click rates tracked for optimization

**Priority**: MUST_HAVE

**Traceability**: FR-001/021/042/044 (Email notifications), BR-005 (GOV.UK Notify for public sector), SD-4 (Learner communication)

---

### INT-006: Analytics and Business Intelligence Integration

**Description**: Platform SHOULD integrate with analytics platform (Google Analytics, Mixpanel, or custom BI tool) for user behavior tracking, conversion optimization, and business intelligence.

**Rationale**: Analytics enable data-driven decisions (optimize conversion funnel, identify drop-off points, measure marketing ROI). Supports SD-1 (CEO data-driven growth), SD-2 (provider insights), SD-3 (enterprise ROI).

**Integration Details**:
- Google Analytics 4 (GA4): client-side tracking (page views, events, conversions) and server-side tracking (enrollment, payment)
- Mixpanel: event-based analytics (user actions, funnels, cohorts, retention)
- Custom BI: data warehouse integration (export platform data to Snowflake/BigQuery for custom analysis)

**Acceptance Criteria**:
- Event tracking: page views, search queries, course views, enrollment clicks, payment initiated, payment completed, course progress, course completion
- User attribution: marketing channel attribution (organic, paid search, referral, direct)
- Conversion funnels: track drop-off points (search → course view → enrollment → payment → completion)
- Privacy compliance: respect user consent (GDPR), anonymize IP addresses, provide opt-out
- Dashboards: real-time dashboards for key metrics (DAU, MAU, conversion rate, GMV, churn)

**Priority**: SHOULD_HAVE

**Traceability**: SD-1 (CEO growth metrics), SD-2 (Provider insights), architecture principle "Observability"

---

## Requirement Conflicts and Resolutions

### Conflict 1: Growth Speed (BR-001: 200 Providers) vs Quality Control (BR-003: 4.2+ Rating)

**Conflicting Requirements**:
- **BR-001**: Onboard 200+ providers by Month 12 to achieve platform liquidity
- **BR-003**: Maintain 4.2+ average course rating requiring rigorous quality review
- **FR-004**: Manual quality review with 3-day SLA creates bottleneck (capacity: 520 courses/year)

**Stakeholders Involved**:
- **CEO** (SD-1): Wants rapid provider onboarding for market leadership, network effects, investor traction
- **Head of Content Quality** (SD-8): Requires thorough quality review to maintain 4.2+ rating, prevent reputation damage
- **Enterprise Customers** (SD-3): Demand quality courses to achieve ROI, will churn if quality drops

**Trade-off Analysis**:
- **Option A - Speed First**: Minimal quality review, onboard rapidly → Risk: Low-quality courses damage reputation, customer churn (threatens O-2: 70% renewal)
- **Option B - Quality First**: Thorough review, slow onboarding → Risk: Insufficient course variety, customers don't join (threatens G-1: platform liquidity)
- **Option C - Balanced Phased Approach**: Start with curated providers (quality), scale with automated pre-screening → Balances speed and quality

**Resolution Strategy** (SELECTED: Option C - Phased Approach):

**Phase 1 (Months 1-6): Curated Quality Baseline**
- Manually vet 50 high-quality providers (universities, established institutions)
- Thorough quality review (5-7 business days per course)
- Establish quality baseline (target 4.5+ average rating for first 100 courses)
- Create case studies demonstrating quality for marketing

**Phase 2 (Months 7-12): Automated Pre-Screening**
- Implement automated content validation (FR-003): plagiarism, accessibility, malware, format checks
- Providers pass automated checks before human review (increases throughput to 20 courses/week)
- Reduce human review time (1-2 business days for pre-screened courses)
- Target 120 additional providers (220 total by Month 12 exceeds target)

**Phase 3 (Months 13-18): Tiered Review**
- Established providers (track record of 4.0+ ratings) get expedited review (<1 day)
- New providers get standard review (2-3 days)
- Continuous monitoring: pause provider if rating drops <3.5, require improvement or removal

**Continuous Quality Protection**:
- If platform average rating drops below 4.0 at any point, immediately pause new provider onboarding
- Conduct quality audit: remove bottom 10% of courses, implement stricter approval criteria
- Resume growth only after quality restored to 4.2+

**Decision Authority**: CEO (growth targets) and CPO (quality standards) jointly decide in monthly steering committee. Head of Content Quality has veto power if quality drops below 4.0 (non-negotiable quality floor).

**Stakeholder Communication**:
- **CEO**: Phased approach achieves growth target (200+ providers by Month 12) while protecting quality (sustains 4.2+ rating)
- **Content Quality**: Quality protected through curated Phase 1 and automated pre-screening in Phase 2; veto power if quality drops
- **Enterprise Customers**: Quality guaranteed through phased rollout; early phase provides high-quality curated courses
- **Providers**: Clear quality standards published; automated checks provide fast feedback; established providers rewarded with faster review

**Traceability**: Stakeholder analysis conflict resolution section, architecture principle "Maintainability and Evolvability" (phased approach enables learning and adaptation)

---

### Conflict 2: Platform Commission (BR-006: Revenue) vs Provider Margins (SD-2: Provider Revenue)

**Conflicting Requirements**:
- **BR-006**: Achieve £2M ARR requiring ~£8M GMV with 20-30% platform commission
- **SD-2**: Providers want to maximize revenue, resist high commission (reduces their 70-80% margin)

**Stakeholders Involved**:
- **CEO / Finance Director**: Need 20-30% commission to fund platform operations, achieve profitability, sustain growth
- **Training Providers** (SD-2): Want minimum commission to maximize revenue; compare to competitors (Udemy 50%, Coursera 70% for enterprise)
- **Investors**: Require sustainable business model with path to profitability

**Trade-off Analysis**:
- **Option A - High Commission (30% flat)**: Maximizes platform revenue → Risk: Providers resist, platform loses to lower-commission competitors
- **Option B - Low Commission (15% flat)**: Attracts providers → Risk: Platform unprofitable, cannot fund operations/growth
- **Option C - Tiered Commission**: Volume-based pricing rewards successful providers → Balances platform sustainability and provider incentives

**Resolution Strategy** (SELECTED: Option C - Tiered Commission):

**Commission Structure**:
- **Tier 1 (First £10K GMV)**: 30% commission (new providers, platform invests in customer acquisition)
- **Tier 2 (£10-50K GMV)**: 25% commission (established providers, proven course quality)
- **Tier 3 (£50K+ GMV)**: 20% commission (high-volume providers, retention incentive)

**Rationale**:
- Aligns incentives: providers benefit from growth (lower commission at higher volume)
- Platform revenue secured: majority of providers stay in Tier 1-2 (30-25% blended commission)
- Competitive positioning: effective commission competitive with marketplace norms (Udemy 50%, Amazon 15%, Coursera 70%)

**Value Justification** (Communicated to Providers):
Platform provides value worth 20-30% commission:
- **Customer acquisition**: Platform marketing, SEO, recommendations (providers avoid £500/customer acquisition cost)
- **Payment processing**: Integrated payment infrastructure (providers avoid 2-3% payment gateway fees + fraud management)
- **Customer support**: Platform handles learner support, refunds, technical issues (providers avoid support overhead)
- **Total cost comparison**: Platform 20-30% vs going direct (30% customer acquisition + 3% payment + 10% support = 43% total cost)

**Additional Incentives**:
- **Early adopters**: First 50 providers get 6 months at 20% commission (promotional incentive)
- **Quality bonus**: Providers maintaining 4.5+ rating get 2% commission discount
- **Volume rebates**: Annual rebate for providers exceeding £100K GMV (1-2% cashback)

**Decision Authority**: CEO and Finance Director set commission policy. CCO (Commercial Officer) can offer promotional discounts for strategic providers (limit: 5% discount, max 12 months).

**Stakeholder Communication**:
- **Providers**: Tiered commission explained as "fair pricing" (pay less as you earn more), value justification document provided comparing total cost vs going direct
- **CEO/Finance**: Commission structure achieves revenue target (£2M ARR from £8M GMV with blended 25% commission = £2M platform revenue)
- **Investors**: Tiered model shows path to profitability while remaining competitive for provider acquisition

**Traceability**: Stakeholder analysis conflict "Platform Commission vs Provider Margins", BR-006 (Revenue sustainability)

---

### Conflict 3: Feature Velocity (SD-1: CEO Speed) vs Technical Debt (SD-7: CTO Reliability)

**Conflicting Requirements**:
- **SD-1**: CEO wants rapid feature releases to compete, demonstrate progress to investors, achieve market leadership
- **SD-7**: CTO needs time to build reliable, scalable architecture, reduce technical debt, prevent outages
- **BR-007**: 99.9% uptime requires engineering investment in reliability (conflicts with feature velocity)

**Stakeholders Involved**:
- **CEO**: Pressure from investors for growth metrics, competitive threats require fast innovation
- **CTO**: Accountable for platform reliability, security, scalability; technical debt creates outages and security vulnerabilities
- **Enterprise Customers**: Expect reliable platform; outages damage trust and cause churn (threatens O-2: 70% renewal)

**Trade-off Analysis**:
- **Option A - Speed Only**: Ship features fast, accumulate technical debt → Risk: Outages, security breaches, customer churn, platform collapse
- **Option B - Reliability Only**: Focus on platform stability, slow feature releases → Risk: Competitive disadvantage, lose customers to faster competitors
- **Option C - Balanced Allocation**: Fixed ratio of feature vs platform work → Sustainable velocity with controlled debt

**Resolution Strategy** (SELECTED: Option C - Balanced Allocation with Quality Gates):

**Engineering Allocation (Non-Negotiable)**:
- **70% Features**: Customer-facing features, business requirements, competitive parity
- **20% Platform/Infrastructure**: Scalability, reliability, security, observability improvements
- **10% Technical Debt Reduction**: Refactoring, test coverage, dependency updates, architecture improvements

**Quality Gates (Enforced via CI/CD)**:
- All releases MUST pass automated testing (unit, integration, security, performance)
- Zero critical security vulnerabilities (SAST, dependency scanning blocks deployment)
- Code review approval required (peer review, architectural review for significant changes)
- Production deployment requires runbook, monitoring, rollback plan

**Quarterly Planning**:
- CEO and CTO jointly prioritize features vs platform work in quarterly roadmap planning
- Explicit trade-off discussions: "If we prioritize feature X, we defer platform improvement Y - acceptable?"
- Data-driven decisions: use metrics (uptime, performance, deployment frequency, lead time) to inform allocation

**Incident-Driven Remediation**:
- Post-mortems for outages/incidents identify root causes (often technical debt)
- Allocate time to remediate root cause (not just symptom) after each incident
- Track technical debt inventory: estimate effort, prioritize by risk/impact

**Decision Authority**: CEO decides feature priorities (business value), CTO decides platform priorities (technical risk). Disputes escalated to board (rare). 70/20/10 allocation is non-negotiable (protects platform sustainability).

**Stakeholder Communication**:
- **CEO**: Balanced allocation enables sustainable velocity (avoid boom-bust cycle of rapid features → major outage → recovery)
- **CTO**: Protected time for reliability work prevents technical debt accumulation; quality gates prevent rushing broken code to production
- **Enterprise Customers**: Quality gates ensure reliable platform; quarterly planning balances innovation and stability
- **Investors**: Sustainable velocity creates predictable delivery, reduces risk of catastrophic outages

**Metrics to Monitor**:
- Deployment frequency (measure velocity): target 2-4 deployments/week
- Lead time (idea → production): target <2 weeks for small features
- Change failure rate (measure quality): target <15% (deployments causing outage/rollback)
- MTTR (Mean Time To Recovery): target <15 minutes for critical services

**Traceability**: Stakeholder analysis conflict "Feature Velocity vs Technical Debt", architecture principle "CI/CD", NFR-A-001 (Uptime)

---

### Conflict 4: Data Sharing (SD-3: Enterprise ROI) vs Data Protection (SD-5: ICO/Learner Privacy)

**Conflicting Requirements**:
- **SD-3**: Enterprise customers want detailed learner data (progress, assessment scores, time spent) to measure ROI and manage training programs
- **SD-5**: ICO and learners want data minimization and privacy protection; excessive data sharing violates UK GDPR
- **BR-004**: UK GDPR compliance requires lawful basis, data minimization, purpose limitation

**Stakeholders Involved**:
- **Enterprise Customers**: Need learner data to justify training investment, track completion, identify struggling employees
- **ICO**: Enforces UK GDPR; data sharing must have lawful basis and respect individual rights
- **Individual Learners**: Privacy expectations; may not want employer to see detailed activity (e.g., low quiz scores, time spent)

**Trade-off Analysis**:
- **Option A - Full Data Sharing**: Share all learner data with enterprise → Risk: GDPR violation (no lawful basis), learner backlash, ICO enforcement
- **Option B - No Data Sharing**: Aggregated data only, no individual-level detail → Risk: Enterprises cannot measure ROI, reduce adoption
- **Option C - Tiered Data Sharing with Consent**: Aggregated by default, individual-level with opt-in or employer-sponsored enrollment → Balances privacy and enterprise needs

**Resolution Strategy** (SELECTED: Option C - Tiered Data Sharing with Lawful Basis):

**Tier 1 - Aggregated Reporting (No Consent Required)**:
Enterprises receive aggregated data (no individual learner identity):
- Team/department average scores, completion rates, skill distribution
- Course popularity (enrollment counts, ratings)
- ROI metrics (aggregated skills applied to projects - self-reported surveys)
- Lawful basis: Legitimate interest (enterprise measures training effectiveness without identifying individuals)

**Tier 2 - Individual-Level Reporting (Employer-Sponsored Enrollment)**:
For employer-sponsored training (enterprise pays for employee enrollment):
- Enterprise is data controller, platform is data processor
- Platform shares individual learner data (name, progress, scores, completion) with enterprise
- Lawful basis: Contract (employer-employee relationship, training is work requirement)
- Transparency: Clear privacy notice to learner explaining data sharing with employer

**Tier 3 - Individual-Level Reporting (Learner Opt-In)**:
For self-enrolled learners (learner pays, not employer-sponsored):
- Learner can opt-in to share individual data with employer (voluntary)
- Opt-in mechanism: checkbox during enrollment or profile settings
- Lawful basis: Consent (explicit, informed, revocable)
- Transparency: Clear explanation of what data shared, with whom, why (e.g., "Share completion certificate with employer for reimbursement")

**Data Minimization**:
Even with lawful basis, limit data shared to minimum necessary:
- Share: course title, enrollment date, completion date, completion status, certificate
- Do NOT share: detailed quiz answers, time-of-day activity patterns, course browsing history (unless explicitly required and consented)

**Data Subject Rights**:
Learners retain GDPR rights even for employer-sponsored training:
- Right to access: view what data shared with employer
- Right to rectification: correct inaccurate data
- Right to erasure: limited (can request deletion after employment ends, if no legal obligation to retain)
- Right to object: can object to processing (may impact employment, not platform decision)

**Decision Authority**: Head of Compliance (lawful basis determination), informed by legal counsel. Enterprise contracts specify data sharing terms. Platform privacy policy published transparently.

**Stakeholder Communication**:
- **Enterprise Customers**: Aggregated data sufficient for most ROI measurement; individual-level data available for employer-sponsored enrollments (lawful)
- **ICO**: Tiered approach respects data minimization, purpose limitation; lawful basis documented for each tier
- **Learners**: Transparent privacy notices explain data sharing; opt-in control for self-enrolled learners
- **CPO**: Data sharing model enables enterprise ROI measurement while maintaining GDPR compliance (no enforcement risk)

**Traceability**: Stakeholder analysis conflict "Data Sharing vs Privacy", BR-004 (UK GDPR), DR-006 (Enterprise employee data), NFR-C-001 (GDPR compliance)

---

## Requirements Traceability Matrix

| Requirement ID | Requirement Summary | Stakeholder Driver | Stakeholder Goal | Stakeholder Outcome | Architecture Principle | Priority |
|----------------|---------------------|--------------------|--------------------|---------------------|------------------------|----------|
| BR-001 | Platform Liquidity - 200 Providers | SD-1 (CEO), SD-2 (Providers) | G-1 (200 providers, 50 enterprises) | O-1 (10K enrollments) | Multi-Tenancy, Scalability | MUST |
| BR-002 | Platform Liquidity - 50 Enterprises | SD-1 (CEO), SD-3 (Enterprises) | G-1 (Platform liquidity) | O-2 (70% renewal, +20 NPS) | Multi-Tenancy, Interoperability | MUST |
| BR-003 | Course Quality 4.2+ Rating | SD-3 (ROI), SD-4 (Learners), SD-8 (Quality) | G-2 (4.2+ rating, 75% completion) | O-2 (Customer satisfaction) | Responsible AI, Quality | MUST |
| BR-004 | UK GDPR Compliance | SD-5 (ICO) | G-3 (GDPR by Month 6) | O-3 (Zero enforcement) | Data Sovereignty, Security | MUST |
| BR-005 | GDS Service Standard | SD-6 (GDS) | G-3 (GDS alpha pass) | O-3 (£500K public sector) | Accessibility, Security | MUST |
| BR-006 | £2M ARR by Month 24 | SD-1 (CEO), SD-2 (Providers) | G-4 (Revenue) | O-1 (Enrollment volume) | Scalability, Reliability | MUST |
| BR-007 | 99.9% Uptime | SD-7 (CTO) | G-3 (Compliance) | O-2 (Reliability supports retention) | Resilience, Availability | MUST |
| FR-001 | Provider Registration | SD-2 (Provider access) | G-1 (Provider onboarding) | O-1 (Platform liquidity) | Loose Coupling | MUST |
| FR-002 | Course Creation | SD-2 (Content publishing) | G-1 (Course catalog growth) | O-1 (Course variety) | Maintainability | MUST |
| FR-003 | Automated Validation | SD-8 (Quality) | G-2 (Quality standards) | O-2 (Quality protection) | Responsible AI | MUST |
| FR-004 | Quality Review | SD-8 (Manual review) | G-2 (4.2+ rating) | O-2 (Quality assurance) | - | MUST |
| FR-005 | Provider Dashboard | SD-2 (Analytics) | G-1 (Provider retention) | O-1 (Provider engagement) | Observability | MUST |
| FR-020 | Enterprise Subscription | SD-3 (Bulk licensing) | G-1 (Enterprise acquisition) | O-2 (Renewal revenue) | Multi-Tenancy | MUST |
| FR-021 | Bulk Learner Assignment | SD-3 (Workforce training) | G-2 (Completion tracking) | O-2 (ROI measurement) | Interoperability | MUST |
| FR-022 | Progress Tracking | SD-3 (ROI reporting) | G-2 (75% completion) | O-2 (70% renewal) | Observability | MUST |
| FR-040 | Course Search | SD-4 (Discovery) | O-1 (Enrollments) | O-1 (Search conversion) | Performance | MUST |
| FR-041 | Recommendations | SD-4 (Personalization) | O-1 (Organic growth) | O-1 (80% organic) | Responsible AI | SHOULD |
| FR-042 | Payment Processing | SD-3/4 (Enrollment) | G-4 (Revenue) | O-1 (GMV) | Security, Interoperability | MUST |
| FR-043 | Content Delivery | SD-4 (Learning) | G-2 (Completion) | O-2 (Learner satisfaction) | Performance, Accessibility | MUST |
| FR-044 | Certificates | SD-3/4 (Credentials) | G-2 (Completion proof) | O-2 (ROI, career advancement) | - | MUST |
| FR-045 | Reviews and Ratings | SD-3/8 (Quality feedback) | G-2 (Quality loop) | O-2 (Trust, quality improvement) | Responsible AI | MUST |
| NFR-P-001 | API Response Time | SD-7 (Performance) | G-3 (Operational excellence) | O-2 (User experience) | Performance and Efficiency | MUST |
| NFR-P-002 | Search Performance | SD-4 (Discovery speed) | O-1 (Conversion) | O-1 (Enrollment volume) | Performance | MUST |
| NFR-P-005 | Concurrent Users | SD-7 (Scalability) | G-1 (Growth support) | O-1 (10K enrollments) | Scalability and Elasticity | MUST |
| NFR-SEC-001 | Authentication | SD-7 (Security) | G-3 (Security controls) | O-3 (Zero breaches) | Security by Design | MUST |
| NFR-SEC-002 | Encryption | SD-5/7 (Data protection) | G-3 (GDPR Article 32) | O-3 (Compliance) | Security by Design | MUST |
| NFR-A-001 | Uptime SLA | SD-7 (Reliability) | G-3 (99.9% uptime) | O-2 (Customer trust) | Availability and Reliability | MUST |
| NFR-S-001 | Horizontal Scaling | SD-7 (Scalability) | G-1 (Growth) | O-1 (Support 50K users) | Scalability and Elasticity | MUST |
| NFR-C-001 | UK GDPR | SD-5 (ICO) | G-3 (GDPR by Month 6) | O-3 (Zero enforcement) | Data Sovereignty | MUST |
| NFR-C-003 | WCAG 2.2 AA | SD-6 (GDS accessibility) | G-3 (Service Standard) | O-3 (Public sector sales) | Accessibility | MUST |
| NFR-C-004 | Cyber Essentials Plus | SD-6 (GDS security) | G-3 (Certification) | O-3 (Public sector) | Security by Design | MUST |
| DR-001 | Learner Personal Data | SD-5 (GDPR) | G-3 (Data protection) | O-3 (Compliance) | Data Sovereignty | MUST |
| DR-002 | Enrollment Data | SD-3/4 (Progress tracking) | G-2 (Completion) | O-2 (ROI measurement) | Data Quality | MUST |
| DR-003 | Payment Transactions | SD-1 (Revenue) | G-4 (£2M ARR) | O-1 (GMV tracking) | Data Sovereignty, Security | MUST |
| INT-001 | GOV.UK Pay | SD-6 (Public sector payment) | G-3 (Public sector sales) | O-3 (£500K revenue) | Interoperability | MUST |
| INT-002 | Stripe | SD-2/3/4 (Payment) | G-4 (Revenue processing) | O-1 (GMV) | Interoperability | MUST |
| INT-004 | Identity Federation | SD-3/6 (SSO) | G-3 (Enterprise/public sector) | O-2/O-3 (Adoption) | Interoperability, Security | MUST |

---

**Generated by**: ArcKit `/arckit.requirements` command
**Generated on**: 2026-01-26 10:30 GMT
**ArcKit Version**: 0.11.1
**Project**: AI Training Marketplace (Project 001)
**AI Model**: claude-opus-4-5-20251101
**Generation Context**: Requirements derived from stakeholder drivers (ARC-001-STKE-v1.0) and architecture principles (ARC-010-PRIN-v1.0). Updated to match latest template structure.
