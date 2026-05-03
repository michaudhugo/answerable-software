# The Application

*Level 4. Operational tools derived from the thesis.*

The previous levels stated, argued, and defended the thesis.

This level turns it into working practice.

The goal is not to create another architecture checklist. The goal is to make architectural judgment harder to fake.

A real test is one you can fail.

## What this level provides

Use the tools in this order:

1. **The ontological test**: decide whether hexagonal architecture is appropriate before adopting it.
2. **The evidence protocol**: force every architectural claim to point to code.
3. **The diagnostic grid**: diagnose what an existing hexagonal architecture actually carries.
4. **The code probes**: inspect the most common places where formal hexagonal hides substantive failure.
5. **The drift typology**: name the erosion of an initially substantive architecture over time.
6. **The correction order**: decide what to fix first.
7. **The decision record**: capture the architectural judgment in writing.

The tools are deliberately narrow. They do not decide whether the business model is right, whether the product should exist, or whether the organization is healthy. They decide whether a claimed hexagonal structure actually carries what it claims to carry.

## I. The ontological test

*Use this before adopting hexagonal architecture.*

The test is not a checklist. It is one statement to hold.

> There exists, in this application, at least one rule, distinction, policy, or unit of commitment that:
>
> 1. restricts possible states or consequences independently of the current technical mechanism;
> 2. deserves to outlast the tooling that implements it today;
> 3. must be guaranteed by construction rather than by convention;
> 4. can be named now.

All four predicates are required.

If one predicate fails, the test fails.

### Predicate 1. Restriction

If nothing restricts possible states or consequences, the boundary has nothing to carry. It may organize code. It does not institute a core.

A candidate that only says *we want clean code* fails. Cleanliness is not a restriction.

A candidate that says *no payment without a verified identity can be published downstream* may pass. It restricts possible consequences.

### Predicate 2. Duration

If the candidate does not deserve to outlast current tooling, the boundary protects something that will change with the rest.

A temporary vendor workaround usually fails.

An identity rule, regulatory constraint, commitment rule, or irreversible publication rule may pass.

### Predicate 3. Construction

If convention is enough, the full discipline of hexagonal architecture may be disproportionate.

A rule deserves structural weight when violation would be too costly to leave to memory, review discipline, comments, or team habit.

### Predicate 4. Nameability

If the team cannot name the candidate now, the boundary rests on an abstract hope.

*We need flexibility* fails.

*No event with an unresolvable identity may produce an accepted internal command* may pass.

The test rejects architectural insurance purchased against an unnamed future.

### How to run the test

Do not run the test as a survey. Run it as a working session.

Required participants:

- the tech lead or architect who will defend the structure;
- at least one developer who will maintain the code;
- someone who understands the business or operational consequence;
- someone who knows the current technical mechanisms.

Timebox: one hour.

Output: one sentence.

The sentence must name one candidate and must not mention any current framework, database, queue, vendor, protocol, SDK, cloud service, or file format.

Good candidate forms:

```text
No [state] can exist unless [condition] is satisfied.
No [signal] can become [internal meaning] unless [qualification] succeeds.
Every [commitment] must include [effects] or return through [correction path].
A [decision] can be made only after [prior condition] has become true.
```

Examples that pass:

```text
No account can exist with an opening deposit below the minimum.
No payment event with an unresolvable identity can publish a downstream consequence.
Every regulatory disclosure must be acknowledged before customer state mutates.
The priority order among incoming claims cannot be inverted by any adapter.
```

Examples that fail:

```text
We want clean architecture.
We need flexibility for future integrations.
We follow coding standards.
Our domain is complex.
The data must be saved in PostgreSQL.
We want to be able to test without infrastructure.
```

If the team cannot name one candidate in one sentence without mentioning tooling, stop.

Do not adopt hexagonal architecture yet.

Choose a simpler architecture, or do the modeling work first.

### Flow systems

The test applies to flow architectures without modification.

The candidate does not need to be an entity rule. It can be:

- an idempotency policy;
- a priority rule;
- a compensation rule;
- a signal qualification rule;
- an identity preservation rule;
- a publication contract;
- a rejection rule;
- a traceability commitment.

The test does not ask whether the domain looks like a classical object model. It asks whether the application carries a durable constraint that deserves to be made explicit and non-contournable.

## II. The evidence protocol

*Use this before trusting any answer in an architecture discussion.*

Every architectural claim must point to evidence.

The protocol is simple:

> No claim without a place.

If someone says *the model protects this invariant*, ask where.

If someone says *the port isolates the mechanism*, ask where.

If someone says *the service only orchestrates*, ask where.

If someone says *the transaction is safe*, ask where.

If someone says *the error is handled*, ask where.

If the answer cannot point to code, a test, a type, a policy, a transaction boundary, or a documented decision, it is not yet an architectural answer. It is an intention.

Intentions are allowed. They are not evidence.

### Evidence types

| Claim | Acceptable evidence |
| --- | --- |
| The model is substantive | A constructor, type, factory, state machine, or value object that prevents an invalid state |
| The port is applicative | A name and signature that survive replacement of the mechanism |
| The adapter translates | A boundary where external vocabulary is converted into internal meaning |
| The service orchestrates | Responsibilities already constituted outside the service |
| The transaction is named | A visible unit of commitment and recovery strategy |
| The error is meaningful | Typed errors that distinguish violated worlds and correction loci |
| The test is substantive | A test proving impossibility, rejection, commitment, or correction |
| The boundary is organizationally real | Conversations and decisions that respect the declared grammar |

The protocol should feel uncomfortable. That is its function.

## III. Diagnostic grid for an existing hexagonal architecture

*Use this on a project that already claims hexagonal architecture.*

The question is not:

> Is the form correct?

The question is:

> What does this architecture actually answer for?

Run the grid with the code open. Every answer must point to a specific location.

| Angle | Decisive question | Evidence required | Failure sign |
| --- | --- | --- | --- |
| **Domain** | What does the model render impossible? | Constructor, type, value object, factory, state machine | Domain names with no impossible states |
| **Primary ports** | Do external requests become typed intentions? | Command type, input translator, validation boundary | External payloads pass through unchanged |
| **Secondary ports** | Do ports name conversations or mechanisms? | Port names and signatures | `save`, `fetch`, `push`, `move`, `publish` as mechanism verbs |
| **Services** | Do services orchestrate constituted responsibilities? | Decisions located outside the service | Service knows every rule |
| **Flows** | Does the signal become internal meaning quickly? | Qualification object, command, decision, rejection type | Source record survives deep inside the app |
| **Mappers** | Which semantic decisions are taken there? | Named transduction decisions and tests | Fallbacks, defaults, identity choices hidden in mapping |
| **Errors** | Do errors distinguish violated worlds? | Typed errors by source, domain, infrastructure, commitment | Generic `Error`, `BusinessError`, `InvalidInput` everywhere |
| **Transactions** | What becomes true together? | Unit of commitment, transaction policy, outbox, recovery path | Commit lives silently inside adapter |
| **Duration** | To which stratum does each rule belong? | Reason for placement and expected variation | Temporary rules hardened, durable rules dispersed |
| **Tests** | Do tests prove invariants or only paths? | Tests for impossibility, rejection, commitment, correction | Mock-heavy orchestration tests only |
| **Observability** | Do traces reveal consequences or only steps? | Events tied to commitments and errors | Logs are clearer than the model |
| **Conversation** | Is the boundary recognized outside the code? | Team decisions, ADRs, refusal language, intake rules | Requirements arrive in upstream vocabulary |
| **Correction** | Where does each failure return? | Owner type, retry path, compensation, escalation | Failure disappears into logs or generic retry |

### Interpreting results

Use this scale:

| Result | Meaning |
| --- | --- |
| 0 to 3 strong answers | Hexagonal form without hexagonal substance |
| 4 to 7 strong answers | Partial institution with major drift risk |
| 8 to 10 strong answers | Substantive architecture with localized weaknesses |
| 11 to 13 strong answers | Strong hexagonal answerability |

A strong answer is not a convincing explanation. It is an explanation backed by a concrete place.

## IV. Code probes

*Use these probes to inspect where formal hexagonal most often lies.*

The examples below are intentionally small. They are not patterns to copy. They are diagnostic contrasts.

### Probe 1. Domain: named model or substantive model?

Weak sign:

```ts
class Account {
  constructor(
    public id: string,
    public holder: string,
    public balance: number,
  ) {}
}
```

This is a named structure. It is not yet a substantive model. It allows any balance and any state mutation.

Stronger sign:

```ts
class Account {
  private constructor(
    readonly id: AccountId,
    readonly holder: Holder,
    readonly balance: Money,
  ) {}

  static open(holder: Holder, deposit: Money): Account {
    if (deposit.isLessThan(MINIMUM_DEPOSIT)) {
      throw new MinimumDepositNotReached(deposit);
    }

    return new Account(AccountId.new(), holder, deposit);
  }
}
```

The stronger version does not only name the domain. It makes one invalid state unreachable through public construction.

Diagnostic question:

> What invalid state can no longer be produced?

If the answer is none, the model is nominal or descriptive.

### Probe 2. Port: mechanism interface or applicative conversation?

Weak sign:

```ts
interface FilePort {
  move(source: string, target: string): Promise<void>;
}
```

This may be useful. But it is named by the mechanism. The application speaks file-system language.

Stronger sign:

```ts
interface ContractEvidenceArchive {
  archiveSignedEvidence(evidence: SignedContractEvidence): Promise<ArchiveReceipt>;
}
```

This port can be implemented by file storage, object storage, database persistence, or a document service. Its name survives the replacement of the mechanism.

Diagnostic question:

> If the mechanism changes tomorrow, does the port name remain true?

If not, the port is probably too low.

### Probe 3. Mapper: field correspondence or transduction?

Weak sign:

```ts
function toCustomer(record: ExternalRecord): Customer {
  return {
    id: record.customer_id ?? record.legacy_id ?? randomId(),
    email: record.email?.trim() ?? 'unknown',
    status: record.status || 'ACTIVE',
  };
}
```

This code hides identity resolution, defaulting, loss of source uncertainty, and status interpretation inside field mapping.

Stronger sign:

```ts
type TransductionResult =
  | { kind: 'accepted'; customer: Customer }
  | { kind: 'rejected'; reason: TransductionRejection };

function transduce(record: ExternalRecord): TransductionResult {
  const identity = resolveIdentity(record);
  if (identity.kind === 'ambiguous') {
    return { kind: 'rejected', reason: identity.reason };
  }

  const email = qualifyEmail(record.email);
  if (email.kind === 'invalid') {
    return { kind: 'rejected', reason: email.reason };
  }

  return {
    kind: 'accepted',
    customer: Customer.from(identity.value, email.value),
  };
}
```

The stronger version makes acceptance and rejection equally explicit. The mapper is no longer pretending to be plumbing when it is deciding meaning.

Diagnostic question:

> What semantic decision is hidden in the mapping?

If the mapper chooses identity, defaults, loss, or rejection, it is a transduction point.

### Probe 4. Service: orchestration or hidden domain?

Weak sign:

```ts
class ProcessCustomerRecordService {
  async process(record: ExternalRecord): Promise<void> {
    const customer = map(record);

    if (!customer.email) throw new Error('invalid');
    if (record.type === 'DELETE' && record.deletedAt) await this.purge(customer);
    else if (record.garbage) await this.anonymize(customer);
    else await this.upsert(customer);

    await this.notify(customer);
  }
}
```

The service maps, validates, interprets, prioritizes, chooses, mutates, and notifies. It is not only orchestrating. It is carrying the domain without admitting it.

Stronger sign:

```ts
class ProcessCustomerRecordService {
  async process(record: ExternalRecord): Promise<void> {
    const signal = CustomerSignal.transduce(record);
    const decision = this.policy.decide(signal);
    const commitment = await this.committer.commit(decision);
    await this.publisher.publish(commitment.consequence);
  }
}
```

The service still orchestrates. But transduction, policy, commitment, and publication are named responsibilities.

Diagnostic question:

> Which decisions would disappear if the service were split apart?

If many decisions disappear, the service is the hidden domain.

### Probe 5. Transaction: atomic block or named commitment?

Weak sign:

```ts
await db.transaction(async tx => {
  await tx.insert(customer);
  await tx.insert(history);
  await bus.publish(event);
});
```

This says there is an atomic block. It does not clearly say what the application commits to, especially if the bus is not part of the same guarantee.

Stronger sign:

```ts
type CustomerCommitment = {
  customer: Customer;
  history: CustomerHistoryEntry;
  consequence: CustomerRegistered;
};
```

The commitment is named before the mechanism. The technical implementation can then use a database transaction, an outbox, retry, compensation, or escalation according to what the commitment requires.

Diagnostic question:

> What becomes true together, and what returns if it does not?

If the team answers with a database primitive only, the commitment is not yet named.

### Probe 6. Test: path verification or invariant proof?

Weak sign:

```ts
test('calls repository', async () => {
  const repo = mock<CustomerRepository>();
  await service.execute(command);
  expect(repo.save).toHaveBeenCalled();
});
```

This proves an execution path.

Stronger sign:

```ts
test('no accepted customer can be created without a resolvable identity', () => {
  const record = recordWithoutResolvableIdentity();
  const result = CustomerSignal.transduce(record);
  expect(result.kind).toBe('rejected');
});
```

This proves a refusal. It protects a boundary of meaning.

Diagnostic question:

> What does this test prove impossible?

If the answer is nothing, the test may still be useful, but it is not substantive.

## V. Drift typology

*Use this to detect erosion over time.*

Hexagonal architectures rarely fail at once. They drift.

Drifts are dangerous because they often preserve the form while degrading the operation.

| Drift | Description | Concrete sign | First correction |
| --- | --- | --- | --- |
| **Port drift** | Port stops naming a conversation and becomes technical | Methods named `save`, `fetch`, `push`, `move` | Rename around applicative capability |
| **Repository drift** | Referential becomes CRUD and imports persistence ontology | Operations by field or technical key | Rebuild around business lookup or commitment |
| **Service drift** | Service absorbs unmodeled decisions | Service grows and knows too many rules | Extract named policies, decisions, commitments |
| **Mapper drift** | Translation hides semantic decisions | Fallbacks and defaults inside mapping | Name transduction outcomes |
| **DTO drift** | Transport shape colonizes internal types | Internal model mirrors API DTO | Introduce translation boundary |
| **Error drift** | Different violations collapse into generic errors | `Error`, `BusinessError`, `InvalidInput` everywhere | Split by violated world and correction locus |
| **Transaction drift** | Commitment disappears into mechanisms | Commits inside adapters, multiple commits per case | Name unit of commitment |
| **Test drift** | Tests verify paths but not impossibilities | Many mocks, few invariant tests | Add rejection and invariant tests |
| **Monitoring drift** | Traces become clearer than the model | Developers read logs to understand rules | Move meaning back into model and errors |
| **Conversation drift** | Organization bypasses boundary grammar | Requirements arrive as fields, tables, endpoints | Establish intake language around ports |
| **Domain package drift** | Domain folder becomes legitimacy bag | Classes with names but no invariants | Remove or substantiate |
| **Pipeline drift** | Sequence continues after reason is forgotten | No one can answer why this step exists | Name the carried consequence or simplify |

### How to run a drift review

Run once per quarter, or after any major integration, migration, or incident.

Ask:

1. Which drift did we observe?
2. Where is it visible in code?
3. What consequence does it affect?
4. What happens if we do nothing for three months?
5. What is the smallest correction that restores answerability?

A drift named is not solved. But a drift unnamed compounds.

## VI. Correction order

Not every weakness should be corrected first.

Correct in order of consequence, not in order of annoyance.

### Priority 1. Correction failures

Fix first anything that prevents failure from returning to a clear place.

Examples:

- generic errors hiding violated worlds;
- silent retries without diagnosis;
- missing compensation paths;
- failures visible only in logs;
- no ownership of a broken commitment.

Reason: if failure has no return place, every other correction is blind.

### Priority 2. Commitment failures

Fix next anything that hides what becomes irreversible together.

Examples:

- transaction inside adapter with no applicative commitment;
- database commit plus downstream publish without recovery policy;
- multiple effects with no named unit;
- side effects triggered before validation completes.

Reason: unowned irreversibility is more dangerous than messy representation.

### Priority 3. Boundary failures

Fix next anything that lets the outside name the inside.

Examples:

- mechanism-named ports;
- external DTOs living deep inside use cases;
- source-system vocabulary in the model;
- ports shaped by vendor operations.

Reason: conceptual dependency survives technical inversion.

### Priority 4. Model failures

Fix next anything that lets invalid states exist too easily.

Examples:

- public constructors bypassing factories;
- primitives where value objects are needed;
- mutable fields contradicting invariants;
- state transitions represented as casual assignments.

Reason: a model that prevents nothing is a description, not a governor.

### Priority 5. Test failures

Fix next anything that proves only paths while claiming to prove architecture.

Examples:

- mock tests for every port call;
- no test for impossible states;
- no rejection tests;
- no commitment or compensation tests.

Reason: tests should protect what the architecture claims to carry.

### Priority 6. Naming and readability failures

Fix last what is mostly vocabulary, layout, and local clarity.

Reason: naming matters, but renaming without relocated consequence is cosmetic.

## VII. The decision record

*Use this to capture an architectural decision in writing.*

A decision about hexagonal architecture should be recorded as a claim about answerability, not as a preference for a pattern.

Template:

```md
# Decision: adopt / reject / revise hexagonal architecture for [system]

## Context

What is the system? What mechanisms surround it? What is changing? What is expected to endure?

## Ontological candidate

Name the rule, distinction, policy, or unit of commitment that satisfies the four predicates.

## Duration

Why should this candidate outlast the current tooling?

## Commitment

What becomes irreversible together?

## Correction

Where does failure return, and how is it understood?

## Boundary

Which ports name applicative conversations? Which adapters translate mechanisms?

## Model

What does the model make impossible?

## Tests

Which tests prove invariants, refusals, commitments, or correction paths?

## Decision

Adopt, reject, simplify, or postpone hexagonal architecture.

## Consequences

What cost do we accept? What drift must we watch? What should trigger revision?
```

A decision record should be short. If it cannot name the candidate, the decision is not ready.

## VIII. Operating modes

### New project

Use:

1. ontological test;
2. decision record;
3. first model and port probes;
4. first substantive tests.

Do not begin by creating folders. Begin by naming what must answer.

### Existing project

Use:

1. evidence protocol;
2. diagnostic grid;
3. code probes;
4. drift typology;
5. correction order.

Do not begin by reorganizing packages. Begin by locating consequence.

### Incident review

Use:

1. correction failures;
2. commitment failures;
3. error model;
4. transaction naming;
5. tests that would have made the failure impossible or explicit.

Do not ask only what happened. Ask where the consequence failed to return.

### Architecture review

Use:

1. ontological candidate;
2. ports as conversations;
3. unit of commitment;
4. model impossibilities;
5. drift exposure;
6. decision record.

Do not accept diagrams without evidence.

## IX. Limits of the tools

These tools support judgment. They do not replace it.

A team can pass the ontological test and still protect the wrong thing. A team can hold a clean diagnostic and still misunderstand users. A team can name every commitment and still choose a poor product strategy.

The tools guarantee only this:

> If the team has chosen a substance to protect, the structure can be tested for whether it actually carries that substance.

They do not guarantee the substance was the right one.

That requires modeling judgment, business understanding, and organizational listening.

The tools also do not replace conversational discipline. A boundary that is respected in code but ignored in meetings will erode. A port that names a conversation in TypeScript but cannot shape conversations with product, upstream teams, and operations will become decorative.

This is why the application comes last. Used without the claim, argument, and defense, these tools become checklists in the bureaucratic sense.

A checklist disconnected from its thesis is exactly the kind of formal quality this work refuses.

## Conclusion

If the ontological test fails, choose a simpler architecture. This is not regression. It is precision.

If the diagnostic reveals gaps, correct in order of consequence: correction first, commitment second, boundary third, model fourth, tests fifth, naming last.

If drifts appear, name them in writing. A named drift has a chance of correction. An unnamed drift becomes culture.

The corpus does not promise that hexagonal architecture will work in your project.

It promises that you will know, with structural clarity, whether it can.

You have the application. That is what level 4 promised.
