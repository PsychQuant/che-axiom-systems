# Academic Project Management

Axiomatizes how a **research project** is kept: the folder that holds one
manuscript with the literature it cites, the data and programs behind its
numbers, and the tools it measures with.

## Scope and boundaries

| Relation | Domain | Difference |
|----------|--------|------------|
| Distinct | `academic-writing` | The text of the article: the order and structure of its argument. This domain covers the project around the text. |
| Distinct | `apa7-style` | Citation and formatting style. A1 and A2 here say where the cited works are kept, not how they are cited. |
| Distinct | `academic-presentation` | Talks and slides. |
| Distinct | `note-writing` | Private notes. |

## Axioms

| ID | Name | One-liner |
|----|------|-----------|
| `A1_references_hold_every_cited_work` | The references folder holds the full text of every cited work | Every work the manuscript cites has its full text in the project's references folder. |
| `A2_one_original_per_full_text` | Each work has one original full text, in the library; the project holds exported copies | A PDF in the project is a copy exported from the library's original, never a file copied from elsewhere. |
| `A3_every_number_traceable` | Every number in the manuscript can be traced to what produced it | Each value the study computed, and each table and figure built from them, has a record of how to reproduce it. |
| `A4_raw_data_immutable` | Raw data are never modified; derived data can be regenerated | Raw data stay as received, processed data come from programs, outputs go apart; paths start at the analysis root. |
| `A5_third_party_and_copyrighted_off_remote` | Raw third-party material, copyrighted full texts and restricted data stay off the remote | Three kinds of material never go to a remote; the author's own writing, code and edited transcripts may. |
| `A6_archive_append_only` | The archive is append-only | Nothing under archive/ is deleted, moved, overwritten or edited; new things may be added. |
| `A7_nested_repos_named_by_role` | A repository placed inside a project is named by its role | Another repository inside a project lives in a folder named for what the project does with it. |
| `A8_frozen_instruments` | A measuring instrument is frozen while the study uses it | An instrument is not upgraded during a study; an upgrade needs a deviation note first, and versions are recorded with the results. |
| `A9_compile_after_every_edit` | The manuscript is compiled and checked after every edit | After any change to the manuscript source, run the full compile and check five counts are zero before committing. |

## Provenance

Seeded on 2026-11-23 at the author's request, in their words:

> che-axioms我想要加入一個 academic project的管理的axioms，例如： references 資料夾裡面要放所有這篇文章會引用到的文獻

That example is A1. A2 to A9 were offered as candidates, each from a rule the
author had already written down or from the practice of their projects, and
the author chose all eight the same day. Each axiom's rationale names its
source.

## Growth path

Further axioms belong here when they concern how a project is kept rather
than what its text says: for example submission records, collaborator
agreements, or how a project is closed and archived.
