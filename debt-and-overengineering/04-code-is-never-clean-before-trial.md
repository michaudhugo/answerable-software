# Code Is Never Clean Before Trial (quality as a property of a pair)

The first three essays of this folder did related work, but it is only when they are placed side by side that the underlying claim becomes visible. [Debt Cannot Be Measured](./01-debt-cannot-be-measured.md) argued that technical debt cannot be measured as a stock. [Developers Cannot Report It Either](./02-developers-cannot-report-it-either.md) argued that developers cannot directly report it as ground truth. [Overengineering Is Debt Whose Trial Has Not Come](./03-overengineering-is-debt-whose-trial-has-not-come.md) argued that overengineering is not a separate category but a failure mode of the same condition that produces debt, with two distinct revelations of its own: non-use and over-mediation. Each essay was about a different supposed access to debt, or a different supposed boundary, and each closed off that access or that boundary. What remains, after the three closures, is a question the essays did not need to answer in order to make their points but which they have together made unavoidable. If debt is not in the code as a measurable stock, not in the developers as reportable knowledge, and not distinct from overengineering as a separate kind of pathology, then what *is* it?

This essay proposes the answer that the three previous ones implied without stating. The industry uses *debt* to name a specific state: form failing under traversal. But the term gestures toward something larger, namely the condition of inscribed form awaiting a verdict that the world will deliver. This essay takes the larger gesture seriously, and proposes that *debt*, in its technically loose but conceptually accurate sense, is the name for that condition. The boundary between *debt* and *clean code* does not exist in the form itself; it exists only in the history of trials the form has or has not been put through. Every form inscribed in a codebase carries some residual bet about future adequacy, and that bet awaits a verdict the world will deliver. What we call *clean code* is the subset of forms that have either passed their trials silently, or have not yet been tested rigorously enough to fail. The category of clean code, treated as a present-tense property of code, is a retrospective attribution dressed up as a current state.

To be precise from the start: *clean* is not a property of code at the moment of writing. It is a verdict that only trial can deliver. Before the trial, what we call clean is an estimate, sometimes accurate, often not. After the trial, the verdict may be *clean* (the code absorbed the change silently), *indebted* (the code resisted), or *over-engineered* (the code was unused, or used at a cost beyond its return). Each is a possible outcome of trial. None is a property of the form alone.

This is a heavier claim than the previous three, and it deserves a careful unfolding.

## What this does not say

This does not say that craft, clarity, tests, naming, locality, or restraint do not matter. It says that these are dispositions toward likely trials, not guarantees of intrinsic quality. They improve the odds. They do not escape the verdict.

This also does not say that engineers should stop judging code before trial. They must judge before trial, because design happens under uncertainty. The claim is narrower: pre-trial judgment is estimation, not verdict. The verdict belongs to the trajectory through which the code is later exercised.

## The pattern the previous essays describe

The first essay observed that the dashboards measure substrates, not debt. Substrates are properties of the code as it sits today: complexity, duplication, coupling, missing tests. They are real, and they are countable. The debt is the cost that those substrates may impose on future work, which is not knowable until the future imposes it. The substrate is in the code; the debt is not.

The second essay extended the analysis to developer testimony. Developers can report what they remember having compromised, in regions they still inhabit, in language they are willing to speak. They cannot report what they did not see at the time, what they have since normalized, or what would cost them socially to admit. Their reports are situated speech acts about a phenomenon that does not have a stable referent in the code itself.

The third essay extended the analysis to overengineering, in both its modes. Overengineering by non-use is form whose anticipated future fails to arrive. Overengineering by over-mediation is form that is exercised but at a cost exceeding its value. Neither is a category of code distinct from debt. Both are failure modes of the same condition: form awaiting a verdict that comes by different paths.

What these three analyses share is a common structural observation, which the previous essays did not name explicitly. In each case, the property that the industry vocabulary attributes to the code as a present-tense fact (debt, indebted region, over-engineered layer) turns out to be a *future-facing relation* whose actuality depends on events that have not yet happened, or that have happened in ways that the code alone cannot disclose. The code is what it is. What the code *is debt of, or overengineering of, or clean instance of* depends on what happens next, and on how the team reads what is already happening.

This pattern, taken seriously, has consequences that go beyond the analyses that produced it. The pattern says that the categories the industry uses to talk about code quality do not name properties of code; they name relations between code and the trajectories of change that will or will not test it. And if that is true for the categories of debt and overengineering, it is hard to see why it would not be true for the category of clean code as well.

## The trial as the only verdict

Consider what we mean when we say a piece of code is *clean*. The judgment usually rests on a set of present-tense properties: the code is well structured, the names are clear, the tests cover the cases, the dependencies are minimal, the abstractions are appropriately placed. These properties are real, and they are visible at the moment of writing. A code review can verify them. A senior developer can recognize them. They give us reasons to call the code clean.

But these properties are not the criterion. They are correlates of a deeper criterion that we usually do not name explicitly. The deeper criterion is *the code will hold up under the changes that will be required of it, and at a cost commensurate with what it provides*. We call code clean when we trust it to absorb future modification gracefully, and when we believe its present cost matches its present contribution. We call code indebted when we expect it to resist modification. We call code over-engineered when we expect it to either sit unused or impose disproportionate cost in use. The present-tense properties are signs from which we infer these future-tense and continuous-tense properties, but the future-tense and continuous-tense properties are the ones that actually matter.

This is hidden in normal practice because the inference from properties to behavior usually works. Code that is well structured, in the present, *typically* holds up well under modification. The correlation is real and the heuristic is useful. But the correlation is not identity, and the heuristic is not the criterion. We have evidence of this every time we encounter code that looked clean and turned out to be indebted, or code that looked messy and turned out to be robust under exactly the kind of change it was asked to absorb. Those cases are not anomalies in the heuristic; they are demonstrations that the heuristic was always a proxy for something else.

The something else is the trial. A piece of code's quality is what its trials reveal it to be. Before the trials, the quality is an estimate, made on the basis of present-tense properties that correlate, on average, with the underlying criterion. After the trials, the quality is established, by the actual evidence of how the code held up. The estimate and the established quality are different objects. We routinely confuse them, because the estimate is what we have to work with at the moment of writing and review, and the established quality only arrives later.

The proposition this essay defends is that the underlying criterion is *always* the trial, and that everything we say about code quality before the trial is an estimate. There is no third option. There is no way to know, in advance of trial, that a piece of code will remain clean under the trajectory it will actually face. There is only a way to predict, with varying accuracy, that it will probably hold up.

## Five states of revelation

If quality is established only by trial, then code at any given moment exists in one of five states with respect to its trials.

The first state is *not yet tested*. The code has been written, perhaps reviewed, perhaps deployed, but no change has yet attempted to traverse it under conditions that would reveal whether its assumptions hold, and no continuous use has yet revealed its cost-to-value ratio. This is the largest category in any active codebase. Most code, most of the time, is in this state. Its quality is estimated but not established.

The second state is *tested and passing silently*. A change has come, has traversed the code, and has been absorbed without friction; or the code has been used, repeatedly, at a cost commensurate with what it provides. The code's assumptions held; the form was adequate to the case; the trial was passed without anyone noticing it was a trial. This is what we usually mean when we point to a region of a codebase and say *this code has worked well for years*. We are saying it has been tested, in one or both modes, and has passed.

The third state is *tested and failing through friction*. A change has come, has tried to traverse the code, and has met resistance. Workarounds have been added, exceptions have been carved, modifications have taken longer than expected. This is the state the industry calls *indebted*. The debt was always present as a latent property of the code's bet; the failure of the trial made it actual.

The fourth state is *tested by absence*. A long stretch of time has passed without any change exercising the code's assumptions in the way they were designed for. The code sits, structurally intact, but unexercised. This is the state the industry calls *over-engineered* in its speculative-failure sense. The verdict comes by negative evidence and arrives slowly, gated by the form's justification horizon.

The fifth state is *tested through costly traversal*. The code is exercised, sometimes heavily, but the exercise reveals its cost to exceed its value. Each traversal pays a small surcharge for the form's existence; the surcharge is invisible at any single point, but the cumulative drag is real. This is the state the industry calls *over-engineered* in its over-mediation sense. The verdict comes by continuous evidence whose granularity is too fine for ordinary observation.

These five states are not categories of code. They are *moments in the trajectory of a single condition*. Every piece of code is in state one at the moment of writing. Over time, it migrates to one of the other four. The migration is determined not by the code itself but by what the world asks of it and what the team continues to pay for it. The same piece of code, in two different organizations with two different change programs and two different cost tolerances, may end up in different states. The code did not differ. The trials it was subjected to did.

This is what makes the categories of *clean*, *indebted*, and *over-engineered* unstable as descriptions of code. They are descriptions of code-in-a-trajectory, and the trajectory is not in the code.

The payment-provider abstraction can occupy each of these states. At the moment of writing, it is not yet tested. If the second provider arrives and the abstraction absorbs it with little friction, it becomes tested and passing silently. If the second provider arrives and the abstraction resists the actual integration, it becomes tested and failing through friction. If no second provider arrives within the declared horizon, it becomes tested by absence. If the abstraction is used every week but makes every payment change heavier than a simpler provider-specific design would have made it, it becomes tested through costly traversal. The code may be materially similar across these states. The trajectory is not.

## Quality as a property of the pair

The reframe forces a more uncomfortable conclusion. If the state of code depends on its trajectory of trials, then the quality of code is not a property of the code alone. It is a property of *the pair* (code, trajectory).

This is not a metaphysical flourish. It has practical consequences that show up the moment one tries to evaluate code without specifying the trajectory.

Consider an abstraction layer that introduces a clean separation between two subsystems. Is the abstraction layer good code? The honest answer is: it depends on what changes will be required, and at what cost the layer is being exercised. If the two subsystems are going to evolve along independent trajectories and the layer is exercised at modest cost, the layer will absorb that evolution gracefully and will look, in retrospect, like prescient design. If the two subsystems are going to evolve in lockstep, the layer will become a coordination overhead that adds nothing, and will look, in retrospect, like overengineering by non-use. If the layer is exercised heavily but at a cost that exceeds what a simpler form would have imposed, it will look like overengineering by over-mediation. The layer itself does not change between these scenarios. The trajectory does. The quality is a property of the pair, not of the layer.

Consider, conversely, a piece of code that hardcodes a value where a configuration parameter could have been used. Is the hardcoded value debt? Again, it depends. If the value will need to change, hardcoding it is debt that will become acute when the change is required. If the value never needs to change, the hardcoding is fine, and adding configuration would have been speculative complexity. The code does not know which of these is true. Neither does the developer at the moment of writing. The quality is established only when the trajectory makes its demand or fails to make it, and at the cost the form imposes in the meantime.

This is why the question *is this code good* tends to produce circular conversations. The participants are usually trying to evaluate the code without specifying the trajectory, which is like asking whether a key is a good key without specifying the lock. The key has properties (its shape, its precision, its material), and those properties matter, but the key's quality as a key is established by its fit to a particular lock. A key that opens its intended lock cleanly is a good key. The same key, attempted on a different lock, may be useless or destructive.

The implication for engineering practice is uncomfortable. The well-formed conversation about code quality requires specifying both the code and the anticipated trajectory of change, including the rate and cost of expected use. The trajectory is itself partially unknown. So the conversation must be conducted under uncertainty, with explicit hypotheses about what is likely to be required, and with awareness that the hypotheses may turn out to be wrong. This is harder than the conversation we usually have, in which the code is evaluated as if its quality were intrinsic. But the easier conversation is wrong, and the harder one is right.

## A shift in competence

If quality is a property of the pair, then what does it mean to be a competent developer?

The traditional answer, implicit in most engineering culture, is that a competent developer produces *adequate code*. They write functions that are well-named, classes that are well-organized, abstractions that are well-placed. They follow principles that are believed to produce good code. They are evaluated on the visible properties of their work.

The reframe makes this answer untenable. Adequate code, as a final present-tense property independent of trajectory, does not exist. There is only code-that-will-or-will-not-prove-adequate-to-its-trajectory, and the trajectory is not under the developer's control. A developer who produces code that is structurally beautiful, well-tested, and elegantly composed has not thereby produced adequate code; they have produced code whose adequacy will be revealed by trials they cannot anticipate.

What the developer can actually do is *produce revisability*. They can produce code that, when its trial does come (whether as friction, as absence, or as costly traversal), will be relatively easy to modify in response. This is a different criterion than producing-the-adequate, and it has different practical implications. Producing-the-adequate encourages overinvestment in the present form, on the assumption that getting it right now will protect against future trouble. Producing-the-revisability accepts that getting it right now is mostly impossible, and shifts effort toward making it easier to get right *next time*.

The two criteria converge in many practical cases. Code that is well-structured for its current purpose tends to also be revisable, because the same properties (clarity, locality, low coupling, restraint in abstraction) serve both functions. But they diverge in the cases where they matter most: in the speculative architectures that look adequate but resist modification when the anticipated future fails to arrive, in the heavily mediated layers that look adequate but compound cost on every traversal, and in the rough but locally honest code that looks inadequate but bends willingly when asked to.

The competent developer, under this reframe, is not the one who produces the most beautiful code at the moment of writing. They are the one who produces code that, after trials they cannot foresee, can still be modified by the developers who will inhabit it later. This is a more modest skill than the traditional one, and it is more honest about the conditions under which code is actually written.

## An anticipated objection

A reader will object at this point that this analysis seems to dissolve all distinctions. If all code is awaiting trial, and quality is a property of the pair rather than the code, then is not the careful developer in the same epistemic position as the careless one? Are we saying that effort and craft do not matter, that all code is equally good or bad, that we should stop trying to write well?

The answer is no, and the reason is precise.

What the analysis dissolves is the *category of intrinsically good code*. It does not dissolve the difference between code that is well-disposed to its likely trials and code that is not. Some forms are observably better-prepared to absorb change than others. A function that is local, named clearly, dependent on few things, and accompanied by tests that exercise its boundary cases is, on most realistic trajectories, more revisable than a function that is global, opaque, dependent on many things, and untested. This is not a tautology. It is an observation about how forms behave when modification arrives.

The point is that the well-disposed form is not therefore *good in itself*. Its good-disposition is itself relative to a class of trajectories that we estimate to be likely. For trajectories outside that class, the well-disposed form may be worse than the alternative. A function that is highly modular and tested is *better* under most ordinary trajectories, and *worse* under a trajectory in which the very boundary between the function and its environment turns out to need redrawing. Modularity protects against modification within boundaries; it impedes modification of boundaries. Which trajectory you are on determines which is the right tradeoff.

What competence means, then, is something like *judgment about which trajectories are likely, and disposition of the code accordingly*. The careful developer is not producing intrinsically good code. They are producing code well-disposed to the trajectories they have implicitly bet on. Their bet may turn out to be wrong, and when it does, their code will look indebted in retrospect even though it was carefully made. The careful developer is not exempt from the trial. They are placing their bet with more information and more attention than the careless one, and that improves their odds, but it does not make them sovereign over the verdict.

This is the honest position. Effort and craft matter. They improve the odds. There is no final code quality to produce outside a trajectory of use and change.

## What this prepares

The reframe this essay defends has consequences that the next essays of the folder will explore.

The first consequence, which [Code as Score](./05-code-as-score.md) takes up, is temporal. If every form is awaiting its trial, and the trial unfolds over time, then the code does not have the mode of existence we usually attribute to objects. Objects sit, persist, and are what they are independently of when we look at them. Code, under the present analysis, is something else. It is a form whose existence is in some sense *suspended* between the moment of writing and the moments of trial that will eventually establish what it was. This suspension has properties of its own. It is not neutral. It is not free. The next essay argues that the right metaphor for this mode of existence is not the object but the *score*, and that this metaphor changes what good design has to attend to.

The second consequence, which [Designing for Local Return](./06-designing-for-local-return.md) takes up, is practical. If quality is a property of the pair, and the pair includes the trajectory of trials, then design cannot be evaluated only by looking at the code. It must be evaluated by looking at how the code is *disposed* with respect to the trials it is likely to face. This requires a criterion that is not about the code's present form but about its *prospective relation* to the changes that will pass through it. The final essay names this criterion and shows how it reorganizes what design is for.

For now, the working position is this. There is no final clean code outside trial, in the strong sense the industry vocabulary suggests. There is only code in various states of trial: not yet tested, tested and passing silently, tested and failing through friction, tested by absence, and tested through costly traversal. The category of debt names one of these states (the third). The category of overengineering names two (the fourth and the fifth). The category of clean code, in its strong industrial sense, names the second state: tested and passing silently. The first state (not yet tested) is what most code is in most of the time, and it is misread as already-clean only because the trial has not yet revealed otherwise. The five states are not different kinds of code. They are different relations between code and the world that has or has not yet asked something of it, at the cost it is or is not willing to pay.

If this is right, then the conversation engineering teams have about debt has been slightly misframed for as long as the conversation has existed. The team was never trying to identify the indebted code, distinct from the clean code. The team was trying to read the trajectory of trials its codebase has been on and is likely to be on, and to estimate where that trajectory will go badly next. This is harder than identifying indebted code. It is also more honest about what knowing the codebase actually involves.

## Operational remainder

| Closed reflex | What remains usable | Forbidden inference |
|---|---|---|
| Clean code as intrinsic property | Code well-disposed to likely trajectories | "This code is clean before trial." |
| Debt as a separate kind of code | Trial states of one condition | "Clean, indebted, and overengineered are stable kinds." |
| Craft as guarantee | Craft as improved odds under uncertainty | "Careful code is exempt from later verdict." |
| Code review as verdict | Code review as pre-trial estimation | "The review settled the quality of the code." |

## Dossier links

This essay depends on the closures established in the first three essays:

1. [Debt Cannot Be Measured](./01-debt-cannot-be-measured.md)
2. [Developers Cannot Report It Either](./02-developers-cannot-report-it-either.md)
3. [Overengineering Is Debt Whose Trial Has Not Come](./03-overengineering-is-debt-whose-trial-has-not-come.md)

It prepares the final two essays:

4. [Code as Score](./05-code-as-score.md)
5. [Designing for Local Return](./06-designing-for-local-return.md)
