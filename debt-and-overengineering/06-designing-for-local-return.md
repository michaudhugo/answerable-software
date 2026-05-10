# Designing for Local Return (consequence locality as the material condition of answerability)

The previous essays of this folder did mostly negative work. They argued that [debt cannot be measured](./01-debt-cannot-be-measured.md), that [developers cannot directly report it](./02-developers-cannot-report-it-either.md), that [overengineering is not a separate category from debt](./03-overengineering-is-debt-whose-trial-has-not-come.md) but a different mode of failed trial, that [the categories of clean and indebted code are states of trajectory](./04-code-is-never-clean-before-trial.md) rather than properties of code, and that [code itself has the mode of existence of a score](./code-as-score.md) rather than an object. Each of these moves dismantled a habit of thinking. None of them, taken alone or together, told a developer what to do tomorrow morning when they sit down to write code.

This essay attempts to extract from the previous five what kind of criterion remains for design once the dismantled habits are gone. The extraction is delicate. It would be easy to overshoot, replacing the dismantled habits with a new prescriptive vocabulary that would itself need dismantling. It would also be easy to undershoot, leaving the developer with a beautiful conceptual landscape and no purchase on the practical question of how to write the next function. Neither would be useful. What follows tries to find the narrow path between them.

The criterion this essay proposes is *local return*. The good design, under this criterion, is the one that disposes the consequences of code to *return locally* when the world tests the code. Local return does not guarantee good code, because good code, in the strong sense, is a category we have already abandoned. It guarantees something more modest and more useful: that when the trial comes, its consequences will arrive somewhere identifiable, attributable, legible, and treatable, rather than scattering across the system in ways that no one can act on.

This is not a method. It is a criterion. The difference matters, and the rest of the essay will make clear why.

## What this does not say

This does not say that modularity, ownership, documentation, or boundaries are irrelevant. It says that they matter only insofar as they help consequences return somewhere identifiable, attributable, legible, and treatable. Local return is not the appearance of good structure. It is the prospective behavior of consequences under trial.

This also does not say that design becomes impossible because adequacy cannot be guaranteed in advance. It says that design must shift its target. The designer cannot control the future trial, but can prepare the conditions under which the trial's consequences will become actionable when they return.

## What the designer cannot do

To see what the designer can do, it helps to fix what the designer cannot.

The designer cannot produce *adequate code*, in the sense of code whose adequacy is a property of its present form. The previous essays established that adequacy is established only by trial, that trials are not under the designer's control, and that the same code can be adequate under one trajectory and inadequate under another. The category of adequate code is not a target one can aim at; it is a retrospective attribution.

The designer also cannot produce *universally revisable code*. Universal revisability is a tempting alternative to adequacy: if we cannot know what the future will require, perhaps we can produce code that will be easy to change in any direction. But this strategy collapses on examination. To be revisable in *any* direction is to be specialized for *no* direction, which means carrying overhead that serves no specific use, which is precisely the condition [Overengineering Is Debt Whose Trial Has Not Come](./overengineering-is-debt-whose-trial.md) called overengineering by over-mediation. Universal revisability is overengineering by another name.

The designer cannot, finally, *anticipate all the futures* that the code might face. Anticipation, when it is precise, is speculation that becomes overengineering by non-use when the anticipated future fails to arrive. Anticipation, when it is general, is overengineering by over-mediation. There is no version of anticipation that escapes the trap.

What is left, after these three exclusions, is a narrower target. The designer cannot make the future come out one way or another. They cannot prepare for all possible futures. They cannot guarantee adequacy. But they can do something subtler: they can *prepare for the moment of testing* in a way that does not depend on knowing in advance what the test will be. They can ensure that, whenever the test comes, its consequences arrive in a form that can be acted on. This is what local return names.

## What local return means

Local return has four dimensions. They are not independent, but they are distinct enough to be discussed one at a time.

The first is *localizability*. When the trial comes, when a change must be made or a problem investigated, the consequences must arrive in an identifiable place. They must not scatter across the system, propagating through dependencies whose paths no one fully sees, ending up distributed across files and modules that have no apparent relation to each other. A localizable consequence is one that can be pointed to. The trial reveals not just that something is wrong but *where* something is wrong, with enough precision that the team can reason about it.

The second is *attributability*. A localized consequence is more useful when there is also someone who is in position to address it. This is not a question of formal ownership, as in "this module belongs to team X", but of practical capacity. The consequence arrives in a region whose history, intentions, and current state are intelligible to a particular person or team. They can read the surrounding code, recognize the constraints under which it was written, understand what it is supposed to do. Without attributability, a localized consequence becomes an orphan: visible, but unactionable, because no one is positioned to act on it without first reconstructing context that has been lost.

The third is *legibility*. The consequence, having arrived in a localized and attributable region, must be intelligible *as a consequence*. The team must be able to read what has gone wrong, why, what it implies, and what the options are for addressing it. A consequence that is localized and attributable but illegible, because the code uses obscure conventions, because the documentation has decayed, because the original design rationale has been lost, is a consequence that the responsible party cannot in fact respond to. Legibility is not a luxury; it is the condition under which attribution becomes operational.

The fourth is *treatability*. The consequence, finally, must be such that it can be treated without entraining unrelated parts of the system. A consequence that requires modifying ten other modules to address it is not really local, even if its initial site is localized. The repair must be something that a small team, working in a defined region, can do without negotiating with half the organization. Treatability is what distinguishes a local consequence from a *deceptively local* one: a problem that appears small but turns out to require a large excavation when actually addressed.

These four dimensions compose. A consequence that is localizable but not attributable is a finding without an owner. One that is attributable but not legible is a responsibility without a handhold. One that is legible but not treatable is an understanding without a path forward. The designer's work is not to optimize any one of these in isolation, but to ensure that they hold together when needed.

Return one last time to the payment-provider abstraction. Local return is good if a failed provider migration, an unexpected fee rule, a missing credential, or a bypassed adapter returns to a place where the responsible team can find it, understand why it happened, and treat it without rewriting unrelated checkout, invoicing, and customer-account flows. Local return is poor if each payment change scatters across provider adapters, checkout orchestration, environment variables, monitoring dashboards, and undocumented operational habits, with no single locus able to answer.

## Local return is not modularity

A natural question at this point is whether local return is just modularity by another name. Modularity, after all, is the engineering practice of dividing systems into parts with clean boundaries, so that each part can be understood and modified independently. Is the criterion this essay proposes simply a reformulation of the modularity ideal?

The answer is no, and the difference is consequential.

Modularity is a property of the present form of the code: this module is well-bounded, that interface is clean, the dependencies are minimal. These properties are visible at the moment of writing and review. Local return, by contrast, is a property of the *prospective behavior* of the code: when consequences come, will they arrive locally? This question cannot be answered by inspecting the present form alone, because the relationship between modular boundaries and the lines along which consequences actually flow depends on something the form does not contain: the structure of the domain that the code addresses.

A modular system can have poor local return when its modules are drawn along lines that do not match the domain's lines of consequence. Consider a system divided into three modules: data access, business logic, presentation. This is a modular system in the architectural sense. But if the actual changes required tend to cross all three layers, a new feature requires changes to the data, the logic, and the presentation simultaneously, then the consequences of any change will not return locally. They will return *transversally*, traversing the modules without depositing in any of them. The modularity is real but its lines do not match the lines of consequence, so local return fails.

Conversely, a system that looks unmodular by present-form criteria can have excellent local return when its untidiness happens to track the domain's actual structure. A function that handles three apparently distinct cases inside its body, in a way that violates the principle of single responsibility, may nonetheless be the right form when the three cases are domain-bound to each other and tend to change together. Modifying any one of them is a local operation; the consequences of any change return to the function and stay there.

The distinction matters because it changes what design effort goes into. Modularity-as-present-form encourages effort that produces clean boundaries by formal criteria. Local-return encourages effort that produces boundaries that *match the rhythms of the domain*. The two often coincide, but not always. When they diverge, local return is the deeper criterion, because it is the one that determines whether the form will hold up under modification.

## The judgment that local return requires

If local return is a property of the relation between code and domain, and if it cannot be read from the code alone, then evaluating it requires something more than the inspection that modularity allows. It requires *situated judgment*: knowledge of the domain, of its history, of the rhythms along which it tends to change, of the actors whose decisions move those rhythms.

This judgment cannot be replaced by an external instrument. A consultant arriving from outside, however skilled, lacks the domain knowledge that allows them to read the lines of consequence. They will see formal modularity and call it good design; they will see formal untidiness and call it debt; they may be right or wrong in either case, but their judgment will be guessed, not seen. The judgment that local return demands is owned by the people who are inside the work: the engineers who have lived with the system, the product people who have watched the domain shift, the operators who know which kinds of failure tend to happen.

This is uncomfortable for organizations that want to evaluate engineering quality from outside. It means that the most important property of design, its disposition to local return, is not transferable to a dashboard or a review committee. It is held by the team, distributed across its members, partially tacit. An external party can ask the team about it; they cannot extract it without the team.

The implication is one that the previous essays have already prepared the ground for, in different registers. Knowledge of debt is triangulated and longitudinal. Knowledge of overengineering is contested and temporally extended. Knowledge of code as score is mediated by the surrounding apparatus. Knowledge of design quality, here, is situated and held by those inside the work. None of these is the property the industry vocabulary supposes them to be: stable, transferable, measurable. All of them require relationships of trust between those who hold the knowledge and those who need to act on it.

## Why this is the criterion

There is a question worth answering directly, before closing. Why local return? Why not some other criterion that the previous essays could equally have produced?

The answer is that local return is what makes the system *answerable* in the practical sense the term should bear. A system is answerable when, faced with a question or a problem, someone can in fact answer. The answer requires that the relevant facts arrive in a place where someone can find them. It requires that the someone can be identified. It requires that they can read what they find. It requires that they can do something about it without having to renegotiate the rest of the system.

These four requirements are exactly the four dimensions of local return. They are not coincidentally aligned; they are the same thing seen from different angles.


Local return is the material condition of answerability. Without it, *answerability* is a word with no purchase: an organization can claim to take responsibility, but the responsibility cannot actually be discharged because the consequences never arrive in a form that allows discharge. With it, answerability becomes operational: when something goes wrong, or needs to change, someone can in fact answer.

This is what the criterion offers that other candidate criteria do not. It is not about producing better code in the abstract. It is about producing systems that can be *responded to*. And response, when systems are real and stakes are real, is what engineering actually requires of its inscriptions. The rest, the elegance, the abstractions, the patterns, are means; the answerability they enable is the end. When they enable it, they earn their place. When they do not, they are scaffolding without a building, no matter how artfully constructed.

## A modest closing

The dossier this essay closes did not produce a theory of code. It produced something more limited and more honest: a set of distinctions that change how the conversation about code quality can be conducted. Debt is not a stock. Reports are not ground truth. Overengineering is not the opposite of debt. Quality is not an intrinsic property. Code is not an object. Design is not the production of adequate forms but the disposition for local return.

These propositions, taken together, do not form a method. They form a *grammar*. They give the engineer a different way of asking the questions they were already asking, and a different vocabulary for the answers. What they do not give is a procedure for getting the right answer in any particular case. That procedure does not exist, because the right answer depends on situated judgment that no procedure can substitute for.

The honest practice that the dossier as a whole points toward is therefore not a checklist or a method but an *attitude*. An attitude that takes seriously that code awaits trial, that quality is relational, that performability erodes, that consequences must return locally if they are to be answered. An attitude that does not pretend to know what the future will demand, but that prepares the conditions under which whatever is demanded can be addressed.

The work of engineering, under this attitude, is not making the right artifact. It is preparing the situation in which whatever happens to the artifact can be answered to. This is more modest than the engineering self-image often allows. It is also, on close inspection, more accurate. The artifacts we produce do not stand alone. They live or die in the relationship between what they enable and what is asked of them. Making that relationship answerable, when it is asked, is the work we are actually doing. The criterion of local return names that work clearly enough to organize attention around it.

This is what the dossier was for. Not to provide answers but to clarify what kind of question engineering is. The question, properly asked, opens onto a practice that is harder than the prevailing one but more responsive to what code actually does in the world.

## Operational remainder

| Closed reflex | What remains usable | Forbidden inference |
|---|---|---|
| Design as adequate present form | Disposition for local return under future trial | "This looks well designed, therefore its consequences will be answerable." |
| Modularity as sufficient criterion | Boundary placement by lines of consequence | "Clean modules guarantee local return." |
| Ownership as formal assignment | Attributability as practical capacity to respond | "A named owner means the consequence is answerable." |

## Dossier links

Previous essay: [Code as Score](./05-code-as-score.md)

Related essays:

1. [Debt Cannot Be Measured](./01-debt-cannot-be-measured.md)
2. [Developers Cannot Report It Either](./02-developers-cannot-report-it-either.md)
3. [Overengineering Is Debt Whose Trial Has Not Come](./03-overengineering-is-debt-whose-trial-has-not-come.md)
4. [Code Is Never Clean Before Trial](./04-code-is-never-clean-before-trial.md)
