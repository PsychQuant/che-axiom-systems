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

## Growth path

Seeded with statement placement (A1). Designed to accrete further exposition
axioms as they are articulated — candidates already in practice:

- constructive-over-existential presentation (give the explicit witness, not "there exists");
- avoidance of "obviously" / "clearly" (replace with a two-line proof or a named tactic);
- direction discipline for bounds (upper vs lower — never cite an upper bound to argue a lower one);
- definition-scope hygiene (state the parameter range, not just the family);
- equation numbering for referenced displays.

Follows **SCD2 (add-only)**: axioms accumulate; existing ones are annotated, not
rewritten. Validate structure and cross-domain consistency with `/axiom-validate`.
