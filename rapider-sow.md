<!-- Rapider Official App SOW & Specification | App #100: Data Governance & Catalog (data-governance) | Domain: DAT -->

# #100 Data Governance & Catalog (`data-governance`) — Scope of Work (SOW)

- **App Number & Slug:** `#100` / `100-data-governance-and-catalog`
- **Proposed Rapider App Key:** `data-governance`
- **Suite / Domain Key:** `DAT` (Data, Analytics & Business Intelligence Suite — `Dat*` Canonical Prefix)
- **Representative Product (`P1`):** Alation
- **Combined Feature Catalog Reference:** [../combined-features/100-data-governance-and-catalog-features.md](../combined-features/100-data-governance-and-catalog-features.md)

---

## 1. Executive Outcome & Target Audience

`data-governance` is the Active Metadata Catalog, Business Glossary, End-to-End Column Lineage, Data Quality Observability, Privacy Classification, and AI Context Governance control plane for the entire Rapider platform. Without centralized governance, analysts waste hours hunting for trustworthy tables, compliance officers cannot prove GDPR/HIPAA PII lineage, upstream ETL changes silently break executive dashboards, and conversational AI agents risk grounding responses on deprecated or restricted data. `data-governance` unifies discovery (`DatCatalogAsset`), semantic alignment (`DatBusinessGlossaryTerm`), lineage (`DatLineageEdge`), quality rules (`DatDataQualityRule`, `DatQualityIncident`), and active policy pushdown (`DatClassificationTag`, `DatDataAccessPolicy`, `DatStewardshipRequest`).

- **SME Fast-Path Defaults:** Mid-sized organizations immediately get an auto-populated searchable catalog across all active Rapider suites (`CRM`, `FIN`, `HR`, `OPS`, `SUP`) and `DAT` tables, prebuilt PII/PCI/PHI sensitivity tags, out-of-the-box completeness/uniqueness checks, and clear `ENDORSED / DEPRECATED` badges without complex metamodel setup.
- **Enterprise Progressive Disclosure:** Regulated enterprises unlock formal domain stewardship mapped to `HrDepartment` and `HrEmployee`, redlined glossary approval workflows via Home `WorkItem`s, automated column-level tag propagation over OpenLineage graphs, dynamic masking pushdown into `#099`/`#096`/`#097`, time-bound Data Product access shopping, GDPR Article 30 RoPA registers, and `AI_GROUNDING_APPROVED` context certification.
- **Measurable Success Outcomes:**
  - `100%` automated PII classification scan coverage across registered `#099` warehouse tables and `#098` sync streams.
  - Sub-second downstream blast-radius impact calculation before breaking schema or metric changes deploy.
  - Zero unapproved AI grounding on `DEPRECATED` or unmasked `RESTRICTED_PII` assets.
- **Top 6 Global Benchmarks Synthesized:** `P1` Alation, `P2` Collibra Data Intelligence, `P3` Atlan, `P4` Microsoft Purview, `P5` Informatica CDGC, and `P6` SAP Datasphere Catalog & MDG.

---

## 2. In-Scope, Out-of-Scope & Suite Ownership Boundaries

### In-Scope
1. Active metadata catalog (`DatCatalogAsset`) indexing warehouse tables, BI dashboards/metrics, ETL pipelines, event schemas, and canonical Rapider suite collections with popularity rankings, trust flags, and `AI_GROUNDING_APPROVED` certification.
2. Hierarchical Business Glossary (`DatBusinessGlossaryTerm`) with Steward redline review workflows and term-driven security policy inheritance.
3. Automated technical and column-level lineage graphs (`DatLineageEdge`), blast-radius impact analysis, and upstream quality warning propagation.
4. 6-dimension Data Quality rule authoring (`DatDataQualityRule`), `0–100%` `Decimal128` asset trust scoring, and incident triage (`DatQualityIncident`) integrated with Home `WorkItem`s.
5. Sensitivity classification taxonomy (`DatClassificationTag`), centralized dynamic masking/row-access policy authoring (`DatDataAccessPolicy`), GDPR RoPA reporting, and time-bound Data Product access requests (`DatStewardshipRequest`).

### Out-of-Scope
1. Physical SQL query execution and compute cluster management — owned by `#099 Data Warehouse & Analytics Platform` (`data-warehouse`), which enforces `#100` policies at runtime.
2. CDC extraction connectors and transformation pipeline execution — owned by `#098 Data Integration / ETL` (`data-integration`).
3. Executive BI visual chart authoring and scheduled report subscriptions — owned by `#096 Business Intelligence & Dashboards` (`bi-dashboards`).
4. Corporate HR organizational chart master maintenance — owned by `HR` (`employees`), referenced read-only via `HrDepartment` and `HrEmployee`.

### Cross-Suite Ownership & Integration Contract

| Domain / App | Owns (Single Source of Truth) | Integration Contract with `data-governance` (`#100`) |
| :--- | :--- | :--- |
| **`data-governance` (`#100`)** | `DatCatalogAsset`, `DatBusinessGlossaryTerm`, `DatLineageEdge`, `DatDataQualityRule`, `DatQualityIncident`, `DatClassificationTag`, `DatDataAccessPolicy`, `DatStewardshipRequest` | Publishes active metadata descriptions, PII classifications, dynamic masking policies, and trust/incident badges across the `DAT` suite. |
| **`#099` Data Warehouse (`data-warehouse`)** | `DatDatabaseCatalog`, `DatWarehouseTable`, `DatQueryExecution` | Emits schema DDL changes & query popularity telemetry to `#100`; enforces `DatDataAccessPolicy` column masking and row filters at SQL runtime. |
| **`#098` Data Integration (`data-integration`)** | `DatSyncPipeline`, `DatTransformationModel` | Streams column-level `DatLineageEdge` events and inline test failures (`DatQualityIncident`) into `#100`; honors `DatClassificationTag` upstream hashing rules. |
| **`#096` BI & `#097` Product Analytics** | `DatSemanticModel`, `DatMetricDefinition`, `DatDashboard`, `DatEventPropertySchema` | Links metrics to `DatBusinessGlossaryTerm`; renders `#100` trust/incident banners on dashboards; gates conversational AI on `AI_GROUNDING_APPROVED` assets. |
| **`HR` (`employees`)** | `HrDepartment`, `HrEmployee` | Read-only linkage for Domain Ownership (`HrDepartment`) and named Business Owners / Data Stewards (`HrEmployee`). |

---

## 3. Primary Web Pages & Sidebar Navigation Architecture (12 Pages)

All visible sidebar sections enforce **`>= 3` visible items (`displayOnMenu: true`)**, while detail views and drawers set `displayOnMenu: false`.

| # | Route | Page Title | Sidebar Section | Menu Visible | Key Components & UX |
| :--- | :--- | :--- | :--- | :--- | :--- |
| 1 | `governance-posture` | Governance & Trust Hub | `Catalog & Glossary` | `true` (Order 1) | Estate trust score (`Decimal128`), PII scan coverage `%`, open `DatQualityIncident` summary, `AI_GROUNDING_APPROVED` counter, `"Ask Catalog"` drawer launcher. |
| 2 | `asset-catalog` | Data Catalog & Marketplace | `Catalog & Glossary` | `true` (Order 2) | Faceted `findSWR` search over `DatCatalogAsset`s (`TABLE`, `SEMANTIC_MODEL`, `DASHBOARD`, `PIPELINE`, `SUITE_ENTITY`), trust pills, `#activeFilterTagsBar` + `Clear all`, clickable asset name, icon+text `Edit`, icon-only `Delete`. |
| 3 | `business-glossary` | Business Glossary | `Catalog & Glossary` | `true` (Order 3) | Domain-grouped `DatBusinessGlossaryTerm` directory with `APPROVED / UNDER_REVIEW / DRAFT` pills, linked metrics count, and `Propose Term` button. |
| 4 | `lineage-impact` | Lineage & Impact Explorer | `Lineage & Quality` | `true` (Order 4) | Interactive column-level `DatLineageEdge` graph (`Source -> ETL -> Warehouse -> BI`), blast-radius simulator, and tabular lineage fallback. |
| 5 | `data-quality-rules` | Data Quality Rules | `Lineage & Quality` | `true` (Order 5) | 6-dimension `DatDataQualityRule` catalog with `Decimal128` pass-rate sparklines, target asset links, and `"Run Check Now"` action. |
| 6 | `quality-incidents` | Quality Incidents | `Lineage & Quality` | `true` (Order 6) | `DatQualityIncident` triage board (`<rapider-kanban>` + synchronized table view) across `OPEN -> INVESTIGATING -> MITIGATED -> RESOLVED` with `#activeFilterTagsBar`. |
| 7 | `classifications-privacy` | PII Tags & RoPA Privacy | `Privacy & Access` | `true` (Order 7) | `DatClassificationTag` taxonomy, automated PII scanner findings queue, and GDPR Article 30 Record of Processing Activities (RoPA) exportable register. |
| 8 | `access-policies` | Masking & Access Policies | `Privacy & Access` | `true` (Order 8) | Centralized `DatDataAccessPolicy` studio defining `FULL_REDACT`, `PARTIAL_MASK_LAST4`, `HASH_SHA256`, and row predicates pushed down to `#099`/`#096`. |
| 9 | `stewardship-requests` | Access & Steward Requests | `Privacy & Access` | `true` (Order 9) | `DatStewardshipRequest` ledger tracking time-bound Data Product access grants (`expiresAt`), glossary change requests, and linked Home `WorkItem` statuses. |
| 10 | `catalog-asset-detail` | Asset 360 Wiki & Column Profile | *(Hidden)* | `false` | Rich asset detail (`#/catalog-asset-detail?id=...`): Business/Technical Stewards, column dictionary + PII tags, trust score breakdown, mini-lineage, `"Request Access"`, and `Back to Catalog`. |
| 11 | `glossary-term-detail` | Glossary Term & Linked Assets | *(Hidden)* | `false` | Canonical prose definition (`#/glossary-term-detail?id=...`), redline revision history, inherited `DatDataAccessPolicy`, linked `#096` metrics, and `projectChannelMessage` discussion. |
| 12 | `governance-editor-drawer` | Glossary, Rule & Policy Drawer | *(Hidden)* | `false` | Sliding creation/edit drawer for `DatBusinessGlossaryTerm`, `DatDataQualityRule`, `DatDataAccessPolicy`, and `DatStewardshipRequest`; enforces `finally` button reset and `closePageDrawer()`. |

---

## 4. Canonical Data Models (`Dat*` — 8 Models)

All models omit `projectId`, use platform UUID `id` + optimistic `version`, store scores/thresholds as `Decimal128`, and use `00000000-xxxx-xxxx-xxxx-xxxxxxxxxxxx` seed UUIDs.

| Model Name | Key Fields & Types | Relationships & External Refs | Invariants & Lifecycle |
| :--- | :--- | :--- | :--- |
| **`DatCatalogAsset`** | `id: UUID`, `qualifiedName: string`, `displayName: string`, `assetType: enum(WAREHOUSE_TABLE, BI_SEMANTIC_MODEL, BI_DASHBOARD, ETL_PIPELINE, PRODUCT_EVENT, RAPIDER_SUITE_ENTITY, DATA_PRODUCT)`, `externalRecordId: UUID?`, `domainDepartmentId: UUID?`, `businessOwnerId: UUID?`, `technicalStewardId: UUID?`, `trustStatus: enum(ENDORSED, UNVERIFIED, WARNING, DEPRECATED)`, `aiGroundingApproved: boolean`, `qualityScorePct: Decimal128`, `popularityScore30d: int`, `columnsMetadataJson: object[]`, `ropaMetadataJson: object?`, `version: int` | `domainDepartmentId -> HrDepartment.id`; `businessOwnerId, technicalStewardId -> HrEmployee.id`; `externalRecordId` links to `#096/#097/#098/#099` record UUID. | `qualifiedName` unique per workspace. `aiGroundingApproved` can only be `true` when `trustStatus === 'ENDORSED'` and zero unresolved `CRITICAL` `DatQualityIncident`s exist. |
| **`DatBusinessGlossaryTerm`** | `id: UUID`, `termCode: string`, `name: string`, `synonyms: string[]`, `domainDepartmentId: UUID`, `definitionMarkdown: string`, `calculationGuidance: string?`, `defaultClassificationTagId: UUID?`, `status: enum(DRAFT, UNDER_REVIEW, APPROVED, RETIRED)`, `stewardEmployeeId: UUID`, `discussionChannelId: UUID?`, `version: int` | `domainDepartmentId -> HrDepartment.id`; `stewardEmployeeId -> HrEmployee.id`; `defaultClassificationTagId -> DatClassificationTag.id`; `discussionChannelId -> projectChannelMessage`. | Edits to an `APPROVED` term create a staged revision via `DatStewardshipRequest` until approved by `stewardEmployeeId`. |
| **`DatLineageEdge`** | `id: UUID`, `sourceAssetId: UUID`, `sourceColumn: string?`, `targetAssetId: UUID`, `targetColumn: string?`, `transformationType: enum(DIRECT_COPY, EXPRESSION, AGGREGATION, HASHED_ANONYMIZED, FILTER_JOIN)`, `producerPipelineOrModelId: UUID?`, `lastObservedAt: datetime`, `version: int` | `sourceAssetId, targetAssetId -> DatCatalogAsset.id`. | Self-loops `(sourceAssetId === targetAssetId && sourceColumn === targetColumn)` are forbidden; `HASHED_ANONYMIZED` breaks raw PII sensitivity inheritance while preserving provenance trace. |
| **`DatDataQualityRule`** | `id: UUID`, `ruleCode: string`, `name: string`, `assetId: UUID`, `targetColumn: string?`, `dimension: enum(COMPLETENESS, UNIQUENESS, VALIDITY, CONSISTENCY, TIMELINESS, VOLUME_ANOMALY)`, `predicateSpecJson: object`, `passThresholdPct: Decimal128`, `lastPassPct: Decimal128?`, `severity: enum(LOW, MEDIUM, HIGH, CRITICAL)`, `evaluationCron: string`, `isEnabled: boolean`, `version: int` | `assetId -> DatCatalogAsset.id`. | `passThresholdPct` bounded `0.00..100.00` (`Decimal128`). |
| **`DatQualityIncident`** | `id: UUID`, `incidentNumber: string`, `ruleId: UUID?`, `assetId: UUID`, `severity: enum(LOW, MEDIUM, HIGH, CRITICAL)`, `status: enum(OPEN, INVESTIGATING, MITIGATED, RESOLVED, FALSE_POSITIVE)`, `observedValuePct: Decimal128`, `impactedAssetCount: int`, `rootCauseNotes: string?`, `assigneeStewardId: UUID?`, `activeWorkItemId: UUID?`, `discussionChannelId: UUID?`, `openedAt: datetime`, `resolvedAt: datetime?`, `version: int` | `ruleId -> DatDataQualityRule.id`; `assetId -> DatCatalogAsset.id`; `activeWorkItemId -> Platform WorkItem.id`; `discussionChannelId -> projectChannelMessage`. | Opening a `CRITICAL` incident automatically sets parent `DatCatalogAsset.trustStatus = 'WARNING'`, pauses `aiGroundingApproved`, and emits upstream warning events to `#096`. |
| **`DatClassificationTag`** | `id: UUID`, `tagCode: string`, `name: string`, `sensitivityLevel: enum(PUBLIC, INTERNAL, CONFIDENTIAL, RESTRICTED_PII, RESTRICTED_PHI, RESTRICTED_PCI, FINANCIAL_MNPI)`, `detectorRegexes: string[]`, `autoPropagateLineage: boolean`, `defaultMaskingPolicyId: UUID?`, `version: int` | `defaultMaskingPolicyId -> DatDataAccessPolicy.id`. | System-seeded regulated tags (`RESTRICTED_PII`, `RESTRICTED_PHI`, `RESTRICTED_PCI`) cannot be hard-deleted. |
| **`DatDataAccessPolicy`** | `id: UUID`, `policyCode: string`, `name: string`, `policyType: enum(COLUMN_MASKING, ROW_FILTER)`, `maskStrategy: enum(NONE, FULL_REDACT, PARTIAL_MASK_LAST4, HASH_SHA256, NULLIFY)?`, `rowPredicateJson: object?`, `boundTagIds: UUID[]`, `exemptRoleKeys: string[]`, `isEnabled: boolean`, `version: int` | `boundTagIds -> DatClassificationTag.id[]`; enforced by `#099`, `#096`, `#097`. | Policy updates increment `version` and immediately publish `dat.governance.access_policy.updated.v1` to invalidate downstream query/BI caches. |
| **`DatStewardshipRequest`** | `id: UUID`, `requestNumber: string`, `requestType: enum(DATA_ACCESS_GRANT, GLOSSARY_APPROVAL, CLASSIFICATION_OVERRIDE, AI_GROUNDING_CERTIFICATION)`, `targetAssetId: UUID?`, `targetTermId: UUID?`, `requesterUserId: UUID`, `businessJustification: string`, `requestedDurationDays: int?`, `expiresAt: datetime?`, `status: enum(PENDING, APPROVED, REJECTED, EXPIRED, REVOKED)`, `reviewerUserId: UUID?`, `activeWorkItemId: UUID?`, `version: int` | `targetAssetId -> DatCatalogAsset.id`; `targetTermId -> DatBusinessGlossaryTerm.id`; `activeWorkItemId -> Platform WorkItem.id`. | `DATA_ACCESS_GRANT` approvals require `requestedDurationDays <= 365` and auto-transition to `EXPIRED` when `now >= expiresAt`. |

---

## 5. Core End-to-End User Journeys (5 Journeys)

1. **Journey 1 — Automated PII Scan, Lineage Tag Propagation & Active Masking Pushdown:**
   - `#098` lands a new table `RAW.customer_kyc` into `#099`. `#100` harvests the `DatCatalogAsset` (`DGC-001`) and runs `DatClassificationTag` detectors (`DGC-023`), tagging `national_id` and `iban` as `RESTRICTED_PII`.
   - Through `DatLineageEdge` (`DGC-013`), `RESTRICTED_PII` automatically propagates to `MARTS.dim_customers.national_id`, binding the `PARTIAL_MASK_LAST4` `DatDataAccessPolicy` (`DGC-024`) and emitting `dat.governance.access_policy.updated.v1` so `#099` SQL worksheets and `#096` BI tiles mask the column immediately.
2. **Journey 2 — Data Product Discovery & Time-Bound Access Grant via Home `WorkItem`:**
   - A Revenue Analyst searches `"Net ARR"` on `asset-catalog`, filters by `Trust Status: "ENDORSED"` (`#activeFilterTagsBar` renders `Trust Status: "ENDORSED" ✕`), clicks `"Enterprise Revenue Data Product"` to open `#/catalog-asset-detail?id=...`, and clicks `"Request 90-Day Read Access"`.
   - Submitting `governance-editor-drawer` creates a `DatStewardshipRequest` (`PENDING`) and dispatches a Rapider Home `WorkItem` to the Finance Business Owner (`HrEmployee`).
   - Approving the `WorkItem` activates a 90-day read grant with `expiresAt` auto-revocation (`DGC-026`).
3. **Journey 3 — Quality Incident Kanban Triage & Downstream BI Trust Banner:**
   - A `UNIQUENESS` `DatDataQualityRule` on `MARTS.fact_subscriptions` drops from `100.00%` to `96.40%` (below `99.90%` `passThresholdPct`).
   - `data-governance` opens a `CRITICAL` `DatQualityIncident`, moves `DatCatalogAsset.trustStatus` to `WARNING`, suspends `aiGroundingApproved`, creates a Steward Home `WorkItem`, and lights up an upstream warning badge on `#096` executive ARR dashboards (`DGC-015`).
   - On `quality-incidents` (`<rapider-kanban>` + table), the Steward drags the incident card from `OPEN` to `INVESTIGATING` and then `RESOLVED` after `#098` deduplicates the feed, synchronously updating both kanban and table views.
4. **Journey 4 — Breaking Change Blast-Radius Impact Check:**
   - Before renaming `account_tier` in `#099`, an engineer opens `lineage-impact`, selects `MARTS.dim_accounts.account_tier`, and inspects the blast radius (`DGC-014`): 2 `#098` SQL models, 4 `#096` certified `DatMetricDefinition`s, and 3 executive `DatDashboard`s, notifying all 3 named Stewards prior to change.
5. **Journey 5 — Business Glossary Stewardship & Grounded "Ask Catalog":**
   - A user opens `"Ask Catalog"` (`projectChannelMessage`) on `governance-posture` and asks: *"What is the official definition of Gross Churn and which table is certified for it?"*
   - The AI cites `DatBusinessGlossaryTerm` `TERM-CHURN-GROSS` (`APPROVED`) and `DatCatalogAsset` `MARTS.fact_mrr_movements` (`ENDORSED`, `qualityScorePct: 99.85%`), with clickable deep links.

---

## 6. Consolidated Feature Priorities & Work Packages (`P0`, `P1`, `P2`)

### `P0` Foundation Work Packages
- **`WP-P0-1` Unified Asset Catalog & Domain Stewardship (`DGC-001`, `DGC-002`, `DGC-003`):** Build `governance-posture`, `asset-catalog`, and `catalog-asset-detail` with popularity ranking, `HrDepartment`/`HrEmployee` ownership, and trust banners (`All Users` / `Data Steward`).
- **`WP-P0-2` Business Glossary & Metric Alignment (`DGC-007`, `DGC-008`):** Build `business-glossary`, `glossary-term-detail`, and `governance-editor-drawer` linked to `#096` metrics and `#099` columns (`Data Steward`).
- **`WP-P0-3` Column Lineage, Blast Radius & Quality Scorecards (`DGC-012`, `DGC-013`, `DGC-014`, `DGC-017`, `DGC-018`, `DGC-019`):** Build `lineage-impact`, `data-quality-rules`, and `quality-incidents` (`<rapider-kanban>` + table) with `Decimal128` trust scores and Home `WorkItem` escalation (`Data Engineer` / `Data Steward`).
- **`WP-P0-4` PII Classification Taxonomy & Active Policy Pushdown (`DGC-023`, `DGC-024`):** Build `classifications-privacy` and `access-policies` pushing dynamic column masking and row filters to `#099`, `#096`, and `#097` (`Privacy Officer` / `Security Admin`).

### `P1` Scale & Enterprise Governance Work Packages
- **`WP-P1-1` Data Product Access Shopping, Active Sync & Expiry Revocation (`DGC-004`, `DGC-005`, `DGC-009`, `DGC-010`, `DGC-026`):** Build `stewardship-requests` with Home `WorkItem` routing, term-driven policy inheritance, bidirectional `#099/#096` tooltip sync, and automatic `expiresAt` grant revocation (`Data Steward`).
- **`WP-P1-2` Upstream BI Incident Banners, Cross-Suite Audits, RoPA & Posture (`DGC-015`, `DGC-020`, `DGC-021`, `DGC-025`, `DGC-027`):** Live `#096` incident banners, cross-suite orphan audits, GDPR Article 30 RoPA register, and `projectChannelMessage` incident war rooms (`Privacy Officer` / `Data Steward`).

### `P2` Adjacent & Grounded AI Work Packages
- **`WP-P2-1` AI Context Readiness Gate & Regulatory Provenance (`DGC-006`, `DGC-016`):** `AI_GROUNDING_APPROVED` certification gating conversational AI across `DAT` and EU AI Act / SOX provenance exports (`AI Governance Lead`).
- **`WP-P2-2` AI Auto-Documentation, Quality Recommender & "Ask Catalog" (`DGC-011`, `DGC-022`, `DGC-028`):** Draft column descriptions, candidate DQ rule recommendations, and grounded catalog discovery over `projectChannelMessage` (`Data Steward` / `All Users`).

---

## 7. Roles, Permissions & Field-Level Governance

| Role | Permitted Actions | Restricted / Field-Level Boundaries |
| :--- | :--- | :--- |
| **`Catalog Consumer`** | Search `asset-catalog` and `business-glossary`, inspect permitted `lineage-impact` graphs, submit `DatStewardshipRequest` access requests, use `"Ask Catalog"`. | Metadata for `CONFIDENTIAL` executive schemas hidden unless discoverable; never sees raw data samples of masked columns. |
| **`Domain Data Steward`** | Edit `DatCatalogAsset` documentation, approve `DatBusinessGlossaryTerm` revisions and `DATA_ACCESS_GRANT` `WorkItem`s in assigned `HrDepartment`, triage `DatQualityIncident`s. | Cannot weaken workspace-wide `DatDataAccessPolicy` masking strategies or delete `RESTRICTED_PII` tags. |
| **`Data Quality Engineer`** | Author/schedule `DatDataQualityRule`s, run cross-suite integrity checks, manage `quality-incidents` `<rapider-kanban>` transitions. | Cannot grant user access to `RESTRICTED_PII` tables or modify RoPA legal basis fields. |
| **`Privacy & Compliance Officer`** | Manage `DatClassificationTag` detectors, author `DatDataAccessPolicy` masking/row rules, maintain GDPR Article 30 RoPA metadata, certify `AI_GROUNDING_APPROVED`. | Every `CLASSIFICATION_OVERRIDE` downgrading a PII tag requires mandatory justification and writes an immutable audit log. |
| **`Governance Admin`** | Configure automated catalog harvesters, domain operating hierarchies, and global retention/revocation schedules. | Cannot purge immutable stewardship approval or access grant audit trails. |

---

## 8. Technical APIs, Guarded Commands, Events & `requiredWorkflows`

### Guarded Commands
1. `dat.governance.harvestCatalogMetadata({ targetAppKeys, idempotencyKey, correlationId })` — Incrementally indexes schemas, metrics, pipelines, and popularity counters into `DatCatalogAsset`.
2. `dat.governance.publishAccessPolicy({ policyId, expectedVersion, idempotencyKey, correlationId })` — Validates and activates `DatDataAccessPolicy`, emitting immediate cache-invalidation and policy-pushdown events.
3. `dat.governance.evaluateQualityRules({ assetId, ruleIds, idempotencyKey, correlationId })` — Computes `Decimal128` pass rates, updates `DatCatalogAsset.qualityScorePct`, and opens/auto-resolves `DatQualityIncident`s.
4. `dat.governance.decideStewardshipRequest({ requestId, decision: 'APPROVE' | 'REJECT' | 'REVOKE', reviewNotes, expectedVersion, idempotencyKey, correlationId })` — Executes Steward approval, provisions time-bound grant or glossary promotion, and closes the Home `WorkItem`.
5. `dat.governance.certifyAiGrounding({ assetId, approved, expectedVersion, idempotencyKey, correlationId })` — Enforces precondition (`trustStatus === 'ENDORSED'` and zero open `CRITICAL` incidents) before enabling `aiGroundingApproved`.

### Domain Events Published & Consumed (Kafka)
- **Published:** `dat.governance.classification.updated.v1`, `dat.governance.access_policy.updated.v1`, `dat.governance.quality_incident.created.v1`, `dat.governance.quality_incident.resolved.v1`, `dat.governance.access_grant.provisioned.v1`, `dat.governance.access_grant.expired.v1`.
- **Consumed:** `dat.etl.lineage.emitted.v1` (from `#098`), `dat.warehouse.schema.altered.v1` (from `#099`), `dat.bi.semantic_model.certified.v1` (from `#096`).

### `requiredWorkflows`
- `governanceMetadataHarvestAndPiiScanWorkflow` — Scheduled & event-driven metadata indexing, regex/heuristic PII tagging, and column-lineage propagation.
- `governanceQualityObservabilityWorkflow` — Executes `DatDataQualityRule` schedules, recalculates trust scores, and escalates `CRITICAL` incidents to Home `WorkItem`s.
- `governanceStewardshipApprovalWorkflow` — Routes access requests and glossary redlines through Domain Steward Home `WorkItem`s.
- `governanceAccessGrantExpiryWorkflow` — Hourly sweep revoking expired `DatStewardshipRequest` grants (`expiresAt <= now`).

### Grounded Rapider AI Governance Rules
- Bulk AI column descriptions (`DGC-011`) and quality rule suggestions (`DGC-022`) are strictly persisted as `DRAFT` proposals requiring human Steward acceptance; `"Ask Catalog"` (`DGC-028`) never exposes sample row values and strictly respects catalog asset visibility ACLs.

---

## 9. Security, Privacy, Compliance & Non-Functional Requirements

- **Regulatory Compliance (GDPR Art. 30, CCPA, HIPAA, SOX, EU AI Act):** Provides exportable RoPA inventories, automated PII/PHI/PCI tag propagation across lineage hops, verifiable time-bound access grants, and explicit AI dataset provenance records.
- **Immutable Audit Ledger:** Every tag downgrade, masking policy edit, glossary approval, and data access grant/revocation is written to an append-only 7-year compliance audit log.
- **Data Precision & Host Tenancy:** `Decimal128` used for all `qualityScorePct` and `passThresholdPct` calculations; zero `projectId` fields in any model.
- **Accessibility & Responsive UX:** `<rapider-kanban>` on `quality-incidents` pairs with an accessible keyboard-navigable table view; WCAG 2.2 AA tabular fallback provided for `lineage-impact` graphs; `#ffffff !important` white text enforced on primary/danger buttons across `390px`, `768px`, and `1440px`.

---

## 10. Deterministic Acceptance Criteria (14 Testable Criteria)

1. **AC-01 (Sidebar Minimum-3 Rule):** Visible sidebar sections (`Catalog & Glossary`: 3 items, `Lineage & Quality`: 3 items, `Privacy & Access`: 3 items) each contain `>= 3` `displayOnMenu: true` pages; `catalog-asset-detail`, `glossary-term-detail`, and `governance-editor-drawer` set `displayOnMenu: false`.
2. **AC-02 (Rapider Kanban & Multi-View Sync):** `quality-incidents` uses `<rapider-kanban>` (never a custom plain-div mock board) synchronized with its table view; editing or dragging a `DatQualityIncident` updates in-memory state and re-renders both views optimistically without reload.
3. **AC-03 (SWR Clean Queries & Defensive Filtering):** All 9 sidebar routes fetch data via `findSWR`/`countSWR` without client `isDeleted` where-clauses and filter `item.isDeleted !== true` in memory.
4. **AC-04 (Table Actions & Click-Through Navigation):** Zero `"View"` buttons exist in `Actions` columns; clicking an asset name on `asset-catalog` navigates to `#/catalog-asset-detail?id=...` and clicking a term on `business-glossary` navigates to `#/glossary-term-detail?id=...` without `<base href>` 404 traps; `Edit` uses icon+text and `Delete` uses an icon-only button with `#rapiderConfirmOkBtn` modal confirmation.
5. **AC-05 (Active Filter Tags & Clear All):** Entering a search term or toggling `ENDORSED / WARNING / DEPRECATED` pills on `asset-catalog` or `quality-incidents` displays `#activeFilterTagsBar` with HTML-escaped dismissible chips and `[Clear all]`.
6. **AC-06 (Drawer Lifecycle & `finally` Reset):** Saving or cancelling in `governance-editor-drawer` restores button state inside `finally`, clears SWR caches, updates parent lists/kanban optimistically, and closes the drawer via `closePageDrawer()`.
7. **AC-07 (Lineage PII Tag Propagation):** Adding a `DatLineageEdge` (`DIRECT_COPY` or `EXPRESSION`) from a column tagged `RESTRICTED_PII` (`autoPropagateLineage: true`) automatically applies `RESTRICTED_PII` to the downstream target column, whereas `HASHED_ANONYMIZED` preserves lineage provenance without propagating raw PII status.
8. **AC-08 (Critical Quality Incident Circuit Breaker):** Opening a `CRITICAL` `DatQualityIncident` on an `ENDORSED` asset automatically transitions `trustStatus` to `WARNING`, sets `aiGroundingApproved = false`, creates a Steward Home `WorkItem`, and emits `dat.governance.quality_incident.created.v1`.
9. **AC-09 (AI Grounding Precondition Guard):** Calling `dat.governance.certifyAiGrounding({ approved: true })` on an asset with `trustStatus !== 'ENDORSED'` or an open `CRITICAL` incident deterministically fails validation (`422`).
10. **AC-10 (Policy Pushdown Cache Invalidation):** Updating a `DatDataAccessPolicy` emits `dat.governance.access_policy.updated.v1` so `#099` and `#096` immediately invalidate affected result caches.
11. **AC-11 (Time-Bound Grant Auto-Expiry):** Executing `governanceAccessGrantExpiryWorkflow` transitions any `APPROVED` `DatStewardshipRequest` with `expiresAt <= now` to `EXPIRED` and emits `dat.governance.access_grant.expired.v1`.
12. **AC-12 (`Decimal128` Score Precision):** `qualityScorePct` and `passThresholdPct` computations preserve exact `Decimal128` precision across rule aggregations.
13. **AC-13 (Back Navigation Filter Preservation):** Navigating from `asset-catalog` (filtered by `Trust Status: "ENDORSED"`) to `catalog-asset-detail` and clicking `#btnGoBack` restores `asset-catalog` with `Trust Status: "ENDORSED"` intact.
14. **AC-14 (Theme & Contrast Compliance):** All 12 routes pass light/dark `validate_theme` checks with `#ffffff !important` white text on primary/danger buttons and zero `window.alert`/`confirm`/`prompt` calls.
