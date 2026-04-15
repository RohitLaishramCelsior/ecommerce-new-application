# Modernization Brief - Legacy Code Modernization

## Header
- Objective: Modernize legacy code by building from the Discover baseline.
- Domain: software
- Repo: synthetix @ feature-synthetix-ui-v2-bunty (1a897ad4a128f8f34bed5254f37915350c5084d0)
- SIL Versions: SCM 1.0 / CP 1.0 / HA 1.0
- Generated At: 2026-04-15T07:54:22.442515+00:00

## Decision Brief

| Category | Summary |
|---|---|
| Modernization readiness | 75/100 |
| Risk tier | medium |
| Inventory | 1 project(s), 2 forms/usercontrols, 3 dependencies |
| Lines of code scanned | 0 total LOC (0 form LOC, 0 module LOC, 0 class LOC) across 0 files |
| Data touchpoints | Users, Transactions |
| Headline | Phased UI Migration recommended. |

### Recommended strategy
- Phased UI Migration: Allows gradual transition while maintaining functionality.
- PH0 Baseline and equivalence harness: Capture golden flows and baseline outputs.
- PH1 Incremental migration and dependency replacement: Migrate forms/modules with dependency risk controls.
- PH2 Hardening and release evidence: Finalize quality gates and publish evidence pack.

### Decisions Required (Blocking)
- DEC-UI-001: Target UI framework selection for migrated forms
  - Recommendation: WinForms for lowest event-model delta from VB6 unless UX redesign is in scope.
- DEC-OCX-001: ActiveX/OCX replacement strategy by dependency
  - Recommendation: Replace common controls and isolate only high-risk dependencies behind adapters.
- DEC-DB-001: Database contract strategy during migration
  - Recommendation: Preserve contracts initially and modernize behind a compatibility layer.
- DEC-IAM-001: Confirm identity/access model (role model, multi-user assumptions, and credential handling).
  - Recommendation: Define target role model and credential policy before implementation.
- Q-001: Are there existing operational constraints or integration dependencies not listed?
  - Recommendation: Resolve with product/business owner before implementation commitment.
- Q-002: What are target latency, throughput, and availability SLOs?
  - Recommendation: Resolve with product/business owner before implementation commitment.

### Decisions Required (Non-blocking)
- DEC-OBS-001: Logging and observability stack for migrated runtime

## Delivery Spec

### Backlog
| ID | Pri | Type | Outcome | Acceptance |
|---|---|---|---|---|
| FR-001 | P0 | functional | Legacy Code Analysis | A comprehensive report of legacy code components is generated. / Key areas for modernization are identified and documented. |
| FR-002 | P0 | functional | Refactor Legacy Code | Code refactoring adheres to modern coding standards. / All refactored code passes existing unit tests. |
| FR-003 | P0 | functional | Backward Compatibility Testing | All legacy interfaces are supported in the modernized code. / Existing integrations function without modification. |
| FR-004 | P1 | functional | Implement Error Handling | All critical errors are logged with sufficient detail. / Error handling does not degrade application performance. |
| FR-005 | P1 | functional | Enhance Observability | Application metrics are collected and stored for analysis. / Real-time monitoring dashboards are available. |
| FR-006 | P0 | functional | Security Hardening | All sensitive data is encrypted at rest and in transit. / Security vulnerabilities identified in legacy code are resolved. |
| FR-007 | P1 | functional | Performance Optimization | Application response times meet defined SLAs. / Resource utilization is optimized for cost efficiency. |
| FR-008 | P2 | functional | User Documentation Update | All user-facing changes are documented. / Documentation is reviewed and approved by stakeholders. |
| NFR-001 | P1 | non_functional | Performance | Load tests confirm response time under specified conditions. / Performance metrics are consistently monitored. |
| NFR-002 | P1 | non_functional | Security | Security scans show no critical vulnerabilities. / Penetration testing confirms application security. |
| NFR-005 | P1 | non_functional | Usability | User feedback indicates high satisfaction. / Usability tests confirm intuitive design. |
| RM-001 | P0 | risk_remediation | Define identity and access model for modernization scope | Remediation implemented and validated against affected legacy flow. / Evidence artifacts updated with before/after traceability. |

### Testing and Evidence
- Golden flows:
  - GF-001: Form1 primary flow | entry=Form1::Button_Click
- Quality gates:
  - gherkin_syntax: PASS | BDD syntax validation for Feature/Scenario/Given/When/Then.
  - requirements_completeness: PASS | Backlog grounded in discovered behavior (12 derived item(s), threshold 3).
  - compliance_constraints_applied: WARN | Verifies that regulatory/software controls are linked to requirements when applicable.
  - bdd_flow_grounding: PASS | BDD scenarios are grounded in extracted legacy flows.
  - handler_inventory_completeness: PASS | All analyzed forms meet handler coverage threshold.
  - report_model_reconciled: PASS | Reporting model and entrypoints reconciled.
  - variant_resolution: PASS | Single project variant detected; no variant scope decision required.
  - variant_schema_divergence: PASS | No cross-variant schema naming divergence detected.
  - key_safety_issues_identified: FAIL | No explicit SQL/credential safety signals detected in extracted artifacts. Detection is incomplete and blocks progression.
  - schema_key_verification: PASS | No delete-by-customer transaction key hazard detected.
  - identity_access_model: WARN | Role model or credential handling requires confirmation.
  - database_archaeology_ready: WARN | DB QA detected blocking or warning issues in schema reconstruction/mapping.
  - qa_structural_integrity: FAIL | QA structural checks: pass=12, warn=3, fail=1, blockers=1.
  - qa_semantic_plausibility: PASS | Semantic plausibility checks passed with no issues.
- QA summary:
  - Status: FAIL
  - Structural: pass=12, warn=3, fail=1, blockers=1
  - QA Gate qa_structural_integrity: FAIL | QA structural checks: pass=12, warn=3, fail=1, blockers=1.
  - QA Gate qa_semantic_plausibility: PASS | Semantic plausibility checks passed with no issues.
  - Structural checks: 16 total (1 blocking)
  - Rule consolidation notes are documented in Appendix Section E2 when duplicate rule templates are suppressed.

### Open Questions
- [HIGH] Q-001: Are there existing operational constraints or integration dependencies not listed? (owner: Client)
- [HIGH] Q-002: What are target latency, throughput, and availability SLOs? (owner: Client)

## QA Validation Summary
- Overall status: FAIL
- Structural summary: pass=12, warn=3, fail=1, blockers=1

## Evidence Appendix
- legacy_inventory_ref: artifact://legacy_inventory/1.0/art_legacy_inventory_e77c7ba1e7244cd2
- repo_landscape_ref: artifact://repo_landscape/1.0/art_repo_landscape_ec31ec03bba74724
- scope_lock_ref: artifact://scope_lock/1.0/art_scope_lock_3da08f4e3ccc4783
- variant_inventory_ref: artifact://variant_inventory/1.0/art_variant_inventory_249cfb1f730a44da
- event_map_ref: artifact://event_map/1.0/art_event_map_f9089b48a69547a3
- sql_catalog_ref: artifact://sql_catalog/1.0/art_sql_catalog_767ec9a2944446d4
- sql_map_ref: artifact://sql_map/1.0/art_sql_map_c1d76b97a33441fa
- data_access_map_ref: artifact://data_access_map/1.0/art_data_access_map_9d775bc084b74026
- recordset_ops_ref: artifact://recordset_ops/1.0/art_recordset_ops_0ab732d28ec54812
- procedure_summary_ref: artifact://procedure_summary/1.0/art_procedure_summary_9b8ab952930e4121
- form_dossier_ref: artifact://form_dossier/1.0/art_form_dossier_dd551a59465445a5
- dependency_list_ref: artifact://dependency_inventory/1.0/art_dependency_inventory_01611a4651df47c7
- dependency_inventory_ref: artifact://dependency_inventory/1.0/art_dependency_inventory_01611a4651df47c7
- business_rules_ref: artifact://business_rule_catalog/1.0/art_business_rule_catalog_a659391cc55a456f
- detector_findings_ref: artifact://detector_findings/1.0/art_detector_findings_f7066c466c2b4172
- risk_register_ref: artifact://risk_register/1.0/art_risk_register_42afdbc2bb074ec7
- orphan_analysis_ref: artifact://orphan_analysis/1.0/art_orphan_analysis_4a831efc07b74916
- delivery_constitution_ref: artifact://delivery_constitution/1.0/art_delivery_constitution_2d44dc7a0b8e4de0
- source_db_profile_ref: artifact://source_db_profile/1.0/art_source_db_profile_975b8ebf97224713
- source_schema_model_ref: artifact://source_schema_model/1.0/art_source_schema_model_0c876cf9bdc049e1
- source_query_catalog_ref: artifact://source_query_catalog/1.0/art_source_query_catalog_3603647954fa442a
- source_relationship_candidates_ref: artifact://source_relationship_candidates/1.0/art_source_relationship_candidates_e9ef68d73c3046a2
- source_data_dictionary_ref: artifact://source_data_dictionary/1.0/art_source_data_dictionary_1aaf88957baa437d
- source_data_dictionary_markdown_ref: artifact://source_data_dictionary_markdown/1.0/art_source_data_dictionary_markdown_8a6f7568220b416b
- source_erd_ref: artifact://source_erd/1.0/art_source_erd_1ed3a53c59254d64
- source_hotspot_report_ref: artifact://source_hotspot_report/1.0/art_source_hotspot_report_93185c46d5ef4879
- target_schema_model_ref: artifact://analyst/raw/target_schema_model/v1
- target_erd_ref: artifact://analyst/raw/target_erd/v1
- target_data_dictionary_ref: artifact://analyst/raw/target_data_dictionary/v1
- schema_mapping_matrix_ref: artifact://analyst/raw/schema_mapping_matrix/v1
- migration_plan_ref: artifact://analyst/raw/migration_plan/v1
- validation_harness_spec_ref: artifact://analyst/raw/validation_harness_spec/v1
- db_qa_report_ref: artifact://analyst/raw/db_qa_report/v1
- schema_approval_record_ref: artifact://analyst/raw/schema_approval_record/v1
- schema_drift_report_ref: artifact://analyst/raw/schema_drift_report/v1
- variant_diff_report_ref: artifact://variant_diff_report/1.0/art_variant_diff_report_dd39c32157ba463d
- reporting_model_ref: artifact://reporting_model/1.0/art_reporting_model_1060ee9bf3014aa3
- identity_access_model_ref: artifact://identity_access_model/1.0/art_identity_access_model_0a5d6dc86f3a4f80
- discover_review_checklist_ref: artifact://discover_review_checklist/1.0/art_discover_review_checklist_326a53a96d7d4987
- artifact_index_ref: artifact://artifact_index/1.0/art_artifact_index_c1fd983d184c46b7
- qa_report_ref: embedded://analyst_report_v2/qa_report_v1
- knowledge_snapshot_ref: runctx://runctx-7bd5d70fc4a4d524/kctx-693f39aa1367f03c
- run_delivery_constitution_ref: runctx://runctx-7bd5d70fc4a4d524/delivery_constitution/const-f9b11d46f104
- High-volume sections included in structured artifact (inventory, dependencies, event map, SQL catalog, business rules).

## Appendix Snapshot
- Legacy inventory: present
- Event map rows: 1
- SQL catalog rows: 2
- SQL map rows: 1
- Procedure summaries: 1
- Form dossiers: 1
- Dependency rows: 3
- Business rules: 1
- Risk register rows: 2
- Orphan analysis rows: 0
- Repo landscape variants: 1
- Variant inventory rows: 1
- Constitution principles: 3
- MDB inventory rows: 0
- Form LOC profile rows: 0
- Designer LOC rows: 0
- Connection string variants: 0
- Module global inventory rows: 0
- Dead form references: 0
- DataEnvironment report mappings: 0
- Static risk detector findings: 0
- Source data dictionary rows: 0
- Source LOC: 0 total (forms=0, modules=0, classes=0) across 0 file(s)

## Detailed Appendix

### A. Legacy Inventory
- Projects: 1
- Data touchpoints: Users, Transactions
- Source LOC: 0 total (forms=0, modules=0, classes=0) across 0 file(s)
| Project | Type | Startup | Members | Forms | Reports | Dependencies | Source LOC | Shared tables |
|---|---|---|---:|---:|---:|---:|---:|---|
| LegacyApp | Standard EXE | Main | 3 | 2 | 0 | 1 | 0 | Transactions, Users |

### B. Dependency Inventory
| Name | Kind | GUID / Reference | Risk | Recommended action | Forms mapped |
|---|---|---|---|---|---|
| MSComctlLib | com_typelib | n/a | medium | Assess replacement/interop strategy. | n/a |
| msado15.dll | dll | n/a | medium | Assess replacement/interop strategy. | n/a |
| MSComctlLib.ocx | ocx | n/a | medium | Assess replacement/interop strategy. | n/a |

### C. Event Map
| Entry | Container | Trigger | Calls | Side effects |
|---|---|---|---|---|
| Form1:Click | Form1 | Click | SubmitTransaction | Transactions |

### D. SQL Catalog
| SQL ID | Kind | Tables | Query |
|---|---|---|---|
| sql:1 | select | Users | SELECT * FROM Users |
| sql:2 | insert | Transactions | INSERT INTO Transactions |

### D1. Source DB Column Schema
- No source data dictionary rows available.

### E. Business Rules
| Rule ID | Form | Layer | Category | Business Meaning | Implementation Evidence | Risk links |
|---|---|---|---|---|---|---|
| BR-001 | format | Presentation | input_validation | User input must be validated for format and length. | Form1.frm | none |
| BR-002 | Form1 | Presentation | input_validation | User input must be validated for format and length. | Form1.frm; source_rule=BR-001 | none |
| BR-003 | Form1 | Presentation | input_validation | User input must be validated for format and length. | variant_backfill_for_eq_sync (source=BR-001); source_rule=BR-001 | none |

### E1. Rule Cross-Reference by Form
- form1: rule_ids=[BR-002, BR-003]; summary=Authentication and credential validation workflow Business outcome: User access is validated before workflow continuation.. / User input must be validated for format and length.
- format: rule_ids=[BR-001]; summary=User input must be validated for format and length.

### F. Detector Findings
| Detector | Severity | Count | Summary | Required actions |
|---|---|---:|---|---|
| VB6-ERR-001 | high | 3 | Legacy error handling patterns detected | Refactor error handling |

### G. Artifact Index
| Type | Ref |
|---|---|
| legacy_inventory | artifact://legacy_inventory/1.0/art_legacy_inventory_e77c7ba1e7244cd2 |
| repo_landscape | artifact://repo_landscape/1.0/art_repo_landscape_ec31ec03bba74724 |
| scope_lock | artifact://scope_lock/1.0/art_scope_lock_3da08f4e3ccc4783 |
| variant_inventory | artifact://variant_inventory/1.0/art_variant_inventory_249cfb1f730a44da |
| dependency_inventory | artifact://dependency_inventory/1.0/art_dependency_inventory_01611a4651df47c7 |
| event_map | artifact://event_map/1.0/art_event_map_f9089b48a69547a3 |
| sql_catalog | artifact://sql_catalog/1.0/art_sql_catalog_767ec9a2944446d4 |
| sql_map | artifact://sql_map/1.0/art_sql_map_c1d76b97a33441fa |
| data_access_map | artifact://data_access_map/1.0/art_data_access_map_9d775bc084b74026 |
| recordset_ops | artifact://recordset_ops/1.0/art_recordset_ops_0ab732d28ec54812 |
| procedure_summary | artifact://procedure_summary/1.0/art_procedure_summary_9b8ab952930e4121 |
| form_dossier | artifact://form_dossier/1.0/art_form_dossier_dd551a59465445a5 |
| business_rule_catalog | artifact://business_rule_catalog/1.0/art_business_rule_catalog_a659391cc55a456f |
| detector_findings | artifact://detector_findings/1.0/art_detector_findings_f7066c466c2b4172 |
| risk_register | artifact://risk_register/1.0/art_risk_register_42afdbc2bb074ec7 |
| orphan_analysis | artifact://orphan_analysis/1.0/art_orphan_analysis_4a831efc07b74916 |
| project_metrics | artifact://project_metrics/1.0/art_project_metrics_ffb4634ee470488a |
| static_forensics_layer | artifact://static_forensics_layer/1.0/art_static_forensics_layer_3740b2beef0c4e1d |
| type_metrics | artifact://type_metrics/1.0/art_type_metrics_1deaa1c1ff184a9c |
| type_dependency_matrix | artifact://type_dependency_matrix/1.0/art_type_dependency_matrix_d9ef922ae37b4c79 |
| runtime_dependency_matrix | artifact://runtime_dependency_matrix/1.0/art_runtime_dependency_matrix_b59f20ce79694d85 |
| dead_code_report | artifact://dead_code_report/1.0/art_dead_code_report_4722bc935f864f77 |
| third_party_usage | artifact://third_party_usage/1.0/art_third_party_usage_4eb77c8b3dd24781 |
| code_quality_rules | artifact://code_quality_rules/1.0/art_code_quality_rules_0cd7a002d2834dfc |
| quality_violation_report | artifact://quality_violation_report/1.0/art_quality_violation_report_dfa98db222a843a2 |
| trend_snapshot | artifact://trend_snapshot/1.0/art_trend_snapshot_3c3b13ae43274639 |
| trend_series | artifact://trend_series/1.0/art_trend_series_b8a385c573134b50 |
| mdb_inventory | artifact://mdb_inventory/1.0/art_mdb_inventory_10c817107bdf4b4b |
| form_loc_profile | artifact://form_loc_profile/1.0/art_form_loc_profile_de601b99b9b14919 |
| connection_string_variants | artifact://connection_string_variants/1.0/art_connection_string_variants_5ef80eec50c84b85 |
| module_global_inventory | artifact://module_global_inventory/1.0/art_module_global_inventory_081ae84022c543cc |
| dead_form_refs | artifact://dead_form_refs/1.0/art_dead_form_refs_5363503458bb4bb7 |
| dataenvironment_report_mapping | artifact://dataenvironment_report_mapping/1.0/art_dataenvironment_report_mapping_2d0212eb461a4076 |
| static_risk_detectors | artifact://static_risk_detectors/1.0/art_static_risk_detectors_7c5c8bc79c99456a |
| delivery_constitution | artifact://delivery_constitution/1.0/art_delivery_constitution_2d44dc7a0b8e4de0 |
| source_db_profile | artifact://source_db_profile/1.0/art_source_db_profile_975b8ebf97224713 |
| source_schema_model | artifact://source_schema_model/1.0/art_source_schema_model_0c876cf9bdc049e1 |
| source_query_catalog | artifact://source_query_catalog/1.0/art_source_query_catalog_3603647954fa442a |
| source_relationship_candidates | artifact://source_relationship_candidates/1.0/art_source_relationship_candidates_e9ef68d73c3046a2 |
| source_data_dictionary | artifact://source_data_dictionary/1.0/art_source_data_dictionary_1aaf88957baa437d |
| source_data_dictionary_markdown | artifact://source_data_dictionary_markdown/1.0/art_source_data_dictionary_markdown_8a6f7568220b416b |
| source_erd | artifact://source_erd/1.0/art_source_erd_1ed3a53c59254d64 |
| source_hotspot_report | artifact://source_hotspot_report/1.0/art_source_hotspot_report_93185c46d5ef4879 |
| variant_diff_report | artifact://variant_diff_report/1.0/art_variant_diff_report_dd39c32157ba463d |
| reporting_model | artifact://reporting_model/1.0/art_reporting_model_1060ee9bf3014aa3 |
| identity_access_model | artifact://identity_access_model/1.0/art_identity_access_model_0a5d6dc86f3a4f80 |
| discover_review_checklist | artifact://discover_review_checklist/1.0/art_discover_review_checklist_326a53a96d7d4987 |

### H. SQL Map
| Form | Procedure | Operation | Tables | Risks | activex_trigger | trace_complete |
|---|---|---|---|---|---|---|
| Form1 [Password Management] | Button_Click | insert | Transactions | none | Button1:Button1 | yes |

### I. Handler and Procedure Summaries
| Callable | Kind | Form | SQL IDs | Steps | Risks | Source line refs |
|---|---|---|---|---|---|---|
| Button_Click | event_handler | Form1 | sql:2 | Triggered from Button1 Click. / Invokes procedures: SubmitTransaction. | none | n/a |

### J. Delivery Constitution
- Preserve critical legacy behavior first; modernization must prove functional equivalence.
- Every modernization decision must map to explicit evidence (code, query, event, or rule).
- No breaking change to data contracts without approved migration path and rollback evidence.

### K. Form Dossiers
| Form | Display Name | Project | form_type | Status | Purpose | Inputs (data) | Outputs (effects) | ActiveX used | DB tables | Actions | Coverage | Confidence | Exclusion reason |
|---|---|---|---|---|---|---|---|---|---|---:|---:|---:|---|
| Form1 | Form1 [Password Management] | n/a | Login | mapped | Authentication and credential validation workflow. | n/a | Transaction ledger updated. | Button1, TextBox1 | Transactions | 1 | 1.00 | 0.85 | none |
| Form1 | Form1 [Password Management] | LegacyApp [LegacyApp.vbp] | Login | mapped | Authentication and credential validation workflow. | n/a | Transaction ledger updated. | Button1, MSComctlLib, TextBox1 | Transactions | 1 | 1.00 | 0.85 | none |
| Form2 | Form2 | LegacyApp [LegacyApp.vbp] | Child | excluded | n/a | n/a | n/a | MSComctlLib | n/a | 0 | 0.00 | 0.10 | missing_from_form_dossier |

#### K1. Excluded/Unresolved Forms
| Form | Reason | Source |
|---|---|---|
| LegacyApp::Form2 | missing_from_form_dossier | project.forms |

### L. Risk Register
| Risk ID | Severity | Description | Recommended action |
|---|---|---|---|
| RISK-001 | high | Legacy error handling patterns detected | Refactor error handling |
| RISK-002 | medium | SQL risk flags for sql:1: select_star | Parameterize query and align dialect/validation rules before migration. |

### M. Orphan Analysis
- No orphan analysis rows available.

### N. Repository Landscape and Variant Inventory
| Variant | Path | Startup | Forms | Members | Dependencies |
|---|---|---|---:|---:|---:|
| LegacyApp | LegacyApp.vbp | Main | 2 | 3 | 1 |

| Variant | Forms | Modules | Tables touched | Dependency summary |
|---|---:|---:|---:|---|
| LegacyApp | 2 | 1 | 2 | total=1, ocx=0, dll=0 |

### O. Project Dependency Map
- No project dependency rows available.

### O1. Form User Flow (Spec-Kit Style)
- No explicit form-to-form navigation links detected.

### P. Form Flow Traces
#### Form1 (n/a)
| Callable | Kind | Event | ActiveX | SQL IDs | Tables | Source line refs | Trace status |
|---|---|---|---|---|---|---|---|
| Button_Click | event_handler | Form1::Button_Click | Button1:Button1 | sql:2 | Transactions | n/a | OK |

### Q. Form Traceability Matrix
| Form | Project | Source LOC | has_event_map | has_sql_map | has_business_rules | has_risk_entry | completeness_score | missing_links |
|---|---|---:|---|---|---|---|---:|---|
| Form1 | n/a | 0 | yes | yes | yes | no | 80 | risk_register |

### R. Sprint Dependency Map
| Form | Suggested sprint | Depends on | Shared Components Required | Rationale |
|---|---|---|---|---|
| Form1 | Sprint 2 (Parity hardening) | none | none | Complete hardening, regression validation, and release evidence for production readiness. |

### S. MDB Inventory
- No MDB/ACCDB files detected in this run.

### T. Form LOC Profile
- Forms discovered: 1 | active: 1 | orphan: 0 | canonical active forms LOC total: 0 | designer LOC total: 0
| Form ID | Form | Base form | Project | Source file | LOC | In VBP | Active/Orphan | Confidence | Evidence |
|---|---|---|---|---|---:|---|---|---:|---|
| form_dossier:1 | Form1 | Form1 | n/a | n/a | 0 | yes | active | 0.90 | form_dossier:1 \| conf 0.90 |

### T1. Designer LOC Profile
- No designer LOC rows available.

### U. Connection String Variants
- No connection-string variants detected.

### V. Module Global Inventory
- No module global inventory rows available.

### V1. Module Inventory
- No module inventory rows available.

### W. Dead Form References
- No dead-form references detected.

### X. DataEnvironment Report Mapping
- No DataEnvironment/report mappings detected.

### Y. Static Risk Detectors
- No static detector findings were emitted.

### Y1. Raw UI Control Inventory
- Controls discovered from raw form dossiers. Selection/list controls are preserved even when list values are not statically recoverable.
| Project | Form | Control Name | Control Type | Role | Values / Notes |
|---|---|---|---|---|---|
| n/a | Form1 | TextBox1 | TextBox1 | display | n/a |
| n/a | Form1 | Button1 | Button1 | display | n/a |