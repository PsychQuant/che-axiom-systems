# Academic Writing

Axiomatizes the craft of writing **scholarly articles for peer readers in any
discipline** — philosophy, the empirical sciences, mathematics: how the
argument is laid out so that a reader moving through the text in order can
follow and check it.

## Scope and boundaries

| Relation | Domain | Difference |
|----------|--------|------------|
| Parent of specific axioms (generalization) | `mathematical-writing` | That domain covers formal mathematical exposition (theorem / remark architecture). Where an axiom here generalizes one there beyond formal mathematics, it names its parent by id in a `generalizes` field. |
| Distinct | `apa7-style` | Formatting and citation style; this domain covers the order and structure of the argument. |
| Distinct | `academic-presentation` | Spoken talks with slides; this domain covers written articles. |
| Distinct | `note-writing` | Private notes for the writer; this domain is addressed to peer readers. |

## Axioms

| ID | Name | One-liner |
|----|------|-----------|
| `A1_no_forward_dependence` | No forward dependence in any scholarly article | Rest only on items already met; a pointer ahead is a roadmap or a promissory note, nothing else. Generalizes `mathematical-writing/A4_reading_order_dependence`. |
| `A2_motivated_by_prefix` | Each element of a scholarly article is called for by what precedes it | An example, a definition, a finding or a quotation arrives only after the reader holds the question it answers. Generalizes `mathematical-writing/A5_motivated_by_prefix`. |
| `A3_literature_at_introduction` | Each object is introduced with its own literature; the broad review comes later | Where an object from prior work first appears, one or two sentences give its source and the property the article relies on; the wider review goes in a later section of its own. |
| `A4_own_results_after_question` | In the Introduction, the article's own results come after the research question | Before the Introduction states the research question it gives what is known, the setting and the gap; what the article itself establishes comes after the question. |

## Provenance

Seeded on 2026-10-10 at the user's request, in their words:

> 幫我寫在rule裡面與 axiomsystem裡面不能前向引用（所有文章都不適合，除非有例外）

The request arose while removing a forward reference from a philosophy
manuscript (Leibniz on machine-generated proofs, for *Synthese*); A1's
violation and compliant examples are the before and after of that fix.

## Growth path

Seeded with reading-order dependence (A1); A2 (each element called for by what
precedes it), A3 (each object introduced with its own literature, the broad
review later) and A4 (in the Introduction, the article's own results after the
research question) were added on 2026-11-23 at the author's request. Further axioms of article craft
belong here when they hold across disciplines; axioms specific to formal
mathematical exposition stay in `mathematical-writing`.

Follows **SCD2 (add-only)**: axioms accumulate; existing ones are annotated, not
rewritten. Validate structure and cross-domain consistency with `/axiom-validate`.
