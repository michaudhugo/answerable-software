# The Argument

*Level 2. Fifteen minutes. The reasoning that supports the claim.*

Level 1 stated the thesis: hexagonal architecture is true when its boundary localizes duration, commitment, and correction. This level gives the reasoning.

The argument unfolds in seven steps. First, the phenomenon to be explained. Second, the displacement: the boundary institutes rather than merely protects. Third, the consequence of that displacement: the boundary is a decision about duration. Fourth, the three ways the operation can fail. Fifth, the port as conversation. Sixth, the transaction as the name of irreversibility. Seventh, the service as either orchestration or hidden domain.

## 1. The fact to be explained

A regular phenomenon should interrupt doctrinal certainty.

Many applications respect the hexagonal form without obtaining the announced benefit. Dependencies point inward. Adapters are isolated. Ports are declared. Tests run without databases or servers. The `domain` folder sits at the center.

And yet the business logic remains dispersed. Changes remain expensive. Newcomers follow flows without understanding the model. Important decisions live in places the architecture does not recognize as load-bearing.

This cannot be reduced to incompetence. The phenomenon appears in serious teams, disciplined teams, often able to pass strict automated checks. The structure is compliant. The function is missing.

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

## 3. The boundary is a decision about duration

If the boundary institutes, it must decide what has the right to endure.

A boundary is not only spatial. It is temporal. It separates not only inside from outside, but slower from faster, durable from volatile, commitments from mechanisms.

Without such a boundary, an application inherits the fastest temporality it contains. An SDK changes, a protocol evolves, an upstream format shifts, and the internal concepts begin to change at the pace of tooling. Nothing has the right to be slow.

Rules that should outlast ten years of infrastructure become hostage to mechanisms that change in six months.

But the slow / fast distinction is still too coarse. A serious application contains strata of duration.

- **Foundational inscriptions**: identity, accounting invariants, regulatory obligations, irreversible states.
- **Policy inscriptions**: procedures, taxonomies, eligibility rules, governance conventions.
- **Functional inscriptions**: use cases, journeys, campaign rules, product options.
- **Parametric inscriptions**: thresholds, certificates, quotas, feature flags, versions.

The pathology is not that these strata coexist. They must. The pathology is no longer knowing which stratum a given inscription belongs to.

A decade-long rule treated as a parameter weakens the foundations. An operational threshold placed inside a core value object turns a temporary decision into an architectural truth. A multi-year policy dispersed across local conditions becomes invisible as policy.

The business / technical distinction is secondary. A rule that looks technical may belong to the core if it outlasts the tooling and structures the consequences of the domain. A rule that looks business may remain peripheral if it is a campaign contingency, a temporary compromise, or a residue of a third-party system.

What decides is not the label. What decides is duration, legitimate variation, and the cost of violation.

## 4. Three failures of institution

If the boundary calls a core into existence, three failures become possible.

### The empty core

The empty core appears when the application has no real candidate for institution. It receives, transforms, validates superficially, persists, transmits. It is principally a passage.

This is not a fault. Many applications are gateways, synchronizers, pipelines, admin screens, or temporary integrations. Their error is not simplicity. Their error would be to claim a substantial core when they only coordinate external mechanisms.

In this case, hexagonal architecture often adds vocabulary more expensive than the object it claims to protect. A simple, modular, typed, testable architecture is more honest.

Refusing hexagonal here is not regression. It is refusing to institute a void.

### The mimed core

The mimed core appears when the team produces the signs of a domain without producing its force. The names are right. The folders are clean. Entities exist. But nothing important is rendered impossible.

Rules decorate execution paths instead of governing concepts. A public constructor bypasses a factory. A mutable field contradicts an invariant. A method checks one case but lets another path produce the forbidden state.

The mimed core resembles the domain. It speaks like the domain. But it does not answer like the domain, because it does not carry consequences.

A mimed model can be difficult to spot because it looks close to the desired form:

```ts
class Account {
  constructor(
    public id: string,
    public ownerId: string,
    public balance: number,
  ) {}

  static open(ownerId: string, initialDeposit: number): Account {
    if (initialDeposit < 100) {
      throw new Error("minimum deposit not reached");
    }

    return new Account(crypto.randomUUID(), ownerId, initialDeposit);
  }
}

const account = new Account("account-1", "owner-1", -500);
account.balance = -1000;
```

The problem is not that the class has too few methods. The problem is that the forbidden state remains constructible. The rule decorates one creation path; it does not govern the concept.

A substantive model does not merely check a preferred path. It removes the illegitimate path:

```ts
type AccountId = string;
type OwnerId = string;

class Money {
  private constructor(private readonly cents: number) {}

  static ofCents(cents: number): Money {
    if (!Number.isInteger(cents)) {
      throw new Error("money must use integer cents");
    }
    return new Money(cents);
  }

  isLessThan(other: Money): boolean {
    return this.cents < other.cents;
  }
}

const minimumDeposit = Money.ofCents(10_000);

class Account {
  private constructor(
    readonly id: AccountId,
    readonly ownerId: OwnerId,
    readonly balance: Money,
  ) {}

  static open(ownerId: OwnerId, initialDeposit: Money): Account {
    if (initialDeposit.isLessThan(minimumDeposit)) {
      throw new MinimumDepositNotReached(initialDeposit, minimumDeposit);
    }

    return new Account(crypto.randomUUID(), ownerId, initialDeposit);
  }
}
```

This code is load-bearing because the invariant is not a convention. It is part of the conditions under which the object can exist.

### The diffuse core

The diffuse core is more grave. Here, the domain is not absent. It operates. But it has no responsible locus.

It lives in conditions, mappers, service ordering, call options, observability conventions, generic errors, names inherited from source systems, and developer memory. The system possesses real intelligence, but this intelligence is localized nowhere as responsibility.

The mimed core can often be corrected by moving a visible rule to the right level. The diffuse core demands more: it requires naming what had never been recognized as a decision.

The diffuse core is more dangerous than the empty core. In emptiness, absence eventually becomes visible. In diffusion, intelligence continues to operate, but no one answers for it.

The most common danger is therefore not the absence of domain. It is the exile of the domain into the details.

## 5. The port is a conversation, not an interface

If the boundary institutes, its ports cannot be mere interfaces.

An interface describes a possible call. A port describes a conversation the application recognizes as legitimate with its environment.

A weak port names a technical primitive: save, fetch, push, publish, move, send. It abstracts a technology, but it lets the technology impose its grammar.

A strong port names an applicative capability: resolve an identity, register an irreversible decision, make a consolidation available, isolate an incoherent signal, publish a validated consequence. It does not say what the infrastructure does. It says what the application asks of the world, or what it accepts to make available to it.

When a port carries the name of the mechanism, the outside has already named the inside. The dependency may be inverted in the imports; the conceptual dependency remains. The application no longer technically depends on the external system, but it continues to think with its words.

This colonization does not appear in a dependency graph. It appears in vocabulary.

The test is austere:

> If the mechanism changes, does the name of the port remain true?

If the name collapses with the technology, it was not yet a port. It was an interface placed at the right location.

The distinction is visible in names before it is visible in mechanics:

```ts
interface AccountRepository {
  save(account: Account): Promise<void>;
  findById(id: string): Promise<Account | undefined>;
}
```

This may be useful infrastructure abstraction, but it is still named by a persistence grammar. If persistence becomes event publication or a remote source of truth, the name begins to lie.

A stronger secondary port names what the application requires:

```ts
interface AccountReference {
  registerOpening(opening: AccountOpening): Promise<void>;
  resolveByIdentity(id: AccountId): Promise<Account | undefined>;
}
```

The implementation can be relational persistence, an event store, an outbox, a remote service, or a cache backed by another source. The port remains true because it names the applicative conversation, not the mechanism currently used to realize it.

Primary and secondary ports are not symmetric.

A primary port asks: who has the right to address the application, and in what terms? Its discipline is to transform external solicitations into internal intentions.

A secondary port asks: what does the application require from the world, and in what terms? Its discipline is to name a needed capability without formulating it in the language of the mechanism that currently realizes it.

The boundary is a circle, but its passages do not bear the same charge.

## 6. The transaction names what becomes irreversible together

If ports name conversations, transactions name commitments.

Ports say what passes. The transaction says what becomes irreversible. An architecture can have strong ports and remain hollow if it does not know how to name its units of commitment.

A transaction is not merely an atomicity mechanism. It is the operation by which a set of effects becomes true together, or does not become true. It says what enters the world the application maintains in a single moment of commitment.

The common pathology is not the absence of transactions. It is the silent transaction.

The system commits, publishes, persists, notifies, traces, sometimes multiple times in cascade, without the code ever saying: here is what is engaged together; here is what remains outside the engagement; here is how failure returns.

A well-named unit of commitment says four things:

1. what it protects;
2. what it exposes;
3. what it excludes;
4. how it returns on failure.

Without this naming, the architecture can isolate the technology while letting the mechanism decide what becomes true.

This is why strong ports are not enough. The ports declare what the application accepts and requires. The transactions declare what the application commits to. Both are required for the boundary to institute a real locus of answerability.

A silent transaction often appears when the adapter commits several effects while the application never names the engagement:

```ts
class PostgresAccountReference implements AccountReference {
  async registerOpening(opening: AccountOpening): Promise<void> {
    await this.db.transaction(async tx => {
      await tx.insert("accounts", opening.account);
      await tx.insert("account_history", opening.historyEntry);
      await this.bus.publish("account.opened", opening.event);
    });
  }
}
```

The application asked to register an opening, but the adapter silently decided what became true together. The bus publication may not participate in the database transaction. The commitment exists, but it is unnamed.

A stronger design makes the unit of commitment explicit before it reaches the mechanism:

```ts
class AccountOpeningCommitment {
  constructor(
    readonly account: Account,
    readonly historyEntry: AccountHistoryEntry,
    readonly downstreamConsequence: AccountOpened,
  ) {}
}

interface AccountCommitments {
  commitOpening(commitment: AccountOpeningCommitment): Promise<void>;
}
```

The adapter may still use a database transaction, an outbox, a message broker, or another mechanism. The important difference is that the application has named what must be engaged together and what the adapter must preserve.

## 7. The service can hide the domain

If commitments exist, the service must not absorb them silently.

The application service is not suspect by nature. It is necessary when it coordinates already-constituted responsibilities: calling a model, registering a decision, publishing a consequence, triggering a policy, orchestrating a transaction.

It becomes pathological when it absorbs everything the team did not manage to model. It qualifies, interprets, prioritizes, validates, transforms, compensates, chooses, notifies, translates. It claims to orchestrate, but it decides.

It becomes the real domain under a name that asserts it is only a coordinator.

This is the hidden domain: a domain that exists but does not acknowledge itself as a domain.

The situation also misleads superficial readings of SOLID. One can always say that a service has a single responsibility if one names that responsibility at a sufficiently vague level: handle a record, manage a customer, execute a workflow. But a responsibility too broad is not a responsibility. It is an administrative region of the code.

The real test is the number of substantial reasons for change the service absorbs.

A healthy service orchestrates already-constituted responsibilities. A pathological service constitutes in secret the responsibilities it claims merely to coordinate.

## Conclusion of the argument

The reasoning is now in place.

The boundary institutes rather than merely protects. If it institutes, it decides what may endure. If it decides what may endure, it can fail by emptiness, imitation, or diffusion. If it is to avoid these failures, its ports must name conversations, its transactions must name commitments, and its services must not hide the domain they pretend only to coordinate.

The claim of level 1 is no longer an assertion. It is the conclusion of a reasoning.

Whether that reasoning survives counter-examples and alternative readings is the task of [`defense.md`](./defense.md).

Whether it can become operational practice is the task of [`application.md`](./application.md).

You have the argument. That is what level 2 promised.
