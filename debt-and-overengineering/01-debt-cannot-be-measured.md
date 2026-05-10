# Debt Cannot Be Measured (not as a stock)

A senior engineer joins a team and is shown the dashboard... Technical debt: 47 days. Code smells: 312. Maintainability rating: B. The numbers are precise. They are produced by a tool that has parsed every file in the repository, applied a rulebook, and aggregated the result into a figure that can be reported upward, tracked over quarters, and compared between teams. The engineer nods. Something feels off, but the figures are there, and the figures are what gets discussed.

What feels off is that the engineer has worked in repositories where the dashboard said *47 days* and the code was a pleasure to modify, and in repositories where the dashboard said *4 days* and every change required a week of archaeology (we've felt it too). The numbers had no relation to the experience. They were neither wrong nor right. They were just measuring something else than what they claimed to measure.

This essay is about that gap. It argues that the dashboards measure substrates, not debt; that what technical debt names is a future-facing liability, becoming actual only when change must traverse those substrates and only to the extent the team's compensatory capacity is exhausted by the traversal; and that this object does not admit measurement as a stock. Whether something else, more modest, can still be known is a question the essay leaves open for what follows in this folder. The work here is to make the gap visible, so that the reflex to quantify does not distort the rest.

This essay is the first part of the [Debt and Overengineering dossier](./README.md).

## What Cunningham actually said, and what the term has become

Ward Cunningham introduced the metaphor at OOPSLA in 1992, in a talk about the WyCash portfolio system. His formulation is narrower than what the term carries today. He was describing a specific moment: the moment when a developer ships code that encodes a *partial understanding of the domain*, knowing the understanding is partial, intending to revise once production reveals what the code does not yet know. The debt is the gap between the shipped form and the understanding that production will eventually require.

Three things follow from this formulation, and all three matter.

First, the debt is a property of *the moment of writing*, not of the resulting code. It lives in the relation between the developer's epistemic state and the form they inscribed. A second developer reading the same code six months later cannot recover this relation by reading the code. The code is the trace; the debt is what the code is a trace of.

Second, in the strict Cunningham reading, the metaphor is best understood as intentional. The shortcut is taken consciously, with the intention of returning. Code that is bad because the developer did not know better is not debt in this strict sense; it is something else, for which we do not have a good word.

Third, the debt is *paid* in a specific currency: the friction of subsequent modification. As long as no change passes through the indebted region, the debt costs nothing. The interest is not a fixed monthly fee; it is contingent on traffic. A debt that no one ever revisits has, in operational terms, no cost.

Since 1992, the term has broadened. Fowler proposed a quadrant (deliberate or inadvertent, prudent or reckless) that explicitly admits the unintentional case, and even claims that prudent inadvertent debt may be common and unavoidable in good design teams. Kruchten, Nord and Ozkaya extend the metaphor further, to architectural commitments, neglected refactoring, deferred testing, infrastructure shortcuts, and decisions whose costs accrue without anyone having made a conscious shortcut. The contemporary use of *technical debt* covers all of this, and the question of whether the broadened term still names the same concept is rarely asked.

This essay does not arbitrate between Cunningham strict and the broadened term. It will argue, by two paths, that neither version admits the kind of measurement the dashboards pretend to provide. The strict version cannot be measured because it depends on an intentional state that is not in the code. The broadened version cannot be measured for reasons that are structural and that take longer to set out. Both paths arrive at the same place. The dashboards are not on either of them.

## What the tools actually measure

The dashboard the engineer was shown is producing a number, and the number comes from somewhere. It is not invented. It is computed, deterministically, from properties of the code that any analyzer can extract: cyclomatic complexity above a threshold, duplicate blocks, methods longer than thirty lines, test coverage below a percentage, deprecated APIs, missing nullability annotations. Each rule fires on a finding. Each finding is given a severity and a remediation cost in minutes. The minutes add up.

This procedure is rigorous. The number it produces is not arbitrary. But the number is not technical debt. It is something else, and the something else has a name.

What the tools measure is a *correlated substrate*: a set of structural and stylistic properties that often co-occur with technical debt, in the loose statistical sense that code with high duplication and low coverage is more likely, on average, to be code that someone will struggle to modify. The correlation is real. It is also weak in both directions.

It is weak in one direction because clean code can be heavily indebted. A repository can pass every linter, satisfy every coverage threshold, contain no duplication, and still encode a domain model that does not match the domain. The model was a guess made under time pressure; production has since revealed what the domain really requires; the code is structurally pristine and conceptually obsolete. No tool will report this. The dashboard says *4 days*. The next change will take three weeks.

It is weak in the other direction because dirty code can be debt-free in the strict sense. A senior developer working in a domain of high essential complexity may write code that triggers every smell (long methods, deep nesting, sparse comments) and yet have a complete and accurate understanding of what the code is doing, no intention of revising, and no gap between the form and the understanding. The dashboard says *47 days*. The code will outlive the dashboard.

The substrate is in the code. The debt is not. Code holds substrates: duplications, couplings, complexities, omitted tests. Architecture holds commitments: boundaries chosen, frameworks adopted, contracts exposed. Teams hold tacit compensations: workarounds known by oral tradition, files no one touches without warning, modules with an unofficial owner. Roadmaps hold future pressures: the changes the organization has not yet decided to make but will. Debt appears only across the relation of these. Static analysis can detect substrates. It cannot reach the relation.

It helps, here, to name four things that the rest of the essay will distinguish. A *signal* is what the tool detects: a count of findings, a percentage, a complexity number. A *substrate* is the form inscribed in code or architecture that may produce friction. A *liability* is the cost that becomes possible if a change traverses the substrate. A *burden* is the load actually carried by the team when friction arises and is absorbed (often silently) through workaround, coordination, and tacit memory. The dashboard reports signals. From signals, one infers substrates. The liability is hypothetical, indexed to a change program not yet known. The burden is real but distributed across people, not located in the code. None of these is debt by itself. Debt is the relation that connects them.

The slippage from "useful signal about the substrate" to "measurement of debt" is where the industry has lost something. The slippage is not innocent. Calling the output a measurement of debt allows it to be reported, tracked, and used as a management instrument. Calling it a signal would force the conversation about what the signal indicates, and that conversation is harder. So the slippage holds, for institutional reasons that have nothing to do with what is being measured.

## Why measurement is not just hard but wrong-shaped

Suppose the tools improved. Suppose someone built an analyzer that genuinely captured the gap between code and domain understanding, that read every line and somehow inferred whether the form matched what the form was trying to do. This thought experiment is useful because it fails at three levels, and the failures are instructive.

The first failure is *epistemic*. The gap that defines debt, in the strict sense, is the gap between the form and the developer's *current* understanding of the domain. The current understanding is itself partial (that is what makes the debt possible), and the future understanding that will reveal the debt is not yet available. Measuring the gap requires access to a benchmark that does not exist. At best, the tool would measure the gap between the form and *some* understanding of the domain, namely the one encoded in the tool's heuristics. This is a measurement of conformance to the tool's worldview, not of debt.

The second failure is *ontological*. Star and Ruhleder, writing about infrastructure in 1996, observed that infrastructure is invisible until it breaks. The phrase has been quoted often enough to become decorative, but it carries an exact claim: certain kinds of objects do not have a stable presence in the world; they exist only at the moment of friction, and outside that moment, asking whether they are present is asking the wrong question. Technical debt has this property in its broadened sense as well. The duplicated block, the bypassed boundary, the absent test... these are *substrates*, present in the code, available to be counted. But the *debt* is a future-facing liability that becomes actual only when change must traverse the substrate. Before that moment, the substrate is in superposition: possibly debt-bearing, possibly not, depending on what change will be required of it. The tool that measures debt before the moment of friction is measuring a wave function, not a fact.

The third failure is *sociological*. What makes a debt costly is not a property of the code alone. It is the relation between the code and the trajectory of changes that the organization will want to push through it. A substrate in a frozen region of the codebase costs nothing. The same substrate in a region of intense evolution costs massively. The cost is a function of the organization's future change program, which is not knowable in the present, and which is itself partially projective: the organization does not yet know what it will want to change. The measurement of debt at time *t* would require knowledge of the organization's intentions at time *t+n*, which the organization does not have.

These three failures compose. They do not combine into a single difficulty that better tooling could overcome. They form a structural condition: the object called *technical debt* does not have the kind of being that admits measurement as a stock. It is not measurable in the way that file size or compilation time is measurable. The reflex to measure it comes from elsewhere... from the institutional need to report, from the metaphor's financial register, from the discomfort of working with an object that resists quantification. The reflex is understandable. It is also wrong-shaped for what it tries to grasp.

## What can still be estimated

A careful reader will object that this argument proves too much. If nothing can be estimated, the engineering profession has been deluded for thirty years; if something can be estimated, the essay needs to say what. The objection is fair, and the answer is precise.

Several things can be estimated, and treating them as estimable is correct. The *remediation effort* required to bring a substrate into conformance with a chosen rulebook is estimable, because it is the work of applying known transformations to known code. The *change friction* through a region can be estimated retrospectively, by observing how long past modifications to that region took, how often they reopened, how many follow-up commits they required. The *hotspots* in a repository (files that have been changed often and that contain complex code) are identifiable, and the literature on hotspot analysis is empirical and useful. The *defect density*, *lead time*, *review friction*, *incident recurrence*, *architectural drift*: all of these can be tracked, and tracking them produces signals that a team familiar with its own codebase can read.

None of these is debt. Each is a partial signal of a possible debt regime. A team that watches them over time, that knows the history of its codebase, that can correlate friction with the substrates from which it emerges, has knowledge that no dashboard contains. The knowledge is real. It is also irreducibly *situated*: held by the team, indexed to its history, not transferable to a manager who reads the same numbers and concludes that the team is over- or under-performing.

This is the position the essay is defending: not that debt is unknowable, but that what is knowable about it is not a stock. It is a *liability* in the future-facing sense, a possibility of cost contingent on a change that has not yet been required. Liabilities of this kind are estimable only with respect to a hypothesized change program, and the estimation is a hypothesis, not a measurement. The dashboards confuse the two.

## The role the dashboards can still play

A fair reader at this point will object that, having denied the dashboards their claim to measurement, the essay should say what they are still good for. To deny them any value would overstate the case. Engineers do find the reports informative. Teams that act on high-severity findings do, sometimes, end up with codebases that are easier to work in. The correlation, however weak, is not zero.

The objection is correct, and the response is precise. The tools are useful when their output is read as *a list of locations to look at*, not as a measurement of an underlying quantity. A tool that flags a method with cyclomatic complexity 27 is not telling you that you have 27 units of debt; it is telling you that this method is a candidate for inspection by someone who knows the domain. The inspection may conclude that the complexity is essential and well-managed, in which case the finding was a false positive. It may conclude that the complexity is incidental and that a refactor would help, in which case the finding was useful. Either outcome is fine. What is not fine is summing the findings and reporting the sum as a quantity.

This distinction (between *signal that prompts inspection* and *measurement of an underlying quantity*) is the most important practical takeaway of this essay. Most dashboards in the industry conflate the two. The conflation is supported by the user interface, which presents a number, and by the management practice, which asks for a trend. The practice cannot be fixed at the level of the tool. It can only be fixed by changing what the number is taken to mean. The number is not debt. It is a count of locations that are, on heuristic grounds, worth a human reading.

A team that uses dashboards this way will get value from them. A team that uses them as scoreboards risks optimizing the scoreboard, which is a different game from improving the codebase. Goodhart's observation, that a measure used as a target tends to lose its informational value, applies here directly, and the application is not subtle.

## What this means for the rest of the folder

The essays that follow this one assume that the reader has accepted the argument made here, or at least suspended the metrological reflex long enough to read further. If debt cannot be reduced to a stock measurable from the code, then several other things become possible to think.

It becomes possible to ask whether developers can report debt themselves, since the tools cannot. [The next essay](./02-developers-cannot-report-it-either.md) argues that they cannot either, for reasons that are not about competence but about the structure of self-knowledge in writing.

It becomes possible to notice that [*overengineering*](./03-overengineering-is-debt-whose-trial-has-not-come.md), usually treated as a separate category, is not separate at all. It is debt whose trial has not yet come.

It becomes possible to entertain the more radical proposition that [code is never clean before trial](./04-code-is-never-clean-before-trial.md), and that the categories of *clean* and *indebted* are retrospective attributions made after a trial has occurred.

It becomes possible, finally, to ask what design looks like under this regime, a question taken up through [Code as Score](./05-code-as-score.md) and [Designing for Local Return](./06-designing-for-local-return.md).

None of this can be read while the metrological reflex is still operating. The dashboard is too compelling, the number is too convenient, and the pressure to report something is too institutional. The first move is to put the dashboard down, or at least to read it for what it is.

## The honest position

There is a version of this essay that ends with a manifesto: *abandon the dashboards, fire the auditors, throw out the analyzers*. That version would be wrong, for the reason already given: the tools are useful when read correctly, and abandoning them would lose the signal along with the noise. The honest position is more modest and harder to hold.

Technical debt is not absent from code, but it is not contained by code. Code holds substrates, architecture holds commitments, and teams hold tacit compensations. Roadmaps hold future pressures, and debt appears only across their relation. Static analysis can detect substrates, but cannot measure the debt relation itself.

What can be known about debt is known *indirectly*: through triangulated signals, longitudinal observation, situated inspection, and the friction that emerges when change must traverse the substrate. The model is not the financial audit, where the stock is summed and reported. The model is closer to the public health surveillance system: indicators that prompt investigation, hypotheses that get refined over time, an acceptance that the underlying object is never directly accessed and that all knowledge is indirect. A team that knows its codebase well, that has watched its evolution for years, that has lived through the friction and remembers where it came from... that team has knowledge of the debt in its codebase. The knowledge is real. It is also irreducibly situated, partially tacit, and not transferable to a dashboard.

The tools produce one of the inputs to this knowledge. They are not the knowledge itself. The dashboard is not wrong; it is incomplete in a specific way that has to be remembered every time it is read.

This is not a satisfying conclusion. It does not allow a clean handoff from intuition to measurement, which is what the industry has been seeking for thirty years. But the handoff was never available, because the object did not admit it. What is available is something else: a discipline of reading, in which numbers are signals that prompt inspection, inspection is conducted by people who know the domain, and the knowledge that emerges is held by the team rather than by the dashboard.

The rest of this folder operates inside that discipline. The essays do not measure anything. They name distinctions that allow the reading to be more accurate. They will not produce a number at the end. If they do their work, they will produce something more useful: a clearer view of what was being looked at all along.
