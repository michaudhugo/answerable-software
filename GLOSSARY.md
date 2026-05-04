# Glossary

This glossary defines the canonical terms used across the corpus.

It is not a dictionary of fashionable software words. It names the distinctions the corpus depends on. A term belongs here only if misunderstanding it would weaken the argument, the diagnosis, or the application of the work.

## How to read this glossary

Each entry follows the same structure where useful:

- **Definition**: what the term means in this corpus.
- **Not to be confused with**: nearby meanings that should not be collapsed into it.
- **Why it matters**: the practical consequence of the distinction.

---

## Core terms

### Answerability

**Definition.**  
Answerability is the structural capacity of a system to make a rule, commitment, failure, or consequence return to a named place where it can be understood, owned, and corrected.

A system is answerable when its structure can say:

- what was committed;
- what failed;
- which world, rule, or commitment was violated;
- where the consequence returns;
- what can correct it.

**Short form.**  
Answerability means that consequences have a place to return.

**Not to be confused with.**  
Answerability is not the same as accountability. Accountability usually asks who is responsible. Answerability asks where, in the system, a consequence returns so that it can be interpreted and corrected.

Answerability is also not observability. Observability may show what happened. Answerability shows what was violated and where correction belongs.

**Why it matters.**  
A system can be observable, owned, documented, and formally structured while still being unanswerable. It may show traces, assign teams, and pass tests, yet leave consequences without a responsible structural place.

---

### Consequence

**Definition.**  
A consequence is what follows from a decision, rule, transition, action, or commitment in a way that the system must be able to bear, localize, or correct.

A consequence is not merely an output. It is an effect that changes what the system, its users, or its environment may now rely on.

**Not to be confused with.**  
A result is what a computation returns. An effect is what a computation causes. A consequence is what the system must answer for after something has been caused.

**Why it matters.**  
Architectures often track outputs and effects while failing to localize consequences. The corpus judges structures by whether they carry the consequences they make possible.

---

### Consequence-bearing

**Definition.**  
A structure is consequence-bearing when it carries, localizes, and remains answerable for the consequences it enables.

A model is consequence-bearing when it prevents invalid states. A port is consequence-bearing when it names an application conversation that can fail, be corrected, or be fulfilled. A transaction is consequence-bearing when it names what becomes irreversible together. A test is consequence-bearing when it protects an invariant or a commitment, not merely an execution path.

**Not to be confused with.**  
Consequence-bearing does not mean consequence-driven. The consequence does not drive the work like a method. It is what the structure must carry.

**Why it matters.**  
This is one of the broadest criteria of the corpus. It distinguishes decorative structure from structure that bears the weight of what the system makes possible.

---

### Load-bearing

**Definition.**  
A software structure is load-bearing when it carries a real structural charge: meaning, consequence, duration, correction, or commitment. If removed or weakened, something important collapses or becomes unlocalized.

**Not to be confused with.**  
Load-bearing does not mean frequently used. A class, convention, or folder can be used everywhere and still carry no real responsibility. Conversely, a small type or error class can be load-bearing if it prevents an invalid state or preserves a correction path.

**Why it matters.**  
Many architectures contain visible structures that are not load-bearing: interfaces that name tools, domain folders without invariants, services that only move data, tests that only prove mocks were called. The corpus asks what actually carries weight.

---

### Correction locus

**Definition.**  
A correction locus is the named structural place to which a failed consequence returns so that it can be interpreted and corrected.

A correction locus can be a model, policy, error type, workflow, retry mechanism, compensation path, decision record, team-owned boundary, or unit of commitment, provided that it actually receives the consequence and makes correction possible.

**Not to be confused with.**  
A correction locus is not merely a log line, dashboard, alert, ticket, or owner. These may help, but they do not themselves define how the system understands the failure.

**Why it matters.**  
If a consequence has no correction locus, the system may fail intelligibly at runtime but unintelligibly at the architectural level. Everyone can see that something failed. No one can say where the failure belongs.

---

### Institution

**Definition.**  
Institution is the operation by which a software structure gives a responsibility, rule, distinction, or commitment a durable place in the system.

To institute is not merely to name. It is to make something structurally real enough that other parts of the system can depend on it, test it, reject violations of it, and return consequences to it.

**Not to be confused with.**  
Institution is not documentation. It is not intention. It is not naming alone. A rule is not instituted because the team says it exists. It is instituted when the structure of the system gives it force.

**Why it matters.**  
The corpus reads hexagonal architecture as an operation of institution. The boundary does not simply protect a core. It calls a core to become structurally real.

---

### World-maintenance

**Definition.**  
World-maintenance is the work an application performs when it preserves a coherent set of rules, identities, states, commitments, meanings, and correction paths against a variable environment.

An application maintains a world when it does more than transform inputs into outputs. It sustains a way in which things can be valid, invalid, committed, rejected, corrected, or remembered.

**Not to be confused with.**  
World-maintenance is not domain complexity in general. A system may be complex because it optimizes, represents, or composes. It maintains a world only when it protects a coherent internal order of meaning and consequence.

**Why it matters.**  
Hexagonal architecture is most appropriate when the application maintains a world against volatile mechanisms. If the principal work is representation, optimization, composition, or pure capability exposure, another architectural form may be more honest.

---

## Hexagonal architecture terms

### Boundary

**Definition.**  
A boundary is the structural frontier through which an application distinguishes what must be expressed in its own terms from what belongs to mechanisms, protocols, frameworks, databases, SDKs, or third-party systems.

A boundary is not only spatial. It is temporal and semantic. It separates what may change quickly from what deserves to endure, and it prevents external mechanisms from naming the internal world.

**Not to be confused with.**  
A boundary is not a folder, a package, an interface, or a dependency rule by itself. Those can implement a boundary. They do not guarantee one.

**Why it matters.**  
A boundary that does not localize responsibility, duration, and correction is a visible separation without answerability.

---

### Hexagonal frontier

**Definition.**  
The hexagonal frontier is the boundary drawn between the application core and the mechanisms that drive it or are required by it.

In this corpus, the frontier is judged not by whether it is drawn, but by what it institutes and what it makes answerable.

**Not to be confused with.**  
The frontier is not the hexagon diagram. The diagram is only an icon. The frontier exists only where the code and the team can defend the distinction it claims.

**Why it matters.**  
Many teams reproduce the iconography of hexagonal architecture while leaving the real frontier undefined.

---

### Core

**Definition.**  
The core is what the application must continue to know, preserve, refuse, or commit to independently of its current mechanisms.

The core can be an entity model, a policy, a grammar of flow, a transaction boundary, a rule system, or a set of typed consequences. It is not necessarily a set of rich objects.

**Not to be confused with.**  
The core is not the `domain` folder. It is not automatically the model layer. It is not whatever has the least infrastructure imports.

**Why it matters.**  
A system can have a central folder and no core. It can also have a real core dispersed across services, mappers, errors, and ordering rules.

---

### Instituted core

**Definition.**  
An instituted core is a core whose rules, distinctions, commitments, and correction paths have been given structural force.

It does not merely describe the domain. It prevents invalid states, names legitimate conversations, defines commitments, and gives consequences a place to return.

**Not to be confused with.**  
An instituted core is not a domain model that merely uses business nouns. It is a structure that carries consequences.

**Why it matters.**  
The goal of a strong hexagonal architecture is not to place code at the center. It is to institute a core that can answer for what the application does.

---

### Empty core

**Definition.**  
An empty core appears when an application has no real candidate for institution but still adopts the hexagonal form.

It receives, transforms, validates superficially, persists, and transmits, but carries no durable rule, distinction, policy, or commitment of its own.

**Not to be confused with.**  
An empty core is not necessarily bad software. A pipeline, gateway, synchronization job, or temporary integration can be honest and well built without a substantial core.

**Why it matters.**  
The failure is not simplicity. The failure is pretending that a simple passage contains a durable core when it does not.

---

### Mimed core

**Definition.**  
A mimed core appears when the system produces the signs of a domain without producing its force.

It has the right names, folders, entities, ports, and tests, but the model does not prevent invalid states, the ports name mechanisms, and the services secretly decide.

**Not to be confused with.**  
A mimed core is not an absent core. It is a performed core. It resembles the domain enough to be mistaken for it.

**Why it matters.**  
Mimed cores are dangerous because they pass many superficial reviews. They look architecturally correct while failing to carry consequences.

---

### Diffuse core

**Definition.**  
A diffuse core appears when the domain is not absent, but dispersed across places the architecture does not recognize as responsible.

It lives in conditions, mappers, services, call options, generic errors, ordering rules, observability conventions, source-system vocabulary, and developer memory.

**Not to be confused with.**  
A diffuse core is not a mimed core. In a mimed core, a visible rule exists at the wrong level or without enough force. In a diffuse core, the rule is scattered across several locally plausible places and becomes invisible as a rule.

**Why it matters.**  
The diffuse core is often the most common and serious pathology. The system has intelligence, but no structural place answers for it.

---

### Domain folder

**Definition.**  
A domain folder is a code organization device that may contain domain-related code.

**Not to be confused with.**  
A domain folder is not a domain. A folder cannot make states impossible, name commitments, or localize consequences by itself.

**Why it matters.**  
Teams often mistake the presence of a `domain` folder for the presence of a domain. The corpus refuses that equivalence.

---

### Port

**Definition.**  
A port is a conversation the application recognizes as legitimate with its environment.

A port states either what the outside may ask of the application, or what the application requires from the outside, in terms that should survive replacement of the current mechanism.

**Not to be confused with.**  
A port is not merely an interface. An interface describes a possible call. A port names an application conversation.

**Why it matters.**  
If a port is named by the mechanism it abstracts, the outside has already named the inside. The dependency may be inverted technically while remaining conceptually external.

---

### Port as conversation

**Definition.**  
Port as conversation names the principle that a port should express a legitimate application relation, not a technical primitive.

Examples of weak port language include `save`, `fetch`, `push`, `publish`, `send`, and `move`. Examples of stronger port language include resolving an identity, registering a decision, making a consolidation available, isolating an incoherent signal, or publishing a validated consequence.

**Not to be confused with.**  
This principle does not forbid interfaces. It says that when interfaces implement ports, their names and contracts must express application meaning rather than mechanism vocabulary.

**Why it matters.**  
Port naming is one of the fastest ways to detect whether the outside still thinks on behalf of the application.

---

### Primary port

**Definition.**  
A primary port is a way the outside drives the application.

It answers: who has the right to address the application, and in what terms?

A strong primary port turns external requests into typed, qualified, internal intentions.

**Not to be confused with.**  
A primary port is not the HTTP controller, message consumer, CLI handler, or scheduled job itself. Those are primary adapters. The port is the application conversation they must enter.

**Why it matters.**  
Weak primary ports let payloads pass through too far. The outside keeps its format, ambiguity, and vocabulary inside the system.

---

### Secondary port

**Definition.**  
A secondary port is what the application requires from the outside to accomplish its work.

It answers: what capability does the application ask of the world, and in what terms?

**Not to be confused with.**  
A secondary port is not a database repository by default. A repository can implement a secondary port, but the port should name the application requirement, not the storage mechanism.

**Why it matters.**  
Weak secondary ports abstract tools while preserving tool grammar. Strong secondary ports express application requirements that survive mechanism replacement.

---

### Adapter

**Definition.**  
An adapter is the concrete translation between an application conversation and a mechanism.

An adapter knows both languages: the application language and the mechanism language. Its duty is to translate without letting mechanism vocabulary colonize the core.

**Not to be confused with.**  
An adapter is not disposable plumbing. It can be a decisive place of translation. But it should not silently own the application rule it translates.

**Why it matters.**  
Bad adapters leak external categories inward. Good adapters translate external mechanisms into internal meanings and internal requirements into external operations.

---

### Conceptual dependency

**Definition.**  
A conceptual dependency exists when the application thinks with the categories, names, states, temporalities, or assumptions of an external mechanism, even if the technical dependency has been inverted.

**Not to be confused with.**  
A conceptual dependency is not visible in imports alone. A dependency graph can look correct while the vocabulary remains colonized.

**Why it matters.**  
Hexagonal architecture can fail even when dependencies point inward if the external world still names the internal one.

---

### Mechanism

**Definition.**  
A mechanism is a concrete technical means by which the application is driven or served: a database, message broker, framework, SDK, protocol, file system, API, vendor, runtime, or infrastructure service.

**Not to be confused with.**  
A mechanism is not automatically outside the architecture's concern. Mechanisms matter. But they should not define the application world unless the system's purpose is precisely to expose that mechanism.

**Why it matters.**  
The value of the boundary is to prevent the mechanism from deciding what the application means.

---

## Modeling terms

### Model

**Definition.**  
A model is a structure that gives force to distinctions in the system. In its strongest form, it prevents invalid states, names valid transitions, distinguishes violations, and carries consequences.

**Not to be confused with.**  
A model is not a data shape. It is not a collection of nouns. It is not a diagram that merely describes a domain.

**Why it matters.**  
A model is judged by what it makes impossible and what it makes answerable.

---

### Nominal model

**Definition.**  
A nominal model has the right names but little or no governing force.

It names `Customer`, `Order`, `Account`, or `Contract`, but does not prevent invalid states or invalid transitions.

**Not to be confused with.**  
A nominal model is better than pure technical vocabulary, but it is not yet substantive.

**Why it matters.**  
Nominal models create the impression of domain orientation without carrying domain consequences.

---

### Descriptive model

**Definition.**  
A descriptive model structures domain data correctly but still does not govern the domain.

It knows that an order has lines, an account has a balance, and a customer has identifiers. It describes the world, but does not yet constrain it.

**Not to be confused with.**  
Descriptive correctness is useful. It is not the same as architectural substance.

**Why it matters.**  
Many anemic models are descriptive rather than substantive. They are not wrong. They are insufficient for a core that must carry consequences.

---

### Substantive model

**Definition.**  
A substantive model carries consequences by making certain states impossible, certain transitions explicit, and certain violations visible.

The criterion is not how many methods the model has. The criterion is what the model prevents and what it can answer for.

**Not to be confused with.**  
A substantive model is not necessarily object-oriented. It can be built through rich types, value objects, sum types, state machines, algebraic data types, event grammars, policies, or constrained constructors.

**Why it matters.**  
This term replaces the weak debate around whether domain objects should have many methods. Substance is about force, not style.

---

### Anemic model

**Definition.**  
An anemic model is a model whose domain names are separated from the consequences those names should carry.

In this corpus, anemia is not merely the lack of behavior on objects. It is the failure to localize consequences where the model claims the domain lives.

**Not to be confused with.**  
An object with few methods is not necessarily anemic. An object with many methods is not necessarily substantive.

**Why it matters.**  
A hexagonal architecture with an anemic model can protect vocabulary while failing to protect meaning.

---

### Impossible state

**Definition.**  
An impossible state is a state the system's structure prevents from existing, rather than merely detecting after the fact.

**Not to be confused with.**  
An invalid state that is detected later is not impossible. It is allowed and then rejected. That may be acceptable at boundaries, but a core invariant should generally be impossible by construction.

**Why it matters.**  
The ability to make invalid states impossible is one of the strongest signs of a substantive model.

---

### Invariant

**Definition.**  
An invariant is a condition that must remain true across the relevant life of a model, workflow, commitment, or system state.

**Not to be confused with.**  
An invariant is not a validation rule by default. A validation rule may check an invariant, but an invariant is the durable condition being protected.

**Why it matters.**  
Tests, models, and boundaries become stronger when they protect invariants rather than execution paths.

---

### Valid transition

**Definition.**  
A valid transition is an allowed movement from one state, meaning, commitment, or consequence to another.

**Not to be confused with.**  
A transition is not only a state-machine edge. In workflow and flow systems, it may be a qualification, rejection, publication, compensation, or escalation.

**Why it matters.**  
Strong models do not only define valid states. They define legitimate transitions and reject illegitimate ones.

---

## Temporal terms

### Duration

**Definition.**  
Duration is the expected life of an inscription in the system: how long a rule, name, decision, dependency, policy, threshold, or commitment deserves to remain stable.

**Not to be confused with.**  
Duration is not calendar age. Something old can be volatile. Something newly introduced can be foundational.

**Why it matters.**  
A boundary is partly a decision about duration. What deserves to endure should not depend on what changes quickly.

---

### Strata of duration

**Definition.**  
Strata of duration are levels of expected stability inside a system.

A practical distinction used in the corpus:

| Stratum | Typical cadence | Examples |
| --- | --- | --- |
| Foundational | Decade or more | Identity rules, accounting invariants, structural regulatory constraints |
| Policy | Multi-year | Procedures, taxonomies, eligibility rules, governance conventions |
| Functional | Yearly | Use cases, journeys, campaign rules, business parameters |
| Parametric | Sub-yearly | Thresholds, certificates, quotas, feature flags, library versions |

**Not to be confused with.**  
These strata are not rigid categories. They are diagnostic distinctions. The question is not the label, but whether the location of the rule matches its legitimate cadence of change.

**Why it matters.**  
Many systems fail because rules of different durations are placed at the wrong level. A temporary threshold becomes an architectural truth. A foundational identity rule becomes a local option.

---

### Volatility

**Definition.**  
Volatility is the expected rate and legitimacy of change for a mechanism, rule, requirement, policy, or representation.

**Not to be confused with.**  
Volatility is not bad. Some things should change quickly. The problem is when volatile mechanisms govern durable meanings.

**Why it matters.**  
Hexagonal architecture is valuable when it prevents volatile mechanisms from forcing durable concepts to change at their pace.

---

## Commitment and transaction terms

### Commitment

**Definition.**  
A commitment is something the system makes true, visible, relied upon, or irreversible enough that it must be answerable.

**Not to be confused with.**  
A commitment is not merely a database write. A publication, notification, trace, external call, state transition, or accepted command can also be a commitment.

**Why it matters.**  
Architectures often identify data writes but fail to identify commitments. Consequences escape through that gap.

---

### Unit of commitment

**Definition.**  
A unit of commitment names what becomes true together and what must fail, compensate, or recover together.

A well-named unit of commitment says:

- what it protects;
- what it exposes;
- what it excludes;
- how failure returns.

**Not to be confused with.**  
A unit of commitment is not identical to a database transaction. A database transaction may implement part of it, but it does not define the application commitment by itself.

**Why it matters.**  
If the system does not name what becomes irreversible together, mechanisms will decide it implicitly.

---

### Transaction

**Definition.**  
A transaction is the operation by which a set of effects becomes true together or does not become true.

In this corpus, the transaction is treated as an application concern when it names a unit of commitment, not merely as an infrastructure mechanism.

**Not to be confused with.**  
A transaction is not only a database feature. It can include outbox patterns, sagas, compensations, idempotency, retries, or escalation paths.

**Why it matters.**  
Ports say what passes. Transactions say what stays.

---

### Silent transaction

**Definition.**  
A silent transaction exists when the system commits, persists, publishes, notifies, traces, or compensates without naming what is engaged together.

**Not to be confused with.**  
A silent transaction is not the absence of transaction logic. It is transaction logic without application-level naming.

**Why it matters.**  
Silent transactions make systems difficult to correct. Something became true, but the architecture never said what kind of truth it was.

---

### Irreversibility

**Definition.**  
Irreversibility is the point at which an effect becomes part of the world the application maintains, such that later correction requires compensation, reversal, audit, or explicit recovery rather than mere cancellation.

**Not to be confused with.**  
Irreversibility is not absolute permanence. It means the effect has crossed a commitment threshold.

**Why it matters.**  
A system that cannot identify its irreversible moments cannot reliably say what it has committed to.

---

## Service and flow terms

### Application service

**Definition.**  
An application service coordinates already-constituted responsibilities in response to an application intention.

It may call the model, request capabilities through ports, coordinate a unit of commitment, publish consequences, or return results.

**Not to be confused with.**  
An application service is not a place to hide every rule the model did not carry.

**Why it matters.**  
Services are necessary. They become pathological only when they secretly become the domain.

---

### Hidden domain

**Definition.**  
A hidden domain appears when the real rules, policies, distinctions, and consequences live in a place that claims not to be the domain.

The most common example is the application service that says it orchestrates while actually deciding.

**Not to be confused with.**  
A hidden domain is not automatically bad placement. Some application rules belong in use cases. It becomes a problem when the rule's duration, variation, or correction locus belongs elsewhere.

**Why it matters.**  
Hidden domains make systems hard to reason about. The architecture says the rule lives in one place. The code makes it live in another.

---

### Shameful domain

**Definition.**  
Shameful domain is a sharper term for a hidden domain: a domain that exists, but does not acknowledge itself as domain.

It qualifies, prioritizes, validates, transforms, compensates, and chooses, while calling itself an orchestrator or service.

**Not to be confused with.**  
The term is not a moral judgment on developers. It is a diagnostic name for a structural displacement.

**Why it matters.**  
The term makes visible a common pathology: the code that carries the domain often denies that it is doing so.

---

### Flow architecture

**Definition.**  
A flow architecture is an application organized around the reception, qualification, transformation, sequencing, publication, compensation, or propagation of signals.

Examples include event consumers, pipelines, batch processes, synchronizations, integrations, propagators, and consolidation services.

**Not to be confused with.**  
A flow architecture is not necessarily domain-poor. Its domain may be a grammar of consequences rather than a set of rich entities.

**Why it matters.**  
Judging every system by the presence of rich entities misses many real enterprise domains. In flows, the core may live in qualification, idempotency, priority, rejection, publication, and recovery.

---

### Grammar of consequences

**Definition.**  
A grammar of consequences is the set of rules by which an application qualifies signals, refuses incoherence, orders priorities, preserves identity, prevents duplicate action, commits effects, and returns failures for correction.

**Not to be confused with.**  
It is not an informal process description. It is the internal structure by which a flow system decides what consequences may exist.

**Why it matters.**  
In flow systems, the domain is often not an object. It is the grammar by which signals become accepted, rejected, retried, compensated, or published.

---

### Signal

**Definition.**  
A signal is an external or internal input that may become meaningful to the application after qualification.

A signal can be an event, record, message, file, command, row, webhook, or payload.

**Not to be confused with.**  
A signal is not automatically an intention. A signal must be interpreted, qualified, and possibly refused before it becomes an application meaning.

**Why it matters.**  
Weak architectures let raw signals travel too far. Strong architectures transform signals into internal meanings early.

---

### Qualified signal

**Definition.**  
A qualified signal is a signal that has been interpreted enough to be accepted, rejected, or transformed by the application in its own terms.

**Not to be confused with.**  
A parsed payload is not necessarily a qualified signal. Parsing says the shape is readable. Qualification says the signal has an application status.

**Why it matters.**  
Many flow bugs arise because parsed data is treated as meaningful before qualification.

---

### Idempotency policy

**Definition.**  
An idempotency policy defines when repeated signals, commands, or effects are considered the same, and what the system must do when repetition occurs.

**Not to be confused with.**  
Idempotency is not merely checking whether an identifier already exists. It is a domain or flow policy about sameness, repetition, and consequence.

**Why it matters.**  
In many flow architectures, idempotency is part of the core. If left as a condition inside a service, it becomes diffuse.

---

### Compensation

**Definition.**  
Compensation is the structured action by which the system returns from a failed or partially committed consequence to a recoverable, explainable, or corrected state.

**Not to be confused with.**  
Compensation is not just rollback. Rollback cancels before commitment. Compensation responds after a commitment or partial effect has already happened.

**Why it matters.**  
Systems that cannot compensate must be especially precise about what they commit and when.

---

## Translation and integration terms

### Mapping

**Definition.**  
Mapping is the transformation of data from one representation to another.

**Not to be confused with.**  
Mapping is not always neutral. When mapping chooses identity, default values, rejected fields, fallback rules, error categories, or internal names, it becomes semantic decision.

**Why it matters.**  
Many systems hide core decisions in mappers while treating them as plumbing.

---

### Transduction

**Definition.**  
Transduction is the operation by which a signal from one world becomes a meaning in another world.

In software integration, transduction occurs when an external representation becomes an internal object, command, error, identity, policy input, or consequence.

**Not to be confused with.**  
Transduction is stronger than mapping. Mapping can be field-to-field. Transduction changes the world in which the signal has meaning.

**Why it matters.**  
The mapper is often an organ of semantic decision disguised as plumbing. Calling it transduction reveals the responsibility hidden there.

---

### Anti-corruption

**Definition.**  
Anti-corruption is the discipline of protecting an application's internal model from the categories, names, states, and assumptions of an external world.

**Not to be confused with.**  
An anti-corruption layer is not merely a mapping layer. It is an institution of translation and refusal.

**Why it matters.**  
Corruption is not only technical coupling. It is also conceptual dependency: the outside teaching the inside how to think.

---

### Ontological corruption

**Definition.**  
Ontological corruption occurs when an external mechanism, vendor, protocol, database, or upstream system imposes the objects, states, categories, identities, or temporalities through which the application understands itself.

**Not to be confused with.**  
Ontological corruption is deeper than an unwanted import or direct dependency. It can persist after dependencies have been inverted.

**Why it matters.**  
This is one reason formally clean hexagonal architectures can remain substantively weak.

---

## Error and observability terms

### Error model

**Definition.**  
An error model is the structured set of violation categories the system recognizes.

It says what kinds of failure can occur, which world was violated, where correction belongs, and what information must survive the failure.

**Not to be confused with.**  
An error model is not a logging convention or exception hierarchy alone. Those can express it, but they do not guarantee it.

**Why it matters.**  
A poor error model collapses distinct failures into generic categories, making correction harder or impossible.

---

### Generic error

**Definition.**  
A generic error is an error that fails to distinguish what kind of world, rule, mechanism, translation, or commitment was violated.

**Not to be confused with.**  
Generic errors can be acceptable at outer technical boundaries. They become dangerous when they erase distinctions needed for correction.

**Why it matters.**  
Generic errors destroy answerability by making different correction paths look the same.

---

### Discriminating error

**Definition.**  
A discriminating error names the kind of violation that occurred and implies a distinct correction path.

Examples include domain violation, source inconsistency, identity ambiguity, translation refusal, infrastructure unavailability, downstream publication failure, and commitment breach.

**Not to be confused with.**  
A discriminating error is not a verbose error. Its value is not quantity of information. Its value is correct classification.

**Why it matters.**  
The system can only correct what it can distinguish.

---

### Observability

**Definition.**  
Observability is the capacity to reconstruct and understand what happened in a running system through traces, logs, metrics, events, and diagnostic signals.

**Not to be confused with.**  
Observability is not answerability. It may reveal that something happened without revealing what was violated or where correction belongs.

**Why it matters.**  
Observability supports answerability only when it reflects the system's commitments, rules, and correction loci. Otherwise it can colonize the architecture by imposing its own categories.

---

### Monitoring drift

**Definition.**  
Monitoring drift occurs when the system becomes more intelligible through its traces than through its model.

**Not to be confused with.**  
This is not a critique of monitoring. It is a critique of monitoring becoming the implicit architecture of meaning.

**Why it matters.**  
If developers need logs to understand a rule, the model may no longer carry that rule.

---

## Testing terms

### Infrastructure-free test

**Definition.**  
An infrastructure-free test exercises application behavior without starting databases, servers, brokers, or external systems.

**Not to be confused with.**  
An infrastructure-free test is not automatically a substantive test. It may only prove that mocks were called.

**Why it matters.**  
Hexagonal architecture often makes infrastructure-free tests easier. That is useful, but not the ultimate proof that the architecture is substantive.

---

### Weak test

**Definition.**  
A weak test verifies paths, calls, mocks, or orchestration without proving that a rule, invariant, commitment, or consequence is protected.

**Not to be confused with.**  
A weak test can still be useful. The problem is treating it as proof of architectural substance.

**Why it matters.**  
A system can have fast, isolated, clean tests and still fail to prove what matters.

---

### Substantive test

**Definition.**  
A substantive test proves that the system cannot lie about what it claims to protect.

It checks that invalid states cannot exist, incoherent signals cannot produce consequences, irreversible commitments are protected, and failures return to the right correction locus.

**Not to be confused with.**  
A substantive test is not necessarily large or slow. It is substantive because of what it proves, not because of its scope.

**Why it matters.**  
The real testing benefit of hexagonal architecture is not speed alone. It is the ability to test boundaries of meaning and consequence.

---

### Test drift

**Definition.**  
Test drift occurs when tests gradually shift from protecting invariants and consequences to verifying implementation paths and mocks.

**Not to be confused with.**  
Test drift is not test decay in general. It is a loss of substantive proof while test quantity may remain high.

**Why it matters.**  
Test suites often keep growing while their protection value declines.

---

## Diagnostic terms

### Ontological test

**Definition.**  
The ontological test decides whether hexagonal architecture is appropriate for a candidate application.

It asks whether the application contains at least one rule, distinction, policy, or unit of commitment that:

1. restricts possible states or consequences independently of the current mechanism;
2. deserves to outlast today's tooling;
3. must be guaranteed by construction rather than convention;
4. can be named now.

**Not to be confused with.**  
The ontological test is not a checklist of preferences. It is a fail-capable test. If the team cannot name a candidate, hexagonal architecture is premature or inappropriate.

**Why it matters.**  
It prevents teams from adopting hexagonal architecture as a mark of seriousness when there is nothing yet to institute.

---

### Diagnostic checklist

**Definition.**  
The diagnostic checklist evaluates what an existing hexagonal architecture actually carries.

It asks questions about domain, ports, services, flows, mappers, errors, transactions, strata, conversation, tests, and correction.

**Not to be confused with.**  
It is not a compliance checklist. It does not ask whether files are in the expected folders. It asks what the structure answers for.

**Why it matters.**  
It turns the thesis into a practical review method.

---

### Drift

**Definition.**  
Drift is the gradual movement by which an initially meaningful structure loses its load-bearing function while preserving its visible form.

**Not to be confused with.**  
Drift is not ordinary change. Drift is change that weakens the relation between form and substance.

**Why it matters.**  
Most architectures do not collapse suddenly. They drift into formality.

---

### Port drift

**Definition.**  
Port drift occurs when ports stop naming application conversations and start naming technical operations.

**Concrete sign.**  
Port methods use mechanism verbs such as `save`, `fetch`, `push`, `publish`, `send`, or `move` without application meaning.

**Why it matters.**  
Port drift lets the mechanism rename the application from inside the boundary.

---

### Repository drift

**Definition.**  
Repository drift occurs when a repository or referential becomes a CRUD interface that imposes persistence ontology on the application.

**Concrete sign.**  
The port exposes operations by field, query shape, table key, or storage concern.

**Why it matters.**  
Repository drift turns persistence into the hidden model of the application.

---

### Service drift

**Definition.**  
Service drift occurs when application services progressively absorb decisions that should have been modeled elsewhere.

**Concrete sign.**  
The service grows, branches, validates, translates, compensates, and becomes the only place where certain rules are understood.

**Why it matters.**  
Service drift produces hidden domain and weakens answerability.

---

### Mapper drift

**Definition.**  
Mapper drift occurs when mapping becomes a hidden site of semantic decision.

**Concrete sign.**  
The mapper silently chooses what is preserved, lost, renamed, defaulted, rejected, or treated as identity.

**Why it matters.**  
Mapper drift is one of the main ways a core becomes diffuse.

---

### DTO drift

**Definition.**  
DTO drift occurs when transport shapes colonize internal types and become implicit policy.

**Concrete sign.**  
Internal objects increasingly resemble API DTOs, source records, message payloads, or database projections.

**Why it matters.**  
DTO drift makes the outside's representation become the inside's ontology.

---

### Error drift

**Definition.**  
Error drift occurs when distinct violations collapse into generic or poorly classified errors.

**Concrete sign.**  
Many failures are represented by undifferentiated errors, strings, or generic exception types.

**Why it matters.**  
Error drift erases correction paths.

---

### Transaction drift

**Definition.**  
Transaction drift occurs when units of commitment disappear into infrastructure mechanisms or implicit service order.

**Concrete sign.**  
Commits live in adapters, multiple commits happen per use case, or downstream effects are mixed with persistence without named commitment boundaries.

**Why it matters.**  
Transaction drift makes irreversibility invisible.

---

### Conversation drift

**Definition.**  
Conversation drift occurs when the boundary remains visible in code but is no longer defended in the team's conversations with the organization.

**Concrete sign.**  
Requirements arrive in external vocabulary and are accepted without being reformulated in the application's grammar.

**Why it matters.**  
A boundary not recognized in speech eventually becomes fictive in code.

---

### Domain package drift

**Definition.**  
Domain package drift occurs when the domain folder becomes a bag of legitimacy for code that should appear clean but carries no invariants.

**Concrete sign.**  
The folder contains types, services, constants, interfaces, and utility classes with domain names but no domain force.

**Why it matters.**  
The folder starts to certify seriousness instead of carrying substance.

---

### Pipeline drift

**Definition.**  
Pipeline drift occurs when a sequence continues to operate while the action it was supposed to carry is no longer understood.

**Concrete sign.**  
No one can answer: why this step, in this order?

**Why it matters.**  
A pipeline can keep running after its meaning has vanished.

---

## Organizational terms

### Boundary as conversation

**Definition.**  
Boundary as conversation names the organizational dimension of the hexagonal boundary: the team must be able to defend the terms in which the application can be addressed and the terms in which it asks things of the world.

**Not to be confused with.**  
This is not stakeholder management in general. It is the organizational counterpart of ports as legitimate conversations.

**Why it matters.**  
If the organization can bypass the boundary in speech, it will eventually bypass it in code.

---

### Fictive boundary

**Definition.**  
A fictive boundary is a boundary that exists in code structure but not in the actual decision and conversation practices around the system.

**Not to be confused with.**  
A fictive boundary can look technically correct. Its problem is that the organization does not recognize or respect the distinction it claims.

**Why it matters.**  
Software boundaries can be dissolved by organizational behavior even when imports remain clean.

---

### Team answerability

**Definition.**  
Team answerability is the team's practical ability to explain, defend, and correct the consequences its system produces.

**Not to be confused with.**  
Team answerability is not the same as structural answerability. A team may be capable and committed while the system gives consequences no structural return place.

**Why it matters.**  
Good teams can compensate for poor structure for a time. The corpus asks whether the structure itself helps them answer.

---

## Architectural comparison terms

### Simple layers

**Definition.**  
Simple layers organize code by technical responsibility, such as presentation, application, domain, persistence, or infrastructure.

**Why it matters.**  
Simple layers may be the right choice for CRUD, prototypes, or systems without durable core commitments. Refusing hexagonal architecture in such cases is precision, not regression.

---

### Clean Architecture

**Definition.**  
Clean Architecture is an architectural style that separates enterprise rules, application rules, interface adapters, and frameworks by dependency direction.

**In this corpus.**  
The issue is not whether rules may live in use cases. They may. The issue is whether each rule lives at the level matching its duration, variation, and correction locus.

---

### Onion Architecture

**Definition.**  
Onion Architecture is a radial architectural style that places the domain model at the center and dependencies toward the outside.

**In this corpus.**  
It is useful when entity invariants are rich, but it does not by itself solve the problem of application commitments, flow grammars, or ontological corruption.

---

### Vertical slice architecture

**Definition.**  
Vertical slice architecture organizes code by feature or capability rather than by horizontal technical layers.

**In this corpus.**  
It is useful when features evolve independently and share few invariants. It weakens when cross-feature invariants or shared commitments become central.

---

### Event sourcing

**Definition.**  
Event sourcing stores state as a sequence of events rather than as a current-state snapshot.

**In this corpus.**  
Event sourcing can make commitments and history more explicit, but it does not automatically solve units of commitment, correction loci, or semantic validity.

---

### CQRS

**Definition.**  
CQRS separates command-side concerns from query-side concerns.

**In this corpus.**  
CQRS is often more appropriate than hexagonal architecture for heavy read sides whose principal work is representation rather than world-maintenance.

---

### Functional core

**Definition.**  
A functional core carries domain force through pure functions, rich types, exhaustive cases, and explicit state transitions.

**In this corpus.**  
A functional core can institute substance without a formal hexagonal boundary. Hexagonal architecture is not the only form of institution.

---

## Writing and evaluation terms

### Formal success

**Definition.**  
Formal success occurs when a system satisfies visible rules of structure, process, or compliance without producing the substantive benefit those rules were meant to support.

**Not to be confused with.**  
Formal success is not fake success. It is real success according to the wrong or incomplete criteria.

**Why it matters.**  
Hexagonal architecture can succeed formally and fail substantively.

---

### Substantive success

**Definition.**  
Substantive success occurs when a structure produces the benefit for which its form was adopted.

For hexagonal architecture, this means the boundary actually localizes duration, commitment, consequence, and correction.

**Not to be confused with.**  
Substantive success may include formal correctness, but it is not reducible to it.

**Why it matters.**  
The corpus judges architecture by substantive success, not by recognizable ceremony.

---

### Structural operation

**Definition.**  
A structural operation is what an architectural form actually does to the system: what it separates, localizes, protects, hides, exposes, commits, or makes correctable.

**Not to be confused with.**  
A structural operation is not the same as a structural shape. The same shape can perform different operations depending on what it carries.

**Why it matters.**  
Hexagonal architecture should be judged by its operation, not by its iconography.

---

### Iconography

**Definition.**  
Iconography is the visible representation of an architecture: diagrams, folders, arrows, dependency directions, and names.

**Not to be confused with.**  
Iconography can help understanding, but it is not the architecture's substance.

**Why it matters.**  
Many misunderstandings of hexagonal architecture come from mistaking the diagram for the operation.

---

## Canonical short formulations

Use these formulations consistently across the corpus.

- **Answerability:** consequences have a place to return.
- **Boundary:** the frontier that prevents mechanisms from naming the application's world.
- **Core:** what must remain true when mechanisms change.
- **Substantive model:** a model judged by what it makes impossible.
- **Port:** a legitimate application conversation, not merely an interface.
- **Adapter:** a translation between application conversation and mechanism.
- **Unit of commitment:** what becomes true together.
- **Silent transaction:** a commitment boundary that exists but is not named.
- **Diffuse core:** domain intelligence without a responsible locus.
- **Substantive test:** a test that proves an invariant, commitment, or correction path.
- **Drift:** the preservation of form while substance erodes.


