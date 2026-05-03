# The Defense

*Level 3. Thirty minutes. The thesis tested against counter-examples, alternative readings, and adjacent positions.*

Level 2 established the argument. This level tests it.

A thesis that has not faced its strongest objections is not yet defensible. The defense unfolds in four movements: counter-examples, relation to the literature, differential comparison of architectural styles, and zone of validity.

## I. Counter-examples

### Objection 1. Some light hexagonal architectures work

Some teams maintain, for years, a modest hexagonal structure on what first appears to be an orchestrator. They draw real benefit from it: shared landmarks, agreed places for responsibilities, stable conversations with other teams.

If the thesis is true, how can this be?

Two readings preserve the thesis.

First, these teams may be using hexagonal vocabulary as organizational scaffolding without claiming to institute a substance. They do not promise a core. They give themselves a map. The value is real, but it is the value of shared geography, not of structural commitment.

Second, these teams may have identified modest but real candidates: an idempotency policy, a traceability discipline, an identity rule, a publication contract. What appears light is modest in scope, not absent in substance.

In both readings, the thesis holds. What it requires is honesty about the claim being made.

If the team says, *we are instituting a domain*, they must name what answers. If the team says, *we are giving ourselves a map*, the cost and benefit must be evaluated as such.

The danger is the team that claims the first while doing the second.

### Objection 2. Some substantive cores need no hexagon

An application can carry a substantive core without formal hexagonal architecture. A functional core with rich types, algebraic data types, typed effects, and explicit signatures may hold invariants as well as, or better than, an object-oriented hexagonal design.

Does this refute the thesis?

No.

The thesis does not say that hexagonal architecture is the only form of institution. It says that when one chooses hexagonal architecture, the thing at stake is institution.

A functional core also institutes. It does so through signatures, exhaustive types, impossible states, explicit effects, and composition laws. What strong ports do in hexagonal architecture, function signatures may do in functional architecture. What transduction names, sum types may force. What tests prove in one style, the type system may exclude in another.

The thesis gains scope through this objection. Institution is the broader prism. Hexagonal architecture is one of its forms, particularly visible in object-oriented or imperative contexts where the type system alone does not carry enough structural force.

### Objection 3. Institution is just ubiquitous language

A domain-driven design reader might say that institution merely renames the ubiquitous language.

It does not.

The ubiquitous language is a social condition: the team and the business share words, and those words live in conversation and code.

Institution is a structural condition: the code contains words, constraints, and commitments that depend on the world being maintained, and that resist the grammar of external mechanisms.

The two conditions reinforce each other. They are not synonyms.

A team may have an excellent ubiquitous language and a weak institution: everyone shares the words, but the code does not make invalid states impossible. Another team may have a strong institution and a weak ubiquitous language: the code prevents invalid states, but the team has not yet made the grammar shareable with business interlocutors.

Institution is what the code does. Ubiquitous language is what the team and the business can say together. A mature architecture holds both.

### Objection 4. The thesis over-intellectualizes a practical pattern

One might argue that hexagonal architecture is simple: keep the domain independent from infrastructure. Why introduce institution, answerability, duration, and commitment?

Because the simple reading fails to explain the regular phenomenon that motivated this work: teams can keep the domain independent from infrastructure at the import level while allowing infrastructure, source formats, generic errors, service order, and transaction placement to decide the meaning of the application.

The additional vocabulary is justified only if it explains failures that the simpler vocabulary cannot see. That is the case here.

A dependency graph can show whether an import points inward. It cannot show whether the outside has already named the inside.

## II. Position relative to the literature

This work does not attempt to replace the literature. It differentiates itself from it.

### Cockburn: boundary

Cockburn gives the founding intuition of ports and adapters: an application should be drivable from multiple peripheries without depending on them directly.

This work keeps that intuition and sharpens one point: a port is not merely an interface of call. It is an intentional conversation. The dependency inversion matters, but the vocabulary carried by the dependency matters as much.

### Parnas: hidden decisions

Parnas gives the deep modular principle: decompose systems by hiding design decisions likely to change.

This work extends the question from hidden decisions to localized consequences. A hidden decision is one kind of protected change. A localized commitment is another kind of structural responsibility. The boundary must not only hide what may vary; it must carry what has been engaged.

### Fowler: anemia

Fowler warns against anemic domain models: domain objects that carry data while behavior lives elsewhere.

This work agrees, but shifts the criterion. Anemia is not only a lack of behavior. It is the separation of name and consequence. A model can have many methods and still fail to make invalid states impossible. A model can have few methods and still be substantive if its types and constructors prevent impossible states.

The criterion is not method count. It is what the model renders impossible.

### Evans and Vernon: model integrity

Domain-driven design gives the model, the bounded context, the ubiquitous language, and the anti-corruption layer.

This work follows that line and hardens the meaning of corruption. Corruption is not only model mixing. It is also ontological dependence: the outside imposes the objects, categories, states, and temporalities through which the application understands itself.

Anti-corruption is therefore not only translation between models. It is the defense of the application's right to think in its own terms.

### Martin: rule levels

Clean Architecture distinguishes enterprise rules, application rules, and interface concerns.

This work agrees that not every rule belongs in an entity. The problem is not that a rule lives in a use case. The problem is that a rule lives at a level that does not match its duration, locus of variation, or locus of correction.

Duration and answerability make the placement criterion stricter.

### Suchman, Weick, Bowker and Star, Scott

These authors are not pattern authors. Their relevance is different. They show that systems organize what can be seen, said, classified, recovered, and corrected.

A hexagonal boundary that holds is not only technical separation. It organizes visibility, vocabulary, refusal, commitment, and correction. A hexagonal boundary that fails can make a system cleaner while making it less true.

## III. Differential comparison of architectural styles

The point of the following comparison is not ranking. It is differentiation.

| Style | What it institutes | What it protects well | What it cannot do alone | When to prefer it |
| --- | --- | --- | --- | --- |
| Simple layers | Organization by technical responsibility | Separation of technical concerns | Real inversion of conceptual dependency | CRUD, disposable applications, low-stakes workflows |
| Hexagonal architecture | Boundary between applicative core and mechanisms | Durable applicative invariants and commitments | Multi-context strategy by itself | Substantive domain, variable periphery, long lifespan |
| Onion architecture | Radial stratification by stability | Stability of the core against the periphery | Distinction between application and entity rules by itself | Rich entity invariants, strong inner model |
| Clean Architecture | Stratification by rule level | Difference between enterprise and application rules | Ontological boundary by itself | Use cases with substantial applicative logic |
| Vertical slice | Isolation by feature or capability | Independent feature evolution | Cross-feature invariants | Features with little shared domain substance |
| Event sourcing | Event grammar as system substance | Traceability and state derivation | Transactional coherence by itself | Audit, finance, regulated history, irreversible events |
| CQRS | Asymmetry between write and read | Read scalability and model specialization | Institution of the write core by itself | Heavy read sides, multiple projections, query diversity |

These styles are not mutually exclusive. Serious systems often combine them: hexagonal for the write core, CQRS for read models, event sourcing for traceable commitments, vertical slicing for team-aligned delivery.

The table is not a choice tree. It is a grammar of combination.

## IV. Zone of validity

The thesis is not universal.

It applies when an application maintains a world against a variable periphery. If the principal work of the application is to represent, optimize, compose, or expose a capability, then the frame of world-maintenance may be wrong, and the hexagonal frontier may not carry what it claims to carry.

### Case A. The core does not exist

For a disposable prototype, a simple CRUD, a temporary gateway, a purely technical transformation, or an integration without its own invariants, there is no world to maintain.

Hexagonal architecture here institutes a void. A simpler architecture will almost always be more honest.

### Case B. The core exists, but hexagonal is not the right form

**Heavy read sides.** The difficulty is not protecting invariants but producing coherent representations from heterogeneous sources. A per-projection or per-query architecture may be more honest. Hexagonal may still belong on the write side.

**Numerical optimization.** The substance lives in mathematical formulation: convergence, complexity, stability, optimality. Hexagonal architecture does not carry these invariants well by itself.

**Creation tools.** Editors, design tools, and interactive environments often revolve around operations on rich state. Command, history, projection, and reactivity may fit better than a classical boundary between core and UI.

**Pure platforms.** In libraries, frameworks, and runtimes, the domain is the public API. There is no external world to filter in the same sense. The hexagonal frontier may duplicate what good API design already does.

### A discriminating question

Ask:

> If I replaced tomorrow all peripheral infrastructure while keeping the internal code intact, what would remain to be protected?

If the answer is a set of invariants and commitments that maintain a world, hexagonal architecture is appropriate.

If the answer is a coherent representation of data from elsewhere, it is likely a read side.

If the answer is a mathematical formulation and its resolution quality, it is likely optimization.

If the answer is a grammar of operations on user-composed state, it is likely a creation tool.

If the answer is a capability offered to other applications, it is likely a platform.

For systems where hexagonal architecture is appropriate, it becomes necessary only on condition of being substantive: ports as conversations, models that make invalid states impossible, named flow policies, discriminating errors, explicit units of commitment, tests of invariants, recognized strata of duration, and assumed loci of correction.

## Conclusion of the defense

The thesis has survived the objections that should have threatened it. It has been differentiated from adjacent literature. It has named the conditions under which it applies and the conditions under which it does not.

This does not make it proven in a formal sense. Software engineering theses of this kind are not proven like theorems. But it has earned the right to be used.

The application is the task of [`application.md`](./application.md).

You have the defense. That is what level 3 promised.
