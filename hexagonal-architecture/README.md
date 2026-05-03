# Hexagonal Architecture

*Under what conditions is hexagonal architecture true?*

Hexagonal architecture often fails while looking correct.

This folder asks why.

It treats hexagonal architecture not as a pattern to apply, but as a structural operation. That operation can succeed or fail independently of whether the visible form has been respected. A system may have a `domain` folder, declared ports, isolated adapters, inward dependencies, and infrastructure-free tests while still failing to localize what matters.

The question is not whether the hexagon is visible.

The question is what the frontier makes the application able to answer for.

## The core displacement

Most explanations of hexagonal architecture start with shape: domain inside, adapters outside, dependencies pointing inward.

This folder starts elsewhere.

A boundary is valuable only if it carries something: a duration, a commitment, a consequence, a correction. If it carries none of these, it is only a form. If it carries them badly, it may hide the very domain it was supposed to reveal.

The guiding question is therefore:

> What does this hexagonal boundary answer for?

In this corpus, **answerability** means the structural capacity of a system to make a rule, commitment, failure, or consequence return to a named place where it can be understood and corrected.

## The reading pact

This folder is organized in four levels of increasing depth.

Each level is sufficient for what it promises.

If you stop at level 1, you have the claim.
If you stop at level 2, you have the argument.
If you stop at level 3, you have the defense.
If you stop at level 4, you have the application.

You are not missing a hidden chapter. The deeper levels do not reveal a different thesis. They put the same thesis under stronger conditions of justification.

## The four levels

**[`claim.md`](./claim.md)** - *5 minutes.*

What this work asserts, what it commits to, and what it excludes. Read this first if you want the thesis without the full reasoning.

**[`argument.md`](./argument.md)** - *15 to 20 minutes.*

The reasoning that makes the claim necessary. It moves from the failure of formally correct hexagonal architectures to the structural role of the boundary: institution, duration, core failure modes, ports, transactions, and services.

**[`defense.md`](./defense.md)** - *45 minutes.*

The thesis tested against counter-examples, adjacent positions, competing readings, and its own limits. Read this if you want to challenge the work rather than only understand it.

**[`application.md`](./application.md)** - *operational.*

The tools derived from the thesis: the ontological test, the evidence protocol, the diagnostic grid, the drift typology, the correction order, and the decision record. Read this if you need to apply the work to a real project.

## Code examples

Code appears only where it carries proof.

The examples are not tutorials. They are structural probes. Their role is to expose the difference between a form that looks correct and a form that actually carries an invariant, a conversation, a commitment, or a correction path.

## Companion concepts

Some concepts can circulate independently from the four levels and may deserve separate essays later:

- **conversation**: the boundary as a legitimacy of conversation, not only a separation of code;
- **transduction**: the mapper as an organ of semantic decision disguised as plumbing;
- **answerability**: the structural return of consequences to a named place of correction;
- **consequence-bearing software**: software whose structures carry what they make possible.

## Glossary

`GLOSSARY.md` should define the canonical vocabulary of the corpus:

- answerability;
- consequence-bearing;
- load-bearing;
- instituted core;
- empty core;
- mimed core;
- diffuse core;
- substantive model;
- port as conversation;
- silent transaction;
- locus of correction;
- transduction;
- drift.

The glossary is not decorative. It protects the corpus against vocabulary drift.

## References

`references.md` should remain annotated. Its purpose is not only to list sources, but to make explicit what each reference contributes to the argument.

## Suggested path

Read `claim.md` first.

If the claim feels obvious, read `argument.md` to see whether it follows.

If the argument feels too strong, read `defense.md` to see what it survives and where it stops.

If you need to use the work on a project, read `application.md` last.

Do not begin with the tools. A checklist without its thesis becomes another form of structural theater.
