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
| `A5_case_frame` | A discussion by cases has a frame: announced, in order, exhaustive | Before the first case, the text names the question, the scope, the cases and their order; the cases are then discussed in that order, each once; together they cover the scope, which is the range the question was raised with and not one the announcement chooses. |
| `A6_topic_once` | Each topic is treated in one place | What the body asserts about a topic stands together: a later assertion about it that depends on nothing introduced since is a return. A backward reference that leaves the earlier assertions as they were, an announced continuation and the framing sections are not returns. |
| `A7_no_open_question` | No question that the text raises is left open | A question the text has made the reader ask is closed before the flow turns to anything else: answered, deferred to a named place, or declared open. Between the question and its closing stand only parts of the answer. The converse of A2. |
| `A8_rearrangement_operations` | A flow is rearranged only by the listed operations | To make a flow read in order, ideas may be swapped, moved earlier, moved later, merged or split, each under its condition; no claim is deleted, duplicated, added or restated. The list is closed, and it is a proposal for the author to cut or extend. |
| `A9_contributions_displays_appendix` | The contributions, the figures and tables, and the appendix are planned with the flow | A flow comes with three lists tied to its ideas: a list of contributions, not empty, each naming the idea that establishes it; for each section its figures and tables, each with a home idea; and for each section what goes to the appendix, whose ideas are ideas of the flow. |

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

A5 to A9 were added on 2026-11-26 at the author's request (issue #47). They are
stated on the *flow* of an article, the ordered list of its ideas, and each can
be decided on a given flow: a frame for a discussion by cases (A5), each topic
treated in one place (A6), no question left open (A7, the converse of A2), the
closed list of rearrangement operations (A8), and the list of contributions, the
figures and tables and the appendix planned with the flow (A9). The list of
operations in A8 is a proposal for the author to cut or extend. On the same day
A1 received one more violation and one more compliant example, for the
announcement of a complete worked example that is given later: the announcement
is A1's exception (1), the roadmap, and not a third exception. The rule on the
order of a general and a simple case is `mathematical-writing/A7_general_case_first`.

Follows **SCD2 (add-only)**: axioms accumulate; existing ones are annotated, not
rewritten. Validate structure and cross-domain consistency with `/axiom-validate`.
