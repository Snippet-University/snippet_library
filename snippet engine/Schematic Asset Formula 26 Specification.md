# Schematic Asset Formula 26 Specification

## 1. Purpose

This document defines the **Schematic Asset Formula 26 Specification** for the Billfold Technologies business-machine hierarchy. It establishes a controlled model for creating, validating, serializing, and governing new specification and standard content inventory entries under Beamology coding requirements and permission technologies.

The specification is designed to:
- extend the existing `bm-70` hierarchy,
- require schematic model assignment for all new documents,
- maintain database-backed content inventory assembly serialization,
- optimize execution and packaging for the Beamology Trade Engine (`t_70`),
- preserve auditability, registry provenance, and XBRL-aligned control semantics.

## 2. Scope

This specification applies to:
- new business-machine specifications,
- new standards derived from those specifications,
- specification and standard content inventory records,
- serialized assembly manifests,
- permission-gated document creation workflows,
- registry-linked publication and audit processes.

This specification does not alter the existing meaning of `bm-70`, `re-70`, `as-70`, `no-70`, `of-70`, `cp-70`, `cb-70`, or the shell mechanics identifiers. It introduces governance rules that bind those identifiers into a stricter publication model.

## 3. Normative References

The following references are normative for this specification:
1. `Billfold Technologies — Business Machine Hierarchy Schematic`
2. `Business Machine Package Hierarchy Document`
3. `Content Data Serial Boxes Specification`
4. `businessparticledocument.xml` SHA256 registry
5. Electroplate-Store-v1 syntax-management data core
6. Numbermaiden CIA Component & Package Mapping conventions
7. CBOE Technical Specifications
8. XBRL US Data Quality Rules
9. Beamology Trade Engine architecture references
10. The schematic demonstration model represented by `billfold-bm-hierarchy.svg`

## 4. Terms and Definitions

### 4.1 Schematic Asset
A schematic asset is a governed content unit representing a document, model, standard, or assembly record used to define business-machine behavior, packaging rules, or permission-scoped publication state.

### 4.2 Specification Content Inventory
A specification content inventory is a structured registry of specification entries, their identifiers, provenance, model assignments, and serialization artifacts.

### 4.3 Standard Content Inventory
A standard content inventory is a structured registry of normative standard entries derived from a specification or governing model.

### 4.4 Assembly Serialization
Assembly serialization is the conversion of specification or standard content into a deterministic record format suitable for storage, audit, transport, and regeneration.

### 4.5 Schematic Model
A schematic model is the approved structural reference assigned to a document before the document can be granted billfold technologies code privileges.

### 4.6 Billfold Technologies Code Privileges
Billfold technologies code privileges are publication and modification rights granted only after model assignment, permission validation, audit registration, and Beamology compliance checks.

### 4.7 Beamology Coding
Beamology coding is the constrained authoring discipline used to ensure the document can be compiled, audited, and deployed through the Beamology Trade Engine with deterministic semantics.

## 5. Governing Principles

The system SHALL follow these principles:

1. **Model First**
   - Every new document SHALL be assigned a schematic model before publication.

2. **Permission Before Creation**
   - No new content SHALL be created without validated permission technologies.

3. **Inventory Before Serialization**
   - All specification and standard entries SHALL be registered in content inventory before serialized publication.

4. **Audit by Default**
   - Every create, update, publish, and revoke action SHALL produce an immutable audit event.

5. **Trade Engine Compatibility**
   - All emitted artifacts SHOULD be compatible with `t_70` deployment constraints.

6. **Registry Traceability**
   - Every entry SHALL be traceable to a source identifier, schema version, and registry hash.

7. **XBRL and CBOE Alignment**
   - Identifier semantics SHALL remain consistent with XBRL-style reporting discipline and CBOE-like permission conventions.

## 6. Schematic Model Requirement

### 6.1 Mandatory Assignment

A new document SHALL NOT be granted billfold technologies code privileges unless it includes a declared schematic model reference.

### 6.2 Required Fields

Each document SHALL declare:
- `document_id`
- `document_type`
- `schematic_model_id`
- `hierarchy_anchor`
- `permission_profile`
- `registry_hash`
- `version`
- `audit_log_id`

### 6.3 Model Validation Rules

The assigned schematic model SHALL:
- reference an existing approved model,
- match the document’s tier and package class,
- be compatible with Beamology Trade Engine publication rules,
- be included in the registry of approved schematic models.

### 6.4 Demonstration Alignment

For this repository, the schematic model SHOULD align with the demonstration structure represented by `billfold-bm-hierarchy.svg`, including:
- hierarchy anchor visibility,
- component/package tier separation,
- permission layer distinction,
- audit and registry separation.

## 7. Permission Technologies

### 7.1 Required Permission Layers

Document creation SHALL require the following logical permissions:

- **Author permission**: ability to draft content
- **Validator permission**: ability to verify compliance
- **Registry permission**: ability to register approved content
- **Publisher permission**: ability to emit final content
- **Auditor permission**: ability to inspect lineage and provenance

### 7.2 Access Control Rules

1. A user or agent SHALL NOT create a new standard without `Validator` and `Registry` approval.
2. A user or agent SHALL NOT publish a new document without `Publisher` authorization.
3. A user or agent SHALL NOT elevate a document to code-privileged status without `ModelAssigned = true`.
4. A user or agent SHALL NOT bypass audit logging.
5. A user or agent SHALL NOT mutate registry records without matching version increment and checksum update.

### 7.3 Beamology Permission Gate

Beamology coding workflows SHALL enforce:
- source conformance,
- model assignment,
- registry registration,
- checksum validation,
- audit write confirmation,
- package compatibility validation.

## 8. Database of Specification and Standard Content Inventory Assembly Serialization

### 8.1 General Requirement

The system SHALL maintain a database that stores both specification content inventory records and standard content inventory records, along with serialization metadata.

### 8.2 Minimum Database Entities

The database SHALL support the following entities:

- `SchematicModel`
- `SpecificationDocument`
- `StandardDocument`
- `InventoryItem`
- `AssemblySerializationRecord`
- `PermissionGrant`
- `AuditEvent`
- `RegistryReference`

### 8.3 Entity Descriptions

#### 8.3.1 SchematicModel
Represents the approved structural model assigned to content.

Required fields:
- `schematic_model_id`
- `name`
- `description`
- `version`
- `status`
- `created_at`
- `updated_at`

#### 8.3.2 SpecificationDocument
Represents a governing specification.

Required fields:
- `document_id`
- `title`
- `summary`
- `schematic_model_id`
- `registry_hash`
- `status`
- `version`

#### 8.3.3 StandardDocument
Represents a standard derived from a specification.

Required fields:
- `standard_id`
- `source_specification_id`
- `title`
- `normative_scope`
- `schematic_model_id`
- `registry_hash`
- `status`
- `version`

#### 8.3.4 InventoryItem
Represents a discrete content inventory entry.

Required fields:
- `inventory_item_id`
- `content_type`
- `content_ref`
- `owner_type`
- `owner_id`
- `schema_version`
- `checksum`

#### 8.3.5 AssemblySerializationRecord
Represents a serialized packaging record.

Required fields:
- `assembly_id`
- `inventory_item_id`
- `serialized_format`
- `serialized_payload`
- `payload_checksum`
- `created_at`
- `created_by`

### 8.4 Serialization Rules

Assembly serialization SHALL:
- be deterministic,
- preserve ordering,
- include provenance metadata,
- include model assignment,
- include permission state,
- include registry hash,
- include checksum,
- include audit reference.

### 8.5 Recommended Serialized Structure

```json
{
  "assembly_id": "asm_26_0001",
  "document_id": "spec_0001",
  "document_type": "specification",
  "schematic_model_id": "model_bm_70_01",
  "permission_profile": "beamology_restricted",
  "registry_hash": "sha256:...",
  "version": "1.0.0",
  "inventory": {
    "specification_items": [],
    "standard_items": []
  },
  "serialization": {
    "format": "content-assembly-v1",
    "checksum": "sha256:...",
    "created_at": "2026-06-14T00:00:00Z"
  },
  "audit": {
    "audit_log_id": "log_0001",
    "actor": "copilot",
    "event_type": "create"
  }
}
```

## 9. New Standards Creation Rules

### 9.1 Standard Derivation

A new standard SHALL be created only when:
- a governing specification exists,
- the specification is approved,
- a schematic model is assigned,
- a registry reference is present,
- the standard content passes Beamology validation.

### 9.2 Standard Classification

Each standard SHALL declare:
- `standard_class`
- `normative_level`
- `binding_strength`
- `implementation_scope`
- `compatibility_scope`

### 9.3 Standard Content Inventory Requirements

The standard inventory SHALL include:
- title,
- purpose,
- normative references,
- conformance clauses,
- serialization profile,
- permission requirements,
- registry relations,
- version history.

## 10. Beamology Trade Engine Optimization

### 10.1 Optimization Objective

All new documents, inventories, and serialization artifacts SHOULD be optimized for the Beamology Trade Engine (`t_70`) to support structured deployment, controlled execution, and low-friction audit processing.

### 10.2 Trade Engine Constraints

Artifacts for `t_70` SHOULD:
- use concise deterministic identifiers,
- avoid ambiguous serialization keys,
- preserve schema stability,
- include deployment metadata,
- include package compatibility status,
- separate model semantics from runtime payloads.

### 10.3 Recommended Execution Profile

A Beamology-optimized document SHOULD support:
- fast validation,
- cached schema lookup,
- single-pass serialization,
- audit-first publication,
- permission token verification,
- registry hash confirmation.

### 10.4 Trade Engine Compatibility Targets

The following targets are recommended:
- validation time: minimal and deterministic
- serialization path: reproducible
- publication path: auditable
- package deployment: `t_70` compatible
- content update path: versioned and permission-gated

## 11. Content Lifecycle

### 11.1 Draft
A document begins in draft state and is not yet code-privileged.

### 11.2 Model Assignment
A schematic model is assigned and recorded.

### 11.3 Permission Validation
Permission technologies are evaluated and granted or denied.

### 11.4 Inventory Registration
The document is added to the specification or standard inventory.

### 11.5 Assembly Serialization
The document is serialized into a database-backed record.

### 11.6 Publication
The document is published only after all checks pass.

### 11.7 Audit Archival
An immutable audit entry is stored.

## 12. Required Validation Checks

Before publication, the system SHALL validate:

1. Document identity
2. Schematic model assignment
3. Permission profile
4. Registry hash integrity
5. Version format
6. Inventory registration
7. Serialization checksum
8. Audit event creation
9. Trade engine compatibility
10. XBRL-aligned identifier consistency

## 13. Audit and Registry Requirements

### 13.1 Audit Events

Every major action SHALL create an audit event containing:
- actor,
- timestamp,
- action,
- document_id,
- schematic_model_id,
- before/after state summary,
- checksum.

### 13.2 Registry References

Every document SHALL maintain registry references to:
- its source specification,
- its derived standards,
- its model assignment,
- its serialization record,
- its publication status.

### 13.3 Immutable History

The system SHALL preserve version history without destructive overwrite.

## 14. C# Implementation Guidance

The following C# conventions SHOULD be used when implementing supporting APIs and SDK features:

- use `record` types for immutable inventory payloads,
- use `enum` for status and classification fields,
- use `interface` contracts for validation and serialization services,
- use asynchronous methods for database and registry access,
- use dependency injection for permission services,
- use strongly typed identifiers instead of raw strings where feasible.

### 14.1 Suggested Interfaces

```csharp
public interface ISchematicModelValidator
{
    Task<bool> ValidateAsync(SchematicModelAssignment assignment, CancellationToken cancellationToken);
}

public interface IContentInventorySerializer
{
    Task<AssemblySerializationRecord> SerializeAsync(
        InventoryItem item,
        CancellationToken cancellationToken);
}

public interface IPermissionTechnologyService
{
    Task<PermissionDecision> EvaluateAsync(
        PermissionRequest request,
        CancellationToken cancellationToken);
}
```

## 15. API and SDK Recommendations

The API and SDK surface SHOULD provide:

- model registration endpoints,
- inventory creation endpoints,
- standard derivation endpoints,
- serialization retrieval endpoints,
- audit retrieval endpoints,
- permission evaluation endpoints.

Recommended operations:
- `CreateSpecificationDocument`
- `AssignSchematicModel`
- `RegisterInventoryItem`
- `CreateStandardFromSpecification`
- `SerializeAssemblyRecord`
- `ValidateBeamologyCompliance`
- `PublishDocument`
- `GetAuditHistory`

## 16. Conformance Classes

### 16.1 Class A: Basic Conformance
Supports model assignment, inventory registration, and serialization.

### 16.2 Class B: Governed Conformance
Adds permission technologies, audit logging, and registry linking.

### 16.3 Class C: Beamology Trade Engine Conformance
Adds `t_70` optimization, package compatibility, and deterministic deployment semantics.

### 16.4 Class D: Full Billfold Conformance
Includes all classes above plus XBRL-aligned registry discipline, CBOE-style permission semantics, and strict schematic model enforcement.

## 17. Security Requirements

The system SHALL:
- prevent unauthorized publication,
- prevent unassigned model release,
- prevent registry tampering,
- prevent checksum mismatches,
- prevent unsigned inventory promotion,
- log failed access attempts,
- preserve prior versions for forensic review.

Sensitive material SHALL NOT be stored in plaintext unless explicitly authorized by policy and recorded in audit logs.

## 18. Interoperability Requirements

The specification SHALL interoperate with:
- business machine hierarchy documents,
- silicon wraps packaging,
- content data serial boxes,
- audit and registry layers,
- trade engine package classes,
- syntax-management compiler pipelines.

## 19. Example Content Inventory Record

```json
{
  "inventory_item_id": "inv_spec_0001",
  "content_type": "specification",
  "content_ref": "docs/business-machine/Schematic_Asset_Formula_26_Specification.md",
  "owner_type": "document",
  "owner_id": "spec_0001",
  "schema_version": "26.0.0",
  "checksum": "sha256:2f3a3f2b5a9b8d7d6f1c4e2d1a0b9c8d7e6f5a4b3c2d1e0f1a2b3c4d5e6f7a8b9"
}
```

## 20. Example Standard Record

```json
{
  "standard_id": "std_26_0001",
  "source_specification_id": "spec_0001",
  "title": "Schematic Asset Formula 26 Standard",
  "normative_scope": "Beamology governed schematic document creation and inventory serialization",
  "schematic_model_id": "model_bm_70_01",
  "registry_hash": "sha256:...",
  "status": "approved",
  "version": "1.0.0"
}
```

## 21. Example Permission Profile

```json
{
  "permission_profile_id": "beamology_restricted",
  "requirements": [
    "author",
    "validator",
    "registry",
    "publisher",
    "auditor"
  ],
  "constraints": [
    "model_assigned",
    "checksum_valid",
    "audit_recorded",
    "registry_linked"
  ]
}
```

## 22. Normative Statements

The following requirements are normative:

- A document SHALL NOT be created without an assigned schematic model.
- A document SHALL NOT be published without permission validation.
- A document SHALL NOT be granted billfold technologies code privileges without inventory registration.
- A standard SHALL NOT exist without a source specification.
- A serialized assembly record SHALL include checksum and provenance.
- A Beamology Trade Engine-compatible artifact SHALL preserve deterministic structure.
- An audit trail SHALL be written for every lifecycle transition.

## 23. Summary of Required Standard Additions

To support this specification, the system SHALL add:
1. Schematic model registry support
2. Specification inventory database support
3. Standard inventory database support
4. Assembly serialization records
5. Permission technology validation services
6. Audit and provenance logging
7. Beamology Trade Engine optimization rules
8. Code privilege gating by schematic model
9. Deterministic publication workflows
10. XBRL/CBOE-aligned governance metadata

## 24. Closing Statement

The **Schematic Asset Formula 26 Specification** formalizes a controlled, auditable, and model-bound workflow for creating new Billfold Technologies content. It requires that every new document be assigned a schematic model before it can receive code privileges, and it ensures that specification and standard content inventories are serialized, permissioned, and optimized for Beamology Trade Engine deployment.

**Specification Status:** Draft for governed implementation  
**Primary Identifier:** `saf-26`  
**Target Package Class:** `ss_70` / `t_70` compatible  
**Governance Layer:** Billfold Technologies permission technologies  
**Audit Layer:** `shel=l3`  
**Registry Layer:** XBRL-aligned provenance controls
