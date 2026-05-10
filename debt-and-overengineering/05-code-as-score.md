# Code as Score (performability beyond the inscription)

There is something odd about how code can deteriorate while remaining identical. A function written three years ago, untouched since, can become harder to read this Tuesday than it was last Tuesday. No line has changed. The function is byte-for-byte the same. And yet something has shifted, and the shift is real enough that the developer who returns to the function feels it. The names that were once obvious now require a moment of reconstruction. The dependencies that were once familiar now belong to a version of the framework no one uses. The conventions that the function followed now look slightly off, because the conventions of the team have moved on without it.

This decay does not fit neatly into the dominant way the industry talks about code. We speak of code as if it were a thing: an artifact, an object, a substance with properties. Things have stable existence. They sit, they persist, they are what they are independently of when we look at them. And code does behave that way at the level of bytes: the file on disk is unchanged, the bytes are intact, the version control system can prove it. But at the level that actually matters for engineering practice, the level at which someone has to read it, modify it, run it, integrate it, migrate it, explain it, or retire it, code does not have the stability of a thing. It has a different mode of existence, one that the metaphor of the object obscures rather than clarifies.

This essay proposes a different metaphor: code as score. The proposal is not decorative. It is meant to do work that the object metaphor cannot do, and to make visible an aspect of code's mode of existence that the previous essays of this folder have circled without naming directly.

The metaphor does not deny that code executes as a machine-readable artifact; that level is real and matters. It targets a different level: the one at which code must be understood, modified, integrated, migrated, explained, and kept performable by humans and systems over time. That level is what the object metaphor cannot grasp, and it is the level at which most of the practical concerns of engineering actually live.

## What this does not say

This does not say that code is not an executable artifact. It says that execution is only one performance among others. Code must also be read, modified, integrated, migrated, explained, and retired. The object metaphor captures the inscription; it misses the apparatus that keeps the inscription performable.

This also does not say that the score metaphor replaces the previous essays. It depends on them. [Debt Cannot Be Measured](./01-debt-cannot-be-measured.md) showed why debt cannot be read as a stock in the code. [Developers Cannot Report It Either](./02-developers-cannot-report-it-either.md) showed why the surrounding knowledge of debt cannot be extracted as a clean inventory. [Overengineering Is Debt Whose Trial Has Not Come](./03-overengineering-is-debt-whose-trial-has-not-come.md) showed that unused or over-mediated form is another mode of failed trial. [Code Is Never Clean Before Trial](./04-code-is-never-clean-before-trial.md) showed that code quality is a state of trajectory rather than an intrinsic property. This essay names the temporal medium in which those trials happen: performability.

## The score and its performance

Consider what a musical score is. It is a piece of paper. The paper has marks on it. The marks encode something, but the something is not the marks. The piece of music does not exist on the paper; it exists when the score is performed. Performance is what brings the music into being. Between performances, the paper sits, but the music is in suspension: it is not happening, even though the paper that encodes it is fully present.

A score, in this sense, has two distinct relations to its existence. There is the textual artifact, the paper, the marks, what could be photographed, and there is the performance, the sound in time, the air vibrating, the hands moving. The textual artifact persists. The performance is each time singular, dated, irreproducible in the strict sense. A symphony performed in Vienna in 1820 and the same symphony performed in Tokyo in 2020 share the score but are not the same musical event. The score made each performance possible without being either of them.

What allows a score to remain performable across centuries is not the score alone. It is the maintenance of an entire surrounding apparatus: musicians who can read the notation, instruments that the notation assumes, conventions of interpretation that fill in what the notation does not specify, traditions of performance that link the notation to a sound. If any of these decays sufficiently, the score becomes harder to perform, even though the score itself has not changed. A medieval score in a notation no one can read anymore is not a score that has been corrupted; it is a score whose performability has been lost while the score itself sits exactly as it was written.

Code is in this position more often than the object metaphor admits. A piece of code, like a score, exists fully only in its performance: when it runs, when it is read by a developer who understands it, when it is modified by someone who can hold its assumptions in mind. Between performances, the code sits, byte-for-byte intact, but its performability is in suspension. And that performability depends on a surrounding apparatus that is not in the code: developers who know the language, libraries that the code uses, conventions of style and structure, memory of why certain choices were made, documentation that has not gone stale.

This apparatus is not stable. It decays. Languages evolve, frameworks publish breaking changes, developers leave, conventions drift, memory fades. The code stays the same. The conditions of its performance erode. And the developer who returns to the code three years later is not encountering a corrupted artifact; they are encountering an artifact whose performability has weakened while the artifact itself remained exactly what it was written to be.

The payment-provider abstraction may still compile. Its tests may still pass. But the engineer who knew why the second provider mattered has left, the provider SDK has changed, the team's conventions for adapters have moved, the deployment pipeline no longer documents the required secrets clearly, and the bypasses introduced by delivery pressure now look like first-class paths. The file is unchanged. The performance has changed.

## The mode of existence

The shift this metaphor proposes is more than rhetorical. It changes what we should understand code to be.

If code is an object, then the work of engineering is the work of producing good objects. We try to write code that is well-formed, internally coherent, free of defects. Once written, the object exists, and our job is to maintain it: to fix it when it breaks, to update it when needs change. The object is what we work on. Its quality is its property.

If code is a score, the work of engineering is something else. It is the work of producing inscriptions whose performances will be possible across the trajectories of decay we cannot fully foresee. The inscription is what we write. The performance is what we cannot write but only enable. And what we are responsible for is not the inscription's quality as an object but its capacity to remain performable across changes in its surrounding apparatus.

This is a meaningful difference. It explains why so much code that appeared excellent at the moment of writing later becomes problematic without anyone having corrupted it. The code was excellent as an inscription. Its surrounding apparatus has shifted. The performance the inscription enabled is no longer easy to bring about. Nothing was done wrong; the conditions changed. Under the object metaphor, this looks like decay we should have prevented. Under the score metaphor, it looks like the ordinary fate of inscriptions that outlive their context.

The difference matters most when we ask what good code is. Under the object metaphor, good code is an artifact with certain properties: clarity, modularity, test coverage, low coupling. These properties are real and they matter. But they describe the inscription, not the performability. A score can be impeccably notated and yet unperformable, if the instruments it requires no longer exist or if no one can read the notation. Code, similarly, can be well-structured at the level of its text and unperformable at the level of its execution context, when its dependencies have moved, its conventions have shifted, its authors have left.

What the score metaphor brings into view is that performability is the criterion. By performability, I do not mean runtime performance in the engineering sense of latency and throughput. I mean the continued capacity of code to be executed, read, modified, integrated, migrated, explained, and retired by the humans and systems that must work with it across time. The inscription matters because it conditions performability, but it is not itself performability. And good engineering, under this view, is the work of producing inscriptions that prepare for their performances, including the performances that will be required after the original conditions have changed.

## The erosion of performability

Not all performances test the inscription equally. A score performed once is not in the same state as a score performed for two centuries by varying performers in varying contexts. Both have been performed. Only the second has been tested at the level that establishes performability across time, across performers, across drift in the surrounding apparatus. The same is true of code. A function executed successfully on its inputs has passed a trial: it ran, this time, in this context. A function executed thousands of times, modified, re-executed by successive developers, carried across versions of its environment, has passed a much richer trial. Both belong to the family the previous essays called *tested and passing*. The thin trial settles that the inscription works at all. The thick trial settles whether it remains performable as conditions move.

Once we see code this way, technical debt takes on a different shape. The metaphor we usually use for debt is financial: debt accumulates, accrues interest, must be paid down. The metaphor implies an object that grows over time as new debts are added. Code that is not modified does not, on this view, become more indebted; it stays where it is.

But under the score metaphor, code that is not modified can absolutely become more indebted, and this is the experience that the financial metaphor cannot capture. The performability of an inscription decays even when the inscription is left alone. Each month that passes without maintenance does not leave the code where it was; it leaves the code in a slightly less performable state, because the world around it has moved while it has stayed. This is not accumulation; it is *erosion*. The two are different temporal patterns. Accumulation adds; erosion subtracts. Code that is not touched does not gather debt the way a credit card does. It loses performability the way a forgotten manuscript loses readers.

This reframing has practical consequences. Under the financial metaphor, the response to debt is repayment: refactor the code, pay down what was borrowed. Under the erosion metaphor, repayment is not quite the right concept. What needs to happen is *maintenance of performability*: keeping the surrounding apparatus alive, updating dependencies before they become cliffs, refreshing the team's memory of why the code is structured the way it is, ensuring that the conventions the code follows are still legible. This is different work from refactoring. It is closer to the conservation work that museums do on aging artifacts: not changing them, but maintaining the conditions under which they can still be encountered.

The difference also explains a phenomenon that [Code Is Never Clean Before Trial](./04-code-is-never-clean-before-trial.md) touched on without explaining. Code that has been tested and found wanting accumulates visible debt: friction, workarounds, hot spots. Code that has not been tested at all, but whose performability has eroded silently, accumulates *invisible* debt: a quiet weakening of the conditions under which it could be modified. When the team finally returns to it, the code does not present as broken; it presents as foreign. The function is still doing what it was written to do. But the team has lost the ability to modify it without significant reconstruction work. No one wrote bad code. Time wrote it bad.

## What good design has to attend to

If code is a score, then good design has to attend to things that the object metaphor does not bring into focus. Three of these are particularly important.

The first is that the score must be *legible without the context of its writing*. Most code is written by people who hold a great deal of context in their heads at the moment of writing: the conversations that led to the design, the alternatives that were considered, the constraints that were operative, the names that were rejected before the chosen one. This context does not survive the writing. By the time another developer, or the same developer six months later, reads the code, the context has dissolved. What remains is the inscription, alone, with whatever signals the inscription itself can carry.

A score that depends on its composer being there to explain it is a fragile score. The same is true of code. The work of writing well is not to produce code that the author understands; it is to produce code that survives the author's absence. This sounds obvious when stated, but it cuts against the way most code is actually written. Code is typically written for the author's present-tense self. The reader is treated as an afterthought, or assumed to be a future-self with similar context. Both assumptions are wrong. The reader will arrive without the context, and the writing must compensate for this.

The second is that the score must *reveal its own conditions of performance*. A musical score that requires an obscure instrument should say so; otherwise, performers will fail to play it correctly without understanding why. Code is in the same position. It has dependencies, contracts with its environment, assumptions about what its callers will provide and what its callees will return. These conditions are real. If they are not visible in the inscription, the next developer will encounter them as failures: the code does not work, and they do not know why.

Types, interfaces, schemas, tests, and contracts are all ways of making the conditions of performance explicit. They are not, in this view, accessories to good code; they are part of what makes the inscription performable. A function with no type signature is, in score terms, a piece of notation that does not tell the performer what instrument it is for. Whether or not such a function is good code by other criteria, it is a poor score, because it conceals what someone would need to know to perform it correctly.

The third is the most uncomfortable. The score must *accept that not all of it will be performed forever*. Some of what was written will become obsolete, will lose its relevance, will need to be set aside. A live tradition is not one in which every score is preserved indefinitely; it is one in which scores enter circulation, are performed for as long as they have something to give, and are eventually retired with grace.

Code, treated as object, tends to resist this. Once written, the code is there, and removing it feels like loss. But once written, code that is no longer performed, or no longer worth performing, is a weight on the surrounding apparatus: it must still be maintained, its dependencies updated, its presence accommodated by the rest of the system. A score whose performance no longer adds value but which cannot be retired is not a treasured artifact; it is a burden carried in deference to the past.

The capacity to retire is therefore a property of well-designed code, not a sign of failure. Code that has been written so as to be removable when its time comes is more valuable than code that has been written so as to be permanent. This inverts an instinct that most developers carry. The instinct is to write for permanence: to make the code so good, so general, so well-integrated that it will last. The result is often code that becomes unremovable even when it should be removed, because too much has grown around it. The score metaphor suggests a different orientation: write so that the code can be set aside cleanly when its performance is no longer wanted, just as much as you write so that it can be performed well while it is wanted.

## What this changes about the previous essays

The reframe sharpens what the previous essays argued without quite naming it.

[Debt Cannot Be Measured](./01-debt-cannot-be-measured.md) argued that debt cannot be measured. The score metaphor explains why: debt is not a property of the inscription that could be read off it; it is a property of the relation between the inscription and its surrounding apparatus, which is itself in motion. Measuring the inscription does not measure debt because debt lives in the relation, not in the inscription.

[Developers Cannot Report It Either](./02-developers-cannot-report-it-either.md) argued that developers cannot directly report debt. The score metaphor explains this too: the developers' knowledge of debt is partly knowledge of the surrounding apparatus, which is distributed, tacit, and not contained in any single mind. They can report what they perceive of the relation, but the relation extends beyond what any of them sees.

[Overengineering Is Debt Whose Trial Has Not Come](./03-overengineering-is-debt-whose-trial-has-not-come.md) argued that overengineering is debt whose trial has not come, in two modes. The score metaphor adds depth here. An over-engineered layer is, among other things, a score with elaborate notation that no one is going to perform: the conditions of its performance have been over-specified relative to the music it is for. Over-mediation, similarly, is a score that imposes more on the performer than the music requires.

[Code Is Never Clean Before Trial](./04-code-is-never-clean-before-trial.md) argued that the categories of clean, indebted, and over-engineered code are not stable kinds but states of trial. The score metaphor recasts this: they are states of *performability* under varying surrounding apparatus. Clean code is code currently performable with low effort. Indebted code is code whose performability has eroded or been undermined by friction. Over-engineered code is code whose performability is being paid for at a rate that exceeds what its performance returns.

What the previous essays were circling, then, was a temporal property of code that is hard to see when code is treated as an object. The score metaphor names that property and gives it operational shape: code is performable, and performability decays, and good engineering is the work of producing inscriptions whose performability is robust to the trajectories of decay we cannot foresee.

## What this prepares

If code is a score, and quality is performability rather than artifact-property, then a question follows that [Designing for Local Return](./06-designing-for-local-return.md), the final essay of this folder, takes up.

What does it mean to design well, given all of this? It cannot mean producing the most beautiful inscription, since the inscription is not the criterion. It cannot mean producing the most flexible inscription, since flexibility itself can become over-mediation. It cannot mean producing the most defensive inscription, since defense against unspecified futures is exactly the speculative form that becomes overengineering when the future fails to require it.

What it can mean is something more modest, and more precise. It can mean producing inscriptions whose *consequences*, when change comes, will be locatable. Producing inscriptions whose conditions of performance are exposed enough to be inspected and renegotiated. Producing inscriptions that can be retired without dragging half the system with them. The criterion that emerges is not about how the code looks today but about how the code will *behave* when something has to be done to it. [Designing for Local Return](./06-designing-for-local-return.md) names this criterion and shows how it reorganizes what design is for.

For now, the position the score metaphor leaves us in is this. Code is not what we have written. Code is what we will be able to perform, with what is around the writing. The writing is real but it is not the music. The music is in the performance, and the performance depends on a fragile arrangement of skills, dependencies, conventions, and memory that we either maintain or watch erode. The work of the writer is not to produce a permanent thing. It is to produce an inscription that helps the music keep happening, for as long as the music is wanted, and that can be set aside cleanly when it is no longer wanted.

This is a more humble account of writing code than the industry usually offers. It is also, on close inspection, a more accurate one. The artifacts we leave behind are scores. What matters is whether someone later can still execute, read, modify, integrate, migrate, explain, or retire them without reconstructing the whole vanished apparatus around them.

## Operational remainder

| Closed reflex | What remains usable | Forbidden inference |
|---|---|---|
| Code as object | Code as inscription requiring performance | "The unchanged file has unchanged engineering meaning." |
| Debt as accumulation only | Performability erosion | "Untouched code cannot become harder to work with." |
| Permanence as design virtue | Retirability as design virtue | "Good code is code that lasts forever." |

## Dossier links

Previous essay: [Code Is Never Clean Before Trial](./04-code-is-never-clean-before-trial.md)

Next essay: [Designing for Local Return](./06-designing-for-local-return.md)

Related essays:

1. [Debt Cannot Be Measured](./01-debt-cannot-be-measured.md)
2. [Developers Cannot Report It Either](./02-developers-cannot-report-it-either.md)
3. [Overengineering Is Debt Whose Trial Has Not Come](./03-overengineering-is-debt-whose-trial-has-not-come.md)
