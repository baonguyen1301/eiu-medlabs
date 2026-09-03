# Documentation Authority and Precedence

This document defines the canonical documentation hierarchy, authority order, repository ownership, runtime contracts, and tool navigation policy for MedLabs Calendar (`eiu-medlabs`).

---

## 1. Document Precedence Hierarchy

When requirements, rules, guidelines, or historical records conflict, resolve authority in this strict order:

1. **Explicit current user instruction**
   - The user's direct, explicit instruction in the active session takes immediate precedence over written guidelines.
2. **Current source code + declarative schemas/migrations + tests + observable runtime**
   - Concrete implementation state, database schema, RLS policies, security functions, test suites, and verified runtime behavior govern all implementation facts.
3. **`AGENTS.md` (and `.omp/AGENTS.md`)**
   - Primary agent governance, workflows, safety guardrails, router policies, and repository engineering rules.
4. **Current business/security contracts and verified operational runbooks present in the active checkout**
   - Authorization rules, role contracts, domain isolation boundaries, and operational runbooks present in this repository checkout.
5. **`docs/UI_DESIGN_SYSTEM_V2_MASTER.md`**
   - Canonical visual and design-system authority. Defines brand colors, typography, layout models, component variants, spacing, radii, shadows, and interaction tokens.
6. **UI Modernization continuity system (`docs/ui-modernization/`)**
   - `DECISIONS.md`, `CURRENT.md`, `TRACKER.md`, `WORKLOG.md`, and `MASTER-PLAN.md` own current task status, batch history, and modernization decisions.
7. **Current OpenSpec scoped contracts (`openspec/`)**
   - Active change proposals, formal feature specifications, and scoped capability schemas.
8. **Onboarding and how-to documentation (`README.md`, etc.)**
   - Developer environment setup, local runtime instructions, and general repository overview.
9. **Dated audits, reviews, handoffs, and checkpoints**
   - `docs/ui-modernization/audits/`, legacy review guides, checkpoint files, and dated logs serve as historical evidence only. They cannot override current source, active tracker state, or canonical UI authority.

---

## 2. Repository and Branch Ownership

- **Canonical UI Modernization Repository:** `baonguyen1301/eiu-medlabs`
- **Active UI Modernization Branch:** `ui-modernization`
- **Base / Upstream Reference (`baonguyen-kobe/eiu-medlabs`):**
  - Historical and operational reference only when needed.
  - It is **NOT** the active UI-modernization delivery target.
  - Legacy documents or historical branches in the fork cannot override newer canonical UI specifications in `baonguyen1301/eiu-medlabs`.

---

## 3. Runtime Roles and Capability Contracts

The authoritative runtime roles in `public.app_role` and `user_roles` are:

- `admin`
- `staff`
- `teaching_assistant`
- `lecturer`
- `viewer`

### Schedule Import Capability

- Schedule import is **NOT** a standalone runtime role.
- It is governed by the `profiles.can_import_schedules` boolean capability combined with a supported role (`admin`, `staff`, `lecturer`, `teaching_assistant`) and room-type scope.
- Legacy "Importer" terminology in older documents is strictly for historical compatibility and must not be used as an independent primary role.

---

## 4. Codebase Navigation Policy

Use the smallest sufficient navigation method for the task:

1. **Direct inspection and search (`read`, `grep`, `glob`):**
   - Default for localized, surgical edits, single-component changes, and straightforward investigations.
2. **GitNexus (`gitnexus-code-intelligence` MCP / CLI):**
   - Use when repository-level architecture, multi-file dependency tracing, caller graphs, shared consumers, or blast radius analysis is useful.
   - Do not require GitNexus for localized edits.
3. **Graphify:**
   - Optional when `graphify-out/graph.json` exists and is current.
   - Never mandatory before codebase exploration or localized edits.
4. **Version-matched Next.js guidance (`NEXTJS_AGENTS.md`):**
   - Read `NEXTJS_AGENTS.md` before changing Next.js behavior to reference documentation bundled with the installed framework version.

---

## 5. UI Authority and Supplemental References

- **Canonical Visual Authority:** `docs/UI_DESIGN_SYSTEM_V2_MASTER.md`
  - Defines the authoritative EIU MedLabs design system: Be Vietnam Pro typography, EIU blue/gold/cream color tokens, surface elevations, card geometry, and component variants.
- **Continuity and State Authority:** `docs/ui-modernization/` (`DECISIONS.md`, `CURRENT.md`, `TRACKER.md`)
  - Governs active modernization tasks, verified mobile strategies (Strategies A–F), and batch history.
- **Supplemental Legacy Layout Reference:** `docs/UI_LAYOUT_SPEC.md`
  - Supplemental reference for calendar grid details and historical layout context. Cannot override the UI Master or modernization decisions.
- **Supplemental Review Checklist:** `docs/UI_REVIEW_GUIDE.md`
  - Supplemental checklist for manual visual reviews. Cannot override current source, server RLS, or UI Master rules.

---

## 6. Historical Documents and Archive Policy

- Historical audit files and review notes document past findings and must not be treated as active task lists or authoritative design rules.
- Durable rules must be migrated to `UI_DESIGN_SYSTEM_V2_MASTER.md`, `DOCUMENTATION_AUTHORITY.md`, or `AGENTS.md`.
- Bulk cleanup, archiving, or deletion of historical artifacts is performed in dedicated docs-only maintenance tasks, never mixed into visual feature delivery.

---

## 7. Production Verification Disclaimer

- Documentation alone **never** constitutes proof of live production state.
- Production status requires explicit release SHA verification, live application inspection, verified remote migration history, and current operational configuration.
