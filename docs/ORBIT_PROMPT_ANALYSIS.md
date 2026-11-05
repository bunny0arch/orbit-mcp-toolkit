# ORBIT Hackathon Prompt — Structured Analysis

**Source:** User-provided `OrbitAI.txt` (3,134 lines).  
**Purpose:** Preserve the product requirements and implementation priorities as context for the MCP toolkit and future ORBIT work. This is an analysis, not an implementation report.

## Product definition

ORBIT (Career Intelligence & Skill Evolution Engine) is a student career-development platform for Agentic AI Hackathon 2.0, Track 3 — Research & Student Development, Problem Statement 15 — AI Student Skill Gap and Certification Recommendation Agent. VFSTR is the primary institutional context, while the product remains open to students elsewhere. The current primary deliverable is a functional web application; Android is a future client of the same backend, identity, and synchronized data.

The product should help a student understand: (1) current capabilities, (2) strength of supporting evidence, (3) what is missing for a target career/certification, (4) what to do next, and (5) how readiness changes over time.

The defining loop is: **discover goal → assess capabilities → identify evidence-backed gaps → plan learning → complete missions → submit evidence → update skill profile → reassess readiness.** The system must never imply that an AI score guarantees employment, internship selection, or certification eligibility.

## Core experience and P0 acceptance

The prompt's P0 list is the minimum valid prototype: login-first authentication; username/password registration; persistent, editable student profile; technical/professional skills and evidence; certifications and optional private proof uploads; basic skill assessment; at least five sourced role templates; role comparison and explainable gap analysis; AI recommendations for courses/certifications; personalized ordered roadmaps with resources; progress tracking; certification/achievement tracking; a real-data dashboard; secure persistence; VFSTR context; responsive web UX; and shared-backend/API architecture ready for Android.

Every visible action should work and persist. Returning users should not repeat onboarding. Metrics must derive from actual user records. Unsupported resources, institutional data, credentials, job requirements, and opportunities must not be fabricated.

## Evidence model and career intelligence

Skills are structured records, not keywords. A skill can be self-reported, assessed, demonstrated, validated by an authorized reviewer, or submitted/pending; provenance and history must be preserved. A completed quiz or roadmap task must not silently turn a skill into a validated capability.

Career readiness must use deterministic, documented application logic. The prompt offers configurable evidence multipliers as prototype assumptions (claimed 0.20, assessed 0.55, demonstrated 0.75, validated 1.00) and a transparent weighted coverage formula. AI may explain results but must not invent numeric scores. Mandatory eligibility (degree, graduation year, branch, experience, location, authorization, deadlines) is checked separately as pass/fail/unknown and cannot be overridden by a high skill score. Scores are estimates against defined requirements, not hiring probabilities.

At least five career-role templates need structured requirements, credible source references, versioning, and a review date. Multiple roles should be comparable. The Career Time Machine should recalculate hypothetical scenarios without mutating canonical profile records, awarding badges, or recording completed credentials.

## AI and source trust

The Career Brain is a contextual assistant using authorized profile, skill, evidence, assessment, project, certification, target-role, roadmap, and progress data. Important answers should include direct advice, student-specific reasoning, skills considered, requirement comparison, supporting sources, uncertainty, and the next action.

The RAG feature must ingest approved official/provider/employer/institutional sources; preserve document metadata and versions; retrieve source passages; validate citations against actual retrieved passages; and say when information is unavailable, conflicting, or outdated. Retrieved text is untrusted input and cannot override permissions or system instructions. Structured AI outputs must be schema-validated server-side before affecting persistent records. AI failure must not make the core product unusable.

## Roadmaps, evidence, progress, and motivation

Roadmaps should adapt to the student's demonstrated capabilities and define ordered stages and measurable tasks with resources, target proficiency, effort, deliverable, prerequisites, validation method, and completion criteria. Progress, history, evidence, notes, and previous versions must persist; changes should be proposed and explained, not silently overwrite completed work. Missions and XP can motivate but do not prove competence. Achievements unlock only when deterministic criteria are met, and duplicates are prevented.

Projects can provide evidence. A bounded public-repository analyzer may inspect selected public README/manifests/source/tests and return candidate skills with exact evidence paths/snippets, confidence, inspected scope, unknowns, and limitations. The student must confirm extracted skills. Private repository access needs explicit narrow authorization.

Opportunity listings require source URLs and checked dates, and eligibility must allow an unknown state when data is incomplete. Seeded/curated data must not be presented as a live integration.

## Security, data, and platform architecture

The suggested architecture is React + TypeScript + Vite and a modular FastAPI/Pydantic API over Supabase PostgreSQL/Auth/RLS/private Storage, with a server-side AI adapter and pgvector where useful. The backend is the source of truth; future React Native/Expo Android should use the same stable contracts, identity, database, and storage.

Security requirements include server-side username-to-auth identity mapping (not client-side password auth), secure sessions, RLS on all user-owned data, ownership checks, role-protected admin/reviewer access, private authenticated file storage, safe signed URLs, consent and data minimization, validated AI tools/outputs, prompt-injection resistance, auditability, and explicit cross-user/file access tests. No real VFSTR private systems or student data may be assumed; institutional information must be verified/authorized, and sample data labeled.

## UI and component sourcing

Dark-first, restrained, high-contrast, responsive, accessible design. Avoid generic AI-SaaS layouts, decorative clutter, fake data, excessive animation, or dead controls. React Bits is mandated as the primary free component source, with other listed libraries considered as fallback after verifying licensing/free availability. Track every sourced component in `COMPONENTS.md`.

## Delivery sequence and differentiators

The prompt explicitly favors a complete, dependable student workflow over many incomplete pages.

- **P0:** Reliable core profile/skills/evidence/assessment/roles/recommendations/roadmap/progress/certifications/achievements/dashboard and secure persistence.
- **P1:** Skill Genome visualization, projects and compiler, Career Time Machine, citation-backed RAG, Opportunity Radar, advanced assessment, adaptive roadmaps/missions, notifications, admin/evidence review, privacy-safe institutional analytics.
- **P2:** Mock interviews, advanced orchestration/analytics/opportunity ingestion, Android client, and other extensions. Mock interviews and Android implementation are not initial blockers.

The three explicit differentiators are (1) evidence-backed Skill Genome, (2) safe hypothetical Career Time Machine, and (3) RAG Career Brain with traceable citations, uncertainty, and personalization.

## Highest delivery risks

1. **Excessive scope:** dozens of routes and modules can displace the end-to-end P0 workflow; prioritize one student journey first.
2. **Username authentication:** secure username mapping to Supabase Auth is more complex than a login form; it needs server-side handling, race-safe uniqueness, anti-enumeration, and account recovery.
3. **Evidence semantics:** claimed, assessed, demonstrated, and validated must remain distinct across all scoring, dashboards, badges, and recommendations.
4. **Source quality/freshness:** role/certification/opportunity advice requires validated sources, citations, and dates, not generated links.
5. **Security and privacy:** RLS, private uploads, admin boundaries, and cross-user tests need early design.
6. **AI reliability:** deterministic scoring/state transitions and validated structured outputs are essential; AI must not control authorization or make unsupported claims.
7. **Hackathon demo readiness:** a repeatable, labeled, consented demo account and persistent end-to-end workflow are more valuable than mock screens.

## Implementation boundary

No ORBIT code, deployment, database, account, or project resource has been created as part of preparing this analysis. Future implementation must use the user's explicit next task and actual environment authorization. The prompt's deliverables and acceptance criteria should be maintained as a traceable checklist during that work.
