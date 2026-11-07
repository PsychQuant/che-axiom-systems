# Cross-Domain Principles

These principles govern ALL axiomatization systems. Every domain must comply.

## Principles

### 1. Domain Independence
Each axiomatization system is self-contained with well-defined boundaries. Knowledge and proficiency in one domain are not necessarily related to or transferable to another domain. Mastery in one domain does not automatically confer competence in another, even when superficial similarities exist.

### 2. Cross-Domain Integration
Systems may reference each other through explicit interfaces when concepts overlap.

### 3. Consistency Requirement
No axiom in one domain may contradict axioms in another domain.

### 4. Ontological Clarity
Each domain must clearly define its primitive terms and entities.

### 5. Methodological Transparency
The methods of derivation and proof within each domain must be explicitly stated.

### 6. Meta-Language Consistency
The meta-language used to articulate a domain's axiomatization should be consistent with the domain's subject matter. Domains focusing on culturally-specific concepts should employ terminology and structural elements from that culture's linguistic and conceptual frameworks.

### 7. Subordination
A domain may declare at most one parent domain in its manifest (`parent`). The parent must itself be a top-level domain: subordination is one level deep. A parent domain states the scope it shares with its children and the convention by which they cite each other; it holds no axioms of its own.

Children of the same parent may cite each other's entries in `derives_from`, written `<domain>:<entry>` — the entry is a YAML id, or the full heading of a markdown domain. This is the explicit interface of principle 2. Derivation across domains that do not share a parent is not permitted; such domains may still refer to each other in prose.

Principle 1 still holds within a parent. A child is answerable for what it asserts, and citing a sibling's entry does not confer the sibling's competence on it.

## Revision Rules

### SCD2 (Add Only)
Axioms and principles are strictly cumulative and monotonically increasing. New axioms and principles may be added, but existing ones cannot be modified or removed. This ensures stability and backward compatibility across all axiomatization systems.

### Domain Expansion
While domains themselves are fixed, their scope may be expanded through the addition of new axioms and principles that extend rather than alter the conceptual foundation.

### Annotation Permissibility
Existing axioms and principles may be annotated with additional clarifications, formalizations, or cross-references, provided these annotations do not change the original meaning.
