# Hexagonal Architecture

*Under what conditions is hexagonal architecture true?*

Hexagonal architecture often fails while looking correct.

This folder asks why.

It treats hexagonal architecture not as a pattern to apply, but as a structural operation. That operation can succeed or fail independently of whether the visible form has been respected. The question is not whether the code contains a `domain` folder, declared ports, isolated adapters, and inward dependencies. The question is what the frontier makes the application capable of answering for.

## The pact

This folder is organized in four reading levels of increasing depth. Each level is sufficient for what it promises.

If you stop at level 1, you have the claim.
If you stop at level 2, you have the argument.
If you stop at level 3, you have the defense.
If you stop at level 4, you have the application.

You are not missing a hidden chapter. The deeper levels do not reveal a different thesis. They place the same thesis under stronger conditions of justification.

## The four levels

**[`claim.md`](./claim.md)** - *5 minutes.*

The thesis stated directly: what it asserts, what it commits to, and what it excludes. Read this if you want to know whether the work is worth your time before entering the reasoning.

**[`argument.md`](./argument.md)** - *15 minutes.*

The reasoning that makes the claim necessary. It moves from the observed failure of formally correct hexagonal architectures to the structural role of the boundary: institution, duration, core failure modes, ports, transactions, and services.

**[`defense.md`](./defense.md)** - *30 minutes.*

The thesis tested against counter-examples, adjacent positions, and competing architectural readings. Read this if you want to argue with the work rather than only understand it.

**[`application.md`](./application.md)** - *operational.*

The tools derived from the thesis: the ontological test, the diagnostic checklist, and the drift typology. Read this if you need to apply the work to a real project on a real Monday morning.

## Companion essays

Some concepts deserve separate treatment because they can circulate independently from the main four levels.

**`conversation.md`** - on the boundary as a legitimacy of conversation, not only a separation of code.

**`transduction.md`** - on the mapper as an organ of semantic decision disguised as plumbing.

They are not required to follow the four levels. They extend specific concepts for readers who want to push them further.

## Glossary

**`GLOSSARY.md`** should define the canonical vocabulary of the corpus: answerability, consequence-bearing, load-bearing, instituted core, empty core, mimed core, diffuse core, substantive model, port as conversation, silent transaction, and locus of correction.

The most important term is **answerability**: the structural capacity of a system to make a rule, commitment, failure, or consequence return to a named place where it can be understood and corrected.

## References

**`references.md`** should remain annotated. Its purpose is not only to list sources, but to make explicit what each reference contributes to the argument.

## How to read this folder

Read `claim.md` if you want the position.
Read `argument.md` if you want the reasoning.
Read `defense.md` if you want the objections.
Read `application.md` if you want the tools.

Do not start with the tools if you have not understood the thesis. A checklist detached from its reason becomes exactly the kind of formal correctness this work was written to question.
