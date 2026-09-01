# Mathematical Writing

Axiomatizes the craft of producing **formal mathematical prose for readers** —
where mathematical material is placed and how claims are set out (the theorem /
proposition / definition / remark architecture, and the rigor conventions of
exposition).

## Scope and boundaries

| Relation | Domain | Difference |
|----------|--------|------------|
| Sibling (consume ↔ produce) | `mathematical-learning` | Learning concerns *acquiring* mathematics (cognition, prerequisite structure); this domain concerns *setting it out*. Same primitives (theorem, proof, definition), opposite direction. |
| Distinct | `note-writing` | Notes are private, for the writer; this domain is formal exposition addressed to peer readers. |
| Cross-reference (§Cross-Domain Integration) | `logic-and-language` | The `Altitude` primitive (object-level vs meta-level) is the exposition-craft analog of the object-language / metalanguage distinction — related, not identical: here it decides *placement*, there it is a *formal* distinction. |

## Axioms

| ID | Name | One-liner |
|----|------|-----------|
| `A1_altitude_placement` | Statement placement by altitude | Object-level relations earn theorem status; meta-level framework properties belong in remarks; never state the same content in both. |
| `A2_repair_accretion` | Altitude drift under repair | Repair rounds accrete meta-level qualifications inside statements; re-check altitude after repair, and relocate rather than delete. |
| `A3_replacement_precondition` | Re-placement requires the citation set | A statement may not be relocated until what cites it is known; references address containers, not content, and the compiler checks neither. |

## Theorems

| ID | Derives from | One-liner |
|----|--------------|-----------|
| `T1_negative_space_is_meta` | `A1` | A claim that a hypothesis does *not* give a conclusion is meta-level — including its witness — so it belongs in a remark, not in the statement that assumes the hypothesis. |

## Growth path

Seeded with statement placement (A1); extended with the revision dynamics that
defeat it (A2: repair accretes meta-level material inside statements; A3:
relocation is admissible only once the citation set is known) and with the
negative-space corollary of A1 (T1). Designed to accrete further exposition
axioms as they are articulated — candidates already in practice:

- constructive-over-existential presentation (give the explicit witness, not "there exists");
- avoidance of "obviously" / "clearly" (replace with a two-line proof or a named tactic);
- direction discipline for bounds (upper vs lower — never cite an upper bound to argue a lower one);
- definition-scope hygiene (state the parameter range, not just the family);
- equation numbering for referenced displays.

Follows **SCD2 (add-only)**: axioms accumulate; existing ones are annotated, not
rewritten. Validate structure and cross-domain consistency with `/axiom-validate`.
