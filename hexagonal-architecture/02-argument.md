# The Argument

*Level 2. Fifteen to twenty minutes. The reasoning that supports the claim.*

Level 1 stated the thesis: hexagonal architecture is true when its boundary localizes duration, commitment, and correction. This level gives the reasoning.

The argument unfolds in eight steps:

1. the phenomenon to be explained;
2. the boundary as institution rather than protection only;
3. duration as the first consequence of institution;
4. the three failure modes of the core;
5. the port as conversation;
6. the transaction as the name of irreversibility;
7. the service as either orchestration or hidden domain;
8. the flow case, where the domain may be a grammar of consequences rather than a classical entity model.

## 1. The fact to be explained

A regular phenomenon should interrupt doctrinal certainty.

Many applications respect the hexagonal form without obtaining the announced benefit. Dependencies point inward. Adapters are isolated. Ports are declared. Tests run without databases or servers. The `domain` folder sits at the center.

And yet the business logic remains dispersed. Changes remain expensive. Newcomers follow flows without understanding the model. Important decisions live in places the architecture does not recognize as load-bearing.

This cannot be reduced to incompetence. The phenomenon appears in serious teams, disciplined teams, often able to pass strict automated checks.

The structure is compliant. The function is missing.

An architecture can therefore succeed formally and fail substantively.

The conventional reading does not explain this. If the hexagonal boundary were only a wrapper protecting an already-constituted business core, then respecting the wrapper should produce the protective benefit. It often does not.

The decisive question is therefore not:

> Is the boundary drawn?

It is:

> What does this boundary make exist when it is drawn?

## 2. The boundary institutes

The hexagonal boundary does not first protect a pre-existing core. It institutes one.

It writes a demand into the code: something must be capable of existing in the application's own terms, without borrowing its vocabulary from the framework, the protocol, the database, the SDK, or the third-party system.

This something is not always already visible. It can be latent. It can live in practices, tacit arbitrations, rules known only to a few developers, the order of a flow, a mapper, a generic error, an option passed to a service, or a name inherited from the source system.

The boundary does not always enclose an object already there. It calls an object to constitute itself.

When the application contains a substance capable of responding, the boundary forces it into articulation. Refusing a technical dependency reveals a rule that was leaking. Requiring a port that does not name the tool surfaces an applicative conversation. Writing a test without infrastructure compels the formulation of what must remain true regardless of mechanism.

The boundary institutes a core.

When nothing responds, the boundary institutes a void. The expected forms appear: ports, adapters, services, folders, mocks, isolated tests. But no durable content inhabits them. The domain folder contains poor types. The ports paraphrase technical operations. The services move data. The architecture looks correct because the skeleton is present, but it remains suspended around an absent object.

The boundary therefore does not guarantee the core. It tests whether a core can be instituted.

## 3. If the boundary institutes, it institutes duration

If the boundary institutes, it must decide what has the right to endure.

A boundary is not only spatial. It is temporal. It separates not only inside from outside, but durable from volatile, commitments from mechanisms, and slow concepts from fast tools.

Without such a boundary, an application inherits the fastest temporality it contains. An SDK changes, a protocol evolves, an upstream format shifts, and the internal concepts begin to change at the pace of tooling. Nothing has the right to be slow.

Rules that should outlast ten years of infrastructure become hostage to mechanisms that change in six months.

But the slow / fast distinction is still too coarse. A serious application contains strata of duration.

- **Foundational inscriptions**: identity rules, accounting invariants, regulatory constraints, irreversible states.
- **Policy inscriptions**: eligibility rules, taxonomies, procedures, governance conventions.
- **Functional inscriptions**: use cases, journeys, business variations, campaign rules.
- **Parametric inscriptions**: thresholds, certificates, quotas, feature flags, library versions.

The pathology is not that these strata coexist. They must.

The pathology is no longer knowing which stratum a given inscription belongs to.

A decade-long rule treated as a parameter weakens the foundations. An operational threshold placed inside a value object of the core turns a temporary decision into an architectural truth. A multi-year policy dispersed across local conditions becomes invisible as policy.

The business / technical question is therefore secondary. A rule that looks technical may belong to the core if it outlasts the tooling and structures domain consequences. A rule that looks business may remain peripheral if it is only a campaign contingency, a temporary compromise, or an artifact of a third-party system in transition.

What decides is duration, legitimate variation, and locus of correction.

## 4. Three ways the operation can fail

Once the boundary is drawn, three failures are possible. Confusing them produces wrong remedies.

### 4.1 The empty core

The empty core appears when the application has no real candidate for institution. It receives, transforms, validates superficially, persists, transmits. It is principally a passage.

This is not a fault. Many applications are gateways, synchronizers, pipelines, admin screens, temporary integrations. Their error would not be to be simple. Their error would be to claim a substantial core when they coordinate external mechanisms.

In this case, hexagonal architecture often adds vocabulary more expensive than the object it claims to protect. A simple, modular, typed, testable architecture is more honest.

Refusing hexagonal here is not regression. It is refusing to institute a void.

### 4.2 The mimed core

The mimed core appears when the team produces the signs of the domain without producing its force.

The names are right. The folders are clean. The entities exist. But nothing important is rendered impossible. Rules decorate execution paths instead of governing concepts.

A public constructor bypasses a factory. A mutable field contradicts an invariant. A method checks one case but lets other paths produce the forbidden state.

The mimed core resembles the domain. It speaks like the domain. It does not respond like the domain, because it does not carry consequences.

A minimal example:

```ts
class Account {
  constructor(
    public id: string,
    public holder: string,
    public balance: number,
  ) {}

  static open(holder: string, initialDeposit: number): Account {
    if (initialDeposit < 100) {
      throw new Error('minimum deposit not reached');
    }

    return new Account(crypto.randomUUID(), holder, initialDeposit);
  }
}
```

The rule exists, but only on one path. `new Account('a1', 'Ada', -5000)` remains possible. `account.balance = -1000` remains possible. The model names the domain, but it does not govern it.

A substantive model is different:

```ts
class Account {
  private constructor(
    readonly id: AccountId,
    readonly holder: Holder,
    readonly balance: Money,
  ) {}

  static open(holder: Holder, initialDeposit: Money): Account {
    if (initialDeposit.isLessThan(MINIMUM_DEPOSIT)) {
      throw new MinimumDepositNotReached(initialDeposit, MINIMUM_DEPOSIT);
    }

    return new Account(AccountId.new(), holder, initialDeposit);
  }
}
```

Here the rule is not a decoration. It is a condition of existence. The forbidden state has no public construction path. The model carries consequence.

### 4.3 The diffuse core

The diffuse core is graver.

Here, the domain is not absent. It operates. But it has no responsible locus. It lives in conditions, mappers, service order, call options, observability conventions, generic errors, inherited field names, and developer memory.

The system possesses real intelligence, but this intelligence is localized nowhere as responsibility.

The mimed is often corrected by moving a visible rule to the right level. The diffuse demands more: it requires naming what was never recognized as a decision.

The diffuse core is more dangerous than the empty core. In emptiness, absence eventually becomes visible. In diffusion, intelligence continues to operate, but no one answers for it.

The most common danger is therefore not the absence of a domain. It is the exile of the domain into the details.

## 5. If the boundary institutes a core, a port cannot be only an interface

The most frequent confusion in modern hexagonal implementations is to believe that a port is an interface.

An interface describes a possible call.

A port describes a conversation that the application recognizes as legitimate with its environment.

A weak port names a technical primitive:

```ts
interface CustomerRepository {
  save(customer: Customer): Promise<void>;
  findById(id: string): Promise<Customer | null>;
}
```

This may be a useful interface. It is not necessarily a strong port. Its vocabulary is borrowed from persistence. If the mechanism changes from a database to an event stream or an external source of truth, the name may collapse.

A stronger port names what the application asks of the world:

```ts
interface CustomerIdentityRegistry {
  registerIdentity(decision: ValidatedCustomerIdentity): Promise<void>;
  resolveByExternalIdentity(identity: ExternalCustomerIdentity): Promise<CustomerIdentity | undefined>;
}
```

This still may be implemented by SQL, events, cache, files, or a remote API. But the port itself does not speak their language. It speaks in applicative terms.

When a port carries the name of the mechanism, the outside has already named the inside. The dependency may be inverted in the imports; the conceptual dependency remains.

This colonization does not appear in a dependency graph. It appears in vocabulary.

The test is austere:

> If the mechanism changes, does the name of the port remain true?

If the name collapses with the technology, it was not yet a port. It was an interface placed at the right location.

### Primary and secondary ports

Primary and secondary ports are not symmetric.

A **primary port** poses a question of interpellation:

> Who has the right to address the application, and in what terms?

Its discipline consists of transforming external solicitations into internal intentions.

A **secondary port** poses a question of requirement:

> What does the application ask of the world, and in what terms?

Its discipline consists of naming a needed capability without formulating it in the language of the mechanism that currently realizes it.

The boundary is a circle, but its passages do not bear the same charge. Treating them as two oriented families of interfaces weakens the frontier on at least one side.

## 6. If ports name conversations, transactions must name commitments

Ports say what passes.

The transaction says what becomes irreversible.

An architecture can have strong ports and remain hollow if it does not know how to name its units of commitment.

A transaction is not merely an atomicity mechanism. It is the operation by which a set of effects becomes true together, or does not become true. It says what enters the world the application maintains in a single commitment.

The common pathology is not the absence of transactions. It is the silent transaction.

The system commits, publishes, persists, notifies, traces, sometimes multiple times in cascade, without the code ever saying: here is what is engaged together; here is what remains outside the engagement; here is how failure returns.

A weak arrangement hides the commitment inside a mechanism:

```ts
class SqlCustomerRegistry implements CustomerIdentityRegistry {
  async registerIdentity(decision: ValidatedCustomerIdentity): Promise<void> {
    await this.db.transaction(async tx => {
      await tx.insert('customers', decision.customer);
      await tx.insert('identity_history', decision.trace);
      await this.bus.publish('CustomerIdentityRegistered', decision); // not part of the database commit
    });
  }
}
```

The code has an atomic block, but the application has not named what becomes true together. The database transaction and the downstream publication do not share the same guarantee.

A better design names the unit of commitment before deciding the mechanism:

```ts
type CustomerIdentityCommitment = {
  customer: Customer;
  trace: IdentityTrace;
  downstreamConsequence: CustomerIdentityRegistered;
};
```

The mechanism may still be a database transaction plus an outbox. But the application has stated what is engaged together and what must be made recoverable if the technical path is split.

A well-named unit of commitment says four things:

1. what it protects;
2. what it exposes;
3. what it excludes;
4. how failure returns.

Without this naming, the architecture can isolate technology while letting mechanisms decide what becomes true.

## 7. If commitments exist, services cannot absorb every responsibility

The application service is not suspect by nature.

It is necessary when it coordinates already-constituted responsibilities: calling a model, registering a decision, publishing a consequence, triggering a policy, orchestrating a transaction.

It becomes pathological when it absorbs everything the team did not manage to model.

It qualifies, interprets, prioritizes, validates, transforms, compensates, chooses, notifies, translates. It claims to orchestrate, but it decides. It becomes the real domain under a name that asserts it is only a coordinator.

This is the shameful domain: a domain that exists but does not acknowledge itself as a domain.

This situation also misleads superficial readings of SOLID. One can always declare that a service has a single responsibility if one names that responsibility at a sufficiently vague level: handle a record, manage a customer, execute a workflow.

But a responsibility too broad is not a responsibility. It is an administrative region of the code.

The real test is the number of substantial reasons for change it absorbs.

A healthy service orchestrates already-constituted responsibilities.

A pathological service constitutes in secret the responsibilities it claims merely to coordinate.

## 8. The flow case: when the domain is a grammar of consequences

The argument must not remain trapped in an entity-centered imagination.

Many enterprise applications are flow architectures: event consumers, pipelines, batch processes, synchronizations, propagations, consolidations, integrations.

In these systems, the core is not always a rich object model. It may be a policy of interpretation over signals.

The central questions become different:

- which signal counts;
- how it is qualified;
- which inconsistency must be rejected;
- which priority must be enforced;
- which identity must be preserved;
- which consequence is irreversible;
- which publication is allowed;
- which recovery is legitimate;
- which idempotency is required.

These questions form a grammar of consequences.

A flow without such grammar is only a sequence. A flow with such grammar has a core, even if that core does not look like a classical entity model.

The error is to say, too quickly, that an orchestrator has no domain. Some orchestrators are empty. Others carry identity, priority, idempotency, compensation, publication, and refusal rules.

In a flow architecture, the domain may be the way an application turns an external signal into an internal decision and a controlled consequence.

## Conclusion

The argument is now in place.

The boundary institutes rather than merely protects. If it institutes, it must decide duration. If it decides duration, it can fail by emptiness, mimicry, or diffusion. If it institutes a core, ports cannot be mere interfaces. If ports name conversations, transactions must name commitments. If commitments exist, services cannot secretly absorb responsibility. If the system is a flow, its domain may be a grammar of consequences rather than an entity model.

The claim of level 1 is no longer an assertion. It is the conclusion of a reasoning.

Whether that reasoning survives counter-examples and alternative readings is the question of [`defense.md`](./defense.md).

Whether it translates into operational practice is the question of [`application.md`](./application.md).

You have the argument. That is what level 2 promised.
