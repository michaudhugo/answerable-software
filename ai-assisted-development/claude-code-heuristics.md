# Claude Code

*Heuristics for configuration, architecture, judgment, action, and economic discipline*

© 2026 Hugo Michaud. Licensed under CC BY-SA 4.0.

## Contents

- [I. CLAUDE.md: Project Constitution](#i-claudemd-project-constitution)
    - [1. CLAUDE.md contains what is too dangerous to forget.](#1-claudemd-contains-what-is-too-dangerous-to-forget)
    - [2. CLAUDE.md is not the project wiki.](#2-claudemd-is-not-the-project-wiki)
    - [3. A rule with no operational consequence does not belong in CLAUDE.md.](#3-a-rule-with-no-operational-consequence-does-not-belong-in-claudemd)
    - [4. A good CLAUDE.md says what the project is, not everything it contains.](#4-a-good-claudemd-says-what-the-project-is-not-everything-it-contains)
    - [5. The raw tech stack does not belong in CLAUDE.md unless it genuinely changes judgment in most tasks.](#5-the-raw-tech-stack-does-not-belong-in-claudemd-unless-it-genuinely-changes-judgment-in-most-tasks)
    - [6. Preferences, tone, and formatting do not belong in the constitutional layer.](#6-preferences-tone-and-formatting-do-not-belong-in-the-constitutional-layer)
    - [7. CLAUDE.md must include a gradient, not only constraints.](#7-claudemd-must-include-a-gradient-not-only-constraints)
    - [8. CLAUDE.md should be revisable without fear.](#8-claudemd-should-be-revisable-without-fear)
    - [9. The same discipline applied to other forms applies to CLAUDE.md itself.](#9-the-same-discipline-applied-to-other-forms-applies-to-claudemd-itself)
- [II. Rules: Local Constraints](#ii-rules-local-constraints)
    - [10. What is not true everywhere must not live in CLAUDE.md.](#10-what-is-not-true-everywhere-must-not-live-in-claudemd)
    - [11. The right question is not 'is this true?' but 'where should this apply?'](#11-the-right-question-is-not-is-this-true-but-where-should-this-apply)
    - [12. A good rule reduces the relevant world rather than adding prose.](#12-a-good-rule-reduces-the-relevant-world-rather-than-adding-prose)
    - [13. Prefer scoped rules to global instructions whenever the constraint is not universal.](#13-prefer-scoped-rules-to-global-instructions-whenever-the-constraint-is-not-universal)
    - [14. Rules are not Skills.](#14-rules-are-not-skills)
    - [15. A rule should be easy to violate and easy to verify.](#15-a-rule-should-be-easy-to-violate-and-easy-to-verify)
- [III. Skills: Carriers of Judgment](#iii-skills-carriers-of-judgment)
    - [16. A Skill is not a component and not a rule.](#16-a-skill-is-not-a-component-and-not-a-rule)
    - [17. Create a Skill only for a recurring variety of judgment.](#17-create-a-skill-only-for-a-recurring-variety-of-judgment)
    - [18. A Skill must absorb ambiguity, not merely store information.](#18-a-skill-must-absorb-ambiguity-not-merely-store-information)
    - [19. A Skill must remain alive, reusable, and revisable.](#19-a-skill-must-remain-alive-reusable-and-revisable)
    - [20. Prefer few, sharp Skills over a forest of micro-Skills.](#20-prefer-few-sharp-skills-over-a-forest-of-micro-skills)
    - [21. Shared Skills between agents are not a problem. Interchangeable agents are.](#21-shared-skills-between-agents-are-not-a-problem-interchangeable-agents-are)
    - [22. Do not add a Skill unless you can also state its revocation condition.](#22-do-not-add-a-skill-unless-you-can-also-state-its-revocation-condition)
    - [23. If a Skill mainly restates a rule, it should probably not exist.](#23-if-a-skill-mainly-restates-a-rule-it-should-probably-not-exist)
- [IV. Subagents: Separation of Loci](#iv-subagents-separation-of-loci)
    - [24. Create a subagent only when there is real separation of context, posture, or permissions.](#24-create-a-subagent-only-when-there-is-real-separation-of-context-posture-or-permissions)
    - [25. If a Skill suffices, do not create a subagent.](#25-if-a-skill-suffices-do-not-create-a-subagent)
    - [26. An agent without its own posture is probably redundant.](#26-an-agent-without-its-own-posture-is-probably-redundant)
    - [27. Size agents by the variety they need to regulate, not by the org chart.](#27-size-agents-by-the-variety-they-need-to-regulate-not-by-the-org-chart)
    - [28. A good subagent reduces drift; it does not just add a step.](#28-a-good-subagent-reduces-drift-it-does-not-just-add-a-step)
    - [29. The orchestrator coordinates; it does not reinterpret on behalf of subagents.](#29-the-orchestrator-coordinates-it-does-not-reinterpret-on-behalf-of-subagents)
    - [30. Escalation to the orchestrator is for scope failure, not routine correction.](#30-escalation-to-the-orchestrator-is-for-scope-failure-not-routine-correction)
    - [31. Ownership of every artifact must be declared and exclusive enough to matter.](#31-ownership-of-every-artifact-must-be-declared-and-exclusive-enough-to-matter)
    - [32. Ownership transfer must be explicit.](#32-ownership-transfer-must-be-explicit)
- [V. Hooks: From Principle to Constraint](#v-hooks-from-principle-to-constraint)
    - [33. What must truly block must not remain a textual intention.](#33-what-must-truly-block-must-not-remain-a-textual-intention)
    - [34. The configuration layer orients; hooks enforce.](#34-the-configuration-layer-orients-hooks-enforce)
    - [35. Use blocking behavior only for constraints that matter enough to interrupt the flow.](#35-use-blocking-behavior-only-for-constraints-that-matter-enough-to-interrupt-the-flow)
    - [36. Hooks apply systemically, including across delegated actions.](#36-hooks-apply-systemically-including-across-delegated-actions)
    - [37. Use hooks for human review thresholds, not only for comfort.](#37-use-hooks-for-human-review-thresholds-not-only-for-comfort)
    - [38. Filtering early costs less than correcting late.](#38-filtering-early-costs-less-than-correcting-late)
    - [39. Do not automate a check that changes nothing.](#39-do-not-automate-a-check-that-changes-nothing)
    - [40. Runtime traces matter.](#40-runtime-traces-matter)
    - [41. Hooks must themselves remain answerable.](#41-hooks-must-themselves-remain-answerable)
- [VI. Memory: What Must Be Findable](#vi-memory-what-must-be-findable)
    - [42. Instruction and memory are not the same thing.](#42-instruction-and-memory-are-not-the-same-thing)
    - [43. What must always shape judgment belongs in context. What must be retrievable belongs in memory.](#43-what-must-always-shape-judgment-belongs-in-context-what-must-be-retrievable-belongs-in-memory)
    - [44. Memory should index first, detail second.](#44-memory-should-index-first-detail-second)
    - [45. Memory should support correction, not only historical accumulation.](#45-memory-should-support-correction-not-only-historical-accumulation)
    - [46. Volatile information should not live in long-term memory.](#46-volatile-information-should-not-live-in-long-term-memory)
    - [47. A memory entry should justify its own persistence.](#47-a-memory-entry-should-justify-its-own-persistence)
- [VII. Documentation: Writing to Orient](#vii-documentation-writing-to-orient)
    - [48. Document to orient, not to record.](#48-document-to-orient-not-to-record)
    - [49. A document without an identifiable reader and an identifiable future decision tends toward dead form.](#49-a-document-without-an-identifiable-reader-and-an-identifiable-future-decision-tends-toward-dead-form)
    - [50. Code carries much of the how; documentation should privilege the why.](#50-code-carries-much-of-the-how-documentation-should-privilege-the-why)
    - [51. Prefer entry points, boundaries, and maps over encyclopedic description.](#51-prefer-entry-points-boundaries-and-maps-over-encyclopedic-description)
    - [52. Do not write documentation 'just in case.'](#52-do-not-write-documentation-just-in-case)
    - [53. If documentation is replacing missing architectural clarity, fix the architecture first.](#53-if-documentation-is-replacing-missing-architectural-clarity-fix-the-architecture-first)
- [VIII. Prompts and Exchanges: Routing Decisions](#viii-prompts-and-exchanges-routing-decisions)
    - [54. Write to route a decision, not to narrate a context.](#54-write-to-route-a-decision-not-to-narrate-a-context)
    - [55. The smallest form that preserves correct judgment is the best form.](#55-the-smallest-form-that-preserves-correct-judgment-is-the-best-form)
    - [56. Prefer a stable exchange contract.](#56-prefer-a-stable-exchange-contract)
    - [57. One block, one function.](#57-one-block-one-function)
    - [58. Bound first, enrich second.](#58-bound-first-enrich-second)
    - [59. A short, structured output is worth more than a long explanation.](#59-a-short-structured-output-is-worth-more-than-a-long-explanation)
    - [60. Standardize response form to reduce cost and downstream parsing.](#60-standardize-response-form-to-reduce-cost-and-downstream-parsing)
    - [61. Minimize ambiguity before minimizing words.](#61-minimize-ambiguity-before-minimizing-words)
    - [62. A solicitation that is not yet determined is not merely ambiguity to eliminate.](#62-a-solicitation-that-is-not-yet-determined-is-not-merely-ambiguity-to-eliminate)
- [IX. Planning and Iteration: Structuring the Work](#ix-planning-and-iteration-structuring-the-work)
    - [63. Plan mode is for structural bifurcations, not for every task.](#63-plan-mode-is-for-structural-bifurcations-not-for-every-task)
    - [64. Bounded micro-iteration is often better than monolithic requests.](#64-bounded-micro-iteration-is-often-better-than-monolithic-requests)
    - [65. The right grain of iteration closes locally without rigidifying globally.](#65-the-right-grain-of-iteration-closes-locally-without-rigidifying-globally)
    - [66. Do not ask Claude to infer what is already certain.](#66-do-not-ask-claude-to-infer-what-is-already-certain)
    - [67. Every iteration must leave the next step clear.](#67-every-iteration-must-leave-the-next-step-clear)
    - [68. Use planning when the cost of a wrong structure would exceed the cost of explicit clarification.](#68-use-planning-when-the-cost-of-a-wrong-structure-would-exceed-the-cost-of-explicit-clarification)
    - [69. Treat iteration boundaries as correction boundaries, not only delivery boundaries.](#69-treat-iteration-boundaries-as-correction-boundaries-not-only-delivery-boundaries)
- [X. Variance and Judgment: Controlling Drift](#x-variance-and-judgment-controlling-drift)
    - [70. The target is not strict sameness, but bounded variation.](#70-the-target-is-not-strict-sameness-but-bounded-variation)
    - [71. Clear boundaries reduce irrelevant exploration.](#71-clear-boundaries-reduce-irrelevant-exploration)
    - [72. A clear internal gradient reduces undirected hesitation.](#72-a-clear-internal-gradient-reduces-undirected-hesitation)
    - [73. Co-location of interpretation, consequence, and correction reduces rework from wrong localization.](#73-co-location-of-interpretation-consequence-and-correction-reduces-rework-from-wrong-localization)
    - [74. Good configuration disciplines interpretation without suppressing it.](#74-good-configuration-disciplines-interpretation-without-suppressing-it)
    - [75. If Claude drifts often, the problem is usually world, gradient, or localization.](#75-if-claude-drifts-often-the-problem-is-usually-world-gradient-or-localization)
    - [76. When Claude improvises more than it executes, treat that as compensation, not performance.](#76-when-claude-improvises-more-than-it-executes-treat-that-as-compensation-not-performance)
    - [77. Use triple answerability as a session vitality test.](#77-use-triple-answerability-as-a-session-vitality-test)
    - [78. Output alone is not evidence of living action.](#78-output-alone-is-not-evidence-of-living-action)
- [XI. Economy: What You Actually Pay For](#xi-economy-what-you-actually-pay-for)
    - [79. You pay not only for the request, but for everything Claude must still hold alive to answer it.](#79-you-pay-not-only-for-the-request-but-for-everything-claude-must-still-hold-alive-to-answer-it)
    - [80. Cost comes mainly from wrong context, wrong exploration, and wrong closure.](#80-cost-comes-mainly-from-wrong-context-wrong-exploration-and-wrong-closure)
    - [81. A small constitutional kernel beats a large doctrine loaded every time.](#81-a-small-constitutional-kernel-beats-a-large-doctrine-loaded-every-time)
    - [82. Rules and Skills usually save more context than imports do.](#82-rules-and-skills-usually-save-more-context-than-imports-do)
    - [83. The setup must remain lighter than the drift it absorbs.](#83-the-setup-must-remain-lighter-than-the-drift-it-absorbs)
    - [84. Enough variety to regulate, not enough forms to suffocate.](#84-enough-variety-to-regulate-not-enough-forms-to-suffocate)
    - [85. Authorize inference only when discovery is worth the cost.](#85-authorize-inference-only-when-discovery-is-worth-the-cost)
    - [86. Economy is not only token economy.](#86-economy-is-not-only-token-economy)
    - [87. A habitable setup is economically superior to a merely elaborate one.](#87-a-habitable-setup-is-economically-superior-to-a-merely-elaborate-one)
- [XII. Foundational Principles: What Everything Else Follows From](#xii-foundational-principles-what-everything-else-follows-from)
    - [88. Constitute the right world before configuring the workflow.](#88-constitute-the-right-world-before-configuring-the-workflow)
    - [89. Place the right actor before delegating.](#89-place-the-right-actor-before-delegating)
    - [90. Ensure the correction path before accelerating.](#90-ensure-the-correction-path-before-accelerating)
    - [91. Stabilize only what deserves to be transmitted.](#91-stabilize-only-what-deserves-to-be-transmitted)
    - [92. A configuration is a living form of judgment, not a text repository.](#92-a-configuration-is-a-living-form-of-judgment-not-a-text-repository)
    - [93. The system must know both what it must not do and toward what it tends.](#93-the-system-must-know-both-what-it-must-not-do-and-toward-what-it-tends)
    - [94. A strong configuration replaces a significant portion of explicit planning.](#94-a-strong-configuration-replaces-a-significant-portion-of-explicit-planning)
    - [95. A small, well-architected setup can outperform a larger model configured badly.](#95-a-small-well-architected-setup-can-outperform-a-larger-model-configured-badly)
    - [96. A configuration that has not been revisited in months deserves inspection.](#96-a-configuration-that-has-not-been-revisited-in-months-deserves-inspection)
    - [97. A session can continue producing after acting has already begun to die.](#97-a-session-can-continue-producing-after-acting-has-already-begun-to-die)
- [XIII. Governance of Forms: Revocation, Conflict, Rhythm](#xiii-governance-of-forms-revocation-conflict-rhythm)
    - [98. Do not add a form unless you can say how it will end.](#98-do-not-add-a-form-unless-you-can-say-how-it-will-end)
    - [99. When governing forms conflict, resolve by consequence proximity, not by hierarchy alone.](#99-when-governing-forms-conflict-resolve-by-consequence-proximity-not-by-hierarchy-alone)
    - [100. Detect silent conflict between forms before it produces incoherent behavior.](#100-detect-silent-conflict-between-forms-before-it-produces-incoherent-behavior)
    - [101. The rhythm of revision should follow the rhythm of variation in the milieu.](#101-the-rhythm-of-revision-should-follow-the-rhythm-of-variation-in-the-milieu)
    - [102. Formal growth without revocation is drift in another register.](#102-formal-growth-without-revocation-is-drift-in-another-register)
    - [103. Every form should justify both its existence and its continued existence.](#103-every-form-should-justify-both-its-existence-and-its-continued-existence)
    - [104. Governance must include subtraction, not only addition.](#104-governance-must-include-subtraction-not-only-addition)

A Claude Code setup is not a pile of instructions. It is an architecture of forms: some living, some dead, some still becoming one or the other. Its quality depends not only on what it contains, but on whether what persists remains answerable to the tensions that produced it, to the milieu in which it operates, and to the consequences it generates.

The goal of this guide is to help build a setup that remains alive: answerable to what called it forth, coupled to the world it governs, corrigible when it drifts, and economical enough to remain habitable.

These are heuristics, not rules. They orient judgment in recurring classes of situations rather than producing binary verdicts. A heuristic that is consistently violated by good practice has either been wrongly stated or wrongly scoped, and its formulation should be revised before its compliance is enforced.

Throughout, a recurring distinction is in play. A living form is one that remains revisable in light of the tensions that produced it and the milieu it now operates in. A dead form is one that persists without answering to either. The same form, whether a rule, a Skill, a hook, an agent, a memory entry, or a document, can shift from one state to the other without changing a line of its text.

The guide is governed by five structural questions:

- **World.** What is the relevant context, and what is noise?

- **Actor.** Who interprets, owns, and corrects within this scope?

- **Gradient.** Toward what is the system oriented, and how does it know when it is drifting? A configuration has a gradient when, given two compliant outputs, it can rank them because it knows toward what it tends, not only what it must avoid.

- **Answerability.** Can what persists still answer to origin, situation, and consequence? A course of action remains answerable when it can still respond to what called it forth, to the situation in which it now operates, and to the consequences it is producing. Loss of any of the three converts action into mere activity.

- **Action.** Is the system still acting, or is activity merely continuing after action has thinned out?

Four principles structure the guide:

- **Co-location of interpretation, consequence, and correction.** The locus that interprets a task must also own its consequences and be the one that corrects them when they go wrong. Separation of these three is the most reliable source of unaddressable drift.

- **Boundary clarity.** The system must discriminate the relevant world from noise, so that attention and action remain bounded by what actually matters.

- **Internal gradient.** The system must have an internal orientation toward better and worse states, so that it is guided not only by constraints but by direction.

- **Vitality of action.** Action must be understood not only as execution but as a temporal career. Something first becomes action-demanding, then becomes action, then stabilizes, and may later continue as mere activity after acting has already begun to die. A setup must remain capable of detecting that pathology in itself.

This document is organized from the most global forms of configuration to the most local. The order matters: each layer presupposes that the layers above it are already correct.

## I. CLAUDE.md: Project Constitution

CLAUDE.md is not documentation. It is the constitutional kernel of the setup. It defines what the project is, what must remain true, where Claude must stop, and toward what direction the system serves. Five things deserve to be defined here: the relevant world, the actors and their loci, the invariants that must always hold, the thresholds at which Claude must escalate, and the gradient that orients the whole. Anything beyond these five is expansion without mandate.

### 1. CLAUDE.md contains what is too dangerous to forget.

If forgetting it would cause structural drift, it belongs here. If forgetting it would only be inconvenient, it belongs elsewhere.

### 2. CLAUDE.md is not the project wiki.

Facts, history, module descriptions, and how things work belong in documentation. CLAUDE.md governs; it does not explain exhaustively.

### 3. A rule with no operational consequence does not belong in CLAUDE.md.

If it does not change what Claude does in most tasks, it is dead weight. Dead weight in the constitutional layer degrades the signal of everything else.

### 4. A good CLAUDE.md says what the project is, not everything it contains.

Constitution is not inventory. A comprehensive record of everything the project does is a wiki. A governing document is shorter and harder, because every line must justify its constitutional status.

### 5. The raw tech stack does not belong in CLAUDE.md unless it genuinely changes judgment in most tasks.

A language or framework name is rarely constitutional by itself. A framework-level constraint that changes nearly every decision may be. Distinguish decoration from governance.

### 6. Preferences, tone, and formatting do not belong in the constitutional layer.

Output style belongs in output conventions. Mixing it with core invariants weakens both, because Claude reads CLAUDE.md as a governing signal and stylistic preferences lower its signal-to-noise ratio.

### 7. CLAUDE.md must include a gradient, not only constraints.

A setup that only says what not to do is corrigible but undirected. Constraints block drift but produce no direction. The gradient is what tells the system toward what it is oriented, not only what it must avoid. Without it, even a fully constrained system produces compliance without coherence.

### 8. CLAUDE.md should be revisable without fear.

If changing one line threatens the whole system's coherence, the system is over-coupled to its own text. That is rigidity, not stability. Good constitutions are durable because they are well-designed, not because they are fragile.

### 9. The same discipline applied to other forms applies to CLAUDE.md itself.

Ask periodically whether the document is still answerable to the tensions that produced it and to the actual milieu of the project. A CLAUDE.md that has not been revisited in months may be governing a project that no longer exists.

## II. Rules: Local Constraints

Rules are local invariants. They apply within bounded scopes. They exist because not everything true of the system is true everywhere in the system.

### 10. What is not true everywhere must not live in CLAUDE.md.

A constraint that applies only to one module, one file type, or one workflow phase is a local invariant. Place it in .claude/rules/. Promoting local constraints to the constitutional layer inflates the global signal with noise.

### 11. The right question is not 'is this true?' but 'where should this apply?'

Scope is a first-order design decision. Getting it wrong produces either over-constraint, where rules apply where they have no business, or silent under-constraint, where rules are present but irrelevant to the actual context.

### 12. A good rule reduces the relevant world rather than adding prose.

Rules should narrow the decision space. If a rule requires several paragraphs to apply, it is probably documentation that has been misclassified. A rule should be short enough to apply without interpretation.

### 13. Prefer scoped rules to global instructions whenever the constraint is not universal.

What can be loaded locally should not be paid globally. Scoped rules keep the constitutional layer clean and ensure that Claude is not carrying irrelevant constraints into every task.

### 14. Rules are not Skills.

A rule enforces a binary constraint. A Skill carries a way of judging. If contextual discernment is required to apply it correctly, it is probably a Skill, not a rule. Misclassifying one as the other produces either over-rigidity or under-enforcement.

### 15. A rule should be easy to violate and easy to verify.

If no one can tell whether a rule is being followed, it is not governing anything. A good rule has a clear violation state, a clear compliance state, and no ambiguous middle. The general principle that a rule which never triggers is drifting toward dead form is treated in Section XIII.

## III. Skills: Carriers of Judgment

A Skill is not a fact repository and not a binary rule. It is a reusable carrier of situated judgment. It exists to absorb recurring ambiguity. A Skill earns its place when the same kind of judgment is needed repeatedly and Claude handles it inconsistently without one.

### 16. A Skill is not a component and not a rule.

It is a way of thinking in a recurring class of situations. Its value is not in the information it contains but in the judgment it encodes. Without situated discernment, it is a reference document misclassified as a Skill.

### 17. Create a Skill only for a recurring variety of judgment.

One-off ambiguity does not warrant a Skill. The signal for creating one is recurrence: the same kind of judgment is needed repeatedly, and without the Skill, Claude handles it inconsistently across sessions.

### 18. A Skill must absorb ambiguity, not merely store information.

Information belongs in documentation or memory. A Skill must actively help Claude decide in a situation where the right answer is not obvious. If it only holds facts without a way of weighing them, it is not a Skill.

### 19. A Skill must remain alive, reusable, and revisable.

A Skill that cannot evolve with the project is already drifting toward dead form. Skills must remain answerable to the situations that produced them. If the situation changes and the Skill does not, it will encode outdated judgment under the appearance of continuity.

### 20. Prefer few, sharp Skills over a forest of micro-Skills.

Too many Skills degrade selection quality and increase the probability that Claude will invoke the wrong one. A small number of well-differentiated Skills outperforms a large collection of overlapping ones.

### 21. Shared Skills between agents are not a problem. Interchangeable agents are.

A Skill can be common to multiple agents; that is efficiency. What must not be common is posture: the interpretive stance from which an agent acts. Two agents with the same posture add complexity without capacity.

### 22. Do not add a Skill unless you can also state its revocation condition.

Every added form should carry an imaginable condition for merge, downgrade, or removal. Without it, accumulation becomes the default trajectory, and the setup grows toward rigidity under the appearance of capability.

### 23. If a Skill mainly restates a rule, it should probably not exist.

Judgment and constraint should not be duplicated without reason. If the Skill adds no discriminative power beyond what the rule already enforces, the duplication adds maintenance cost without value.

## IV. Subagents: Separation of Loci

A subagent is not a miniature job title. It is a distinct locus of attention, action, consequence, or correction. It exists only when genuine separation is required.

### 24. Create a subagent only when there is real separation of context, posture, or permissions.

Without at least one of these three, the subagent is redundant overhead. Context separation means the subagent genuinely should not see everything. Posture separation means it interprets differently. Permission separation means it has a different authorization boundary.

### 25. If a Skill suffices, do not create a subagent.

A subagent is expensive. It introduces context boundaries, handoff points, and additional failure modes. If the required behavior is a way of judging rather than a separate locus of consequence, use a Skill instead.

### 26. An agent without its own posture is probably redundant.

Two agents with the same interpretive stance do not increase useful variety. They are copies of the same locus, adding complexity without new capacity. Posture is the defining characteristic of an agent, not the task it was assigned.

### 27. Size agents by the variety they need to regulate, not by the org chart.

Do not mirror human roles unless those roles correspond to genuinely distinct loci of consequence and correction. An architecture shaped by the org chart will inherit the same inefficiencies as the org chart.

### 28. A good subagent reduces drift; it does not just add a step.

Every handoff is a possible failure of co-location between interpretation and consequence. A subagent that adds a step without narrowing consequence or reducing drift is net negative. The question is always: does this agent make the system more correctable, or just more complex?

### 29. The orchestrator coordinates; it does not reinterpret on behalf of subagents.

If the orchestrator must continuously repair subagent judgment, the architecture is wrong. The locus that interprets must be the one that acts and corrects. When the orchestrator absorbs correction, co-location has been violated and drift has acquired no clear address.

### 30. Escalation to the orchestrator is for scope failure, not routine correction.

If every obstacle escalates, the correction path has no address. Escalation should be the exception, triggered by genuine scope failure or dependency failure, not the default response to any difficulty.

### 31. Ownership of every artifact must be declared and exclusive enough to matter.

If multiple loci modify the same artifact without explicit transfer, consequence has no stable owner. The failure becomes structurally unaddressable because no single locus holds responsibility.

### 32. Ownership transfer must be explicit.

A handoff is part of the artifact's history of responsibility. Implicit transfers accumulate as invisible debt. When ownership moves without being recorded, the next correction has no map.

## V. Hooks: From Principle to Constraint

Hooks are where intention becomes enforcement. They are the layer that turns 'should' into 'cannot proceed unless,' and the surface at which the system holds the boundary between Claude's action and the world's irreversibility.

### 33. What must truly block must not remain a textual intention.

A sentence in a configuration file is an intention. A hook with a blocking exit code is a constraint. Only the second one actually prevents the action. If a violation is genuinely unacceptable, enforce it materially.

### 34. The configuration layer orients; hooks enforce.

Do not confuse governance of judgment with runtime constraint. CLAUDE.md shapes how Claude thinks about a task. Hooks make certain outcomes impossible to reach without interruption. They operate at different levels and should not be substituted for each other.

### 35. Use blocking behavior only for constraints that matter enough to interrupt the flow.

Enforcement without discrimination becomes bureaucracy. Reserve blocking exit codes for what genuinely cannot be allowed to continue. If a constraint is important but not critical, a warning is often sufficient.

### 36. Hooks apply systemically, including across delegated actions.

They are not only for the top-level actor. Hooks applied at the session level apply to all delegated actions within it, including subagent tool calls. Enforcement is systemic, not just top-level.

### 37. Use hooks for human review thresholds, not only for comfort.

The highest value of a hook is early interruption before an irreversible or expensive action is taken. Blocking before a destructive write, before a cross-module modification, before a PR is created. This is worth far more than cleanup after the fact.

### 38. Filtering early costs less than correcting late.

A hook that blocks or redirects early saves both risk and downstream rework. The cost of enforcement at the point of action is almost always lower than the cost of undoing the consequences.

### 39. Do not automate a check that changes nothing.

A hook that never alters the course of action is overhead. Automate only checks that actually change what happens. A hook that always exits zero regardless of input is not a constraint; it is noise with latency.

### 40. Runtime traces matter.

If a consequence log is required for self-correction, it must exist as a real runtime artifact, not as a stated intention. Self-correction without material traces has nothing to work from. The log is the material of accountability.

### 41. Hooks must themselves remain answerable.

A hook that blocks correctly in an old world but not in the current one is now a dead constraint enforcing a former milieu. Hooks accumulate the same pathologies as any other form. Review them at the same rhythm as the rest of the configuration.

## VI. Memory: What Must Be Findable

Memory is not instruction. Instruction shapes active judgment. Memory must be findable when needed without burdening every task.

### 42. Instruction and memory are not the same thing.

Mixing them produces both bloated context and unreliable recall. Instructions need to be active, present in every relevant task. Memory needs to be findable, retrievable when needed, not always loaded.

### 43. What must always shape judgment belongs in context. What must be retrievable belongs in memory.

The criterion is frequency and universality of application. A constraint that applies to every task should be in context. A reference that applies to one category of task should not be paid for universally.

### 44. Memory should index first, detail second.

A good memory system tells Claude when something matters before asking it to read deeply. If a memory entry requires full reading to determine relevance, it is poorly indexed. The first line should answer: when does this matter?

### 45. Memory should support correction, not only historical accumulation.

The value of memory lies in drift recognition, continuity across sessions, and return paths to prior correct states, not in historical completeness for its own sake.

### 46. Volatile information should not live in long-term memory.

Frequently changing state belongs in live tools or real-time calls, not in sedimented recall. Volatile information in long-term memory becomes stale faster than it becomes useful, and pollutes the retrievals that depend on it.

### 47. A memory entry should justify its own persistence.

If no future decision is plausibly improved by retrieving it, it has become accumulation rather than memory. Memory has costs in retrieval, storage, and attention; an entry that never changes a decision is dead weight in a layer whose only job is to improve future decisions.

## VII. Documentation: Writing to Orient

Documentation in a Claude Code setup should orient future judgment, not merely record what once happened. It earns its place by being consulted before a decision is made.

### 48. Document to orient, not to record.

The purpose of documentation in this context is to route judgment to the right place. A document that only records history without guiding future decisions is archival, not operational. Ask what decision it enables before writing it.

### 49. A document without an identifiable reader and an identifiable future decision tends toward dead form.

Before writing, name who will read it, when, and which decision it will inform. A document written for no specific reader and no specific occasion of use becomes archival rather than operational. The reader, the occasion, and the decision are jointly the test of whether the document earns its place.

### 50. Code carries much of the how; documentation should privilege the why.

The how is usually recoverable from code inspection. The why, meaning the reasoning, the trade-offs, and the constraints that shaped the decision, is what becomes inaccessible as the codebase evolves. Document the gap, not the mechanics already visible in the code.

### 51. Prefer entry points, boundaries, and maps over encyclopedic description.

A good document tells you where to start, what is out of scope, and how the system is divided. That is more useful than describing every component in detail. Orientation is worth more than completeness.

### 52. Do not write documentation 'just in case.'

Speculative documentation is one of the easiest forms of dead persistence. It accumulates without accountability. Write documentation when a specific future reader needs it for a specific future decision, not as a precaution.

### 53. If documentation is replacing missing architectural clarity, fix the architecture first.

Documentation that compensates for architectural confusion will grow faster than the confusion it covers. Adding more explanation does not resolve structural ambiguity. Fix the source, not the symptom.

## VIII. Prompts and Exchanges: Routing Decisions

A prompt is not a narrative. It is a routing mechanism. Its role is to reduce ambiguity before action begins.

### 54. Write to route a decision, not to narrate a context.

Every sentence should either bound the problem, specify a constraint, or identify the output. Background that does none of these is overhead. Ask whether each sentence changes what Claude will do; if not, remove it.

### 55. The smallest form that preserves correct judgment is the best form.

Longer prompts are not inherently more precise. Precision comes from structure, not from volume. A well-structured short prompt outperforms an unstructured long one every time.

### 56. Prefer a stable exchange contract.

Intent, scope, constraints, preserve, ask-before, output. This is a routing protocol, not a stylistic preference. Each element removes a dimension of ambiguity. Use as many as the task requires, and no more.

### 57. One block, one function.

Do not ask a single exchange to perform multiple structurally different acts if they can be separated. Compressing them into one prompt produces structurally uncertain output. Separate concerns into separate exchanges or separate agents.

### 58. Bound first, enrich second.

Define what is in scope before adding detail. Enriching a space before bounding it causes Claude to explore the enrichment rather than execute within the bound. Scope must come first.

### 59. A short, structured output is worth more than a long explanation.

If the output format is open-ended, the cost of parsing and validating it is transferred downstream. Structured output is composable, checkable, and cheaper to work with. Specify format to make outputs useful beyond the immediate exchange.

### 60. Standardize response form to reduce cost and downstream parsing.

A specified output format eliminates response-structure decisions and makes outputs composable across sessions. Standardization is a form of economy: it transfers the cost of format decisions out of the token budget.

### 61. Minimize ambiguity before minimizing words.

Brevity that preserves ambiguity is a false economy. The correct sequence is: remove ambiguity first, then remove words. A short ambiguous prompt is more expensive than a slightly longer clear one.

### 62. A solicitation that is not yet determined is not merely ambiguity to eliminate.

It may be practical pressure not yet resolved into a determinate form. Forcing it too quickly into a concrete instruction produces a coherent but misplaced response. Name the tension before naming the task; let the form of response become intelligible from the situation itself rather than imposed on it. Overformalizing a problem before it has become determinable forecloses better answers before they can form.

## IX. Planning and Iteration: Structuring the Work

Planning is a mode, not a ritual. Iteration is the structural unit of correction. Both should preserve the possibility of local revision without freezing the system globally.

### 63. Plan mode is for structural bifurcations, not for every task.

Use it when multiple plausible structures exist and choosing wrongly would be expensive to undo. For tasks with a clear structure, invoking a planning phase is overhead, not discipline.

### 64. Bounded micro-iteration is often better than monolithic requests.

Large requests compress multiple decision points into one exchange and make correction expensive. Small, bounded iterations allow local correction without global rework. The grain of iteration should match the natural closure unit of the task.

### 65. The right grain of iteration closes locally without rigidifying globally.

An iteration too coarse forces expensive correction later because errors compound. An iteration too fine creates integration overhead because partial outputs must be assembled. Find the boundary that closes cleanly without locking in premature decisions.

### 66. Do not ask Claude to infer what is already certain.

Giving Claude latitude to infer what you already know wastes tokens and introduces variance. Reserve inference for what is genuinely uncertain. Certainty should be stated, not rediscovered. When localization is itself part of the question, by contrast, letting Claude infer it is legitimate; the cost of discovery should be proportional to its value.

### 67. Every iteration must leave the next step clear.

An iteration that ends without a clear next action has not truly closed. The handoff, even in a solo session, must be explicit. Ambiguous closure is deferred rework.

### 68. Use planning when the cost of a wrong structure would exceed the cost of explicit clarification.

Planning earns its place when structural decisions are reversible only at high cost. If the structure is clear or correction is cheap, planning is overhead.

### 69. Treat iteration boundaries as correction boundaries, not only delivery boundaries.

An iteration boundary is a point at which errors should be caught and corrected, not only a checkpoint for delivery. Building correction into the rhythm of iteration is cheaper than deferring it to the end.

## X. Variance and Judgment: Controlling Drift

The goal is not identical output. The goal is bounded, answerable, correctable variation.

### 70. The target is not strict sameness, but bounded variation.

A configuration that eliminates all variance also eliminates adaptability. The goal is variation that stays within principled bounds, remains answerable to the original intent, and can be corrected when it drifts.

### 71. Clear boundaries reduce irrelevant exploration.

When the relevant world is well defined, Claude does not spend tokens exploring outside it. Both cost and interpretive drift drop. Defining the world clearly is the first act of economy.

### 72. A clear internal gradient reduces undirected hesitation.

When the system has an internal sense of better and worse states, Claude can choose among plausible options without wandering. Direction is what converts corrigibility into capability.

### 73. Co-location of interpretation, consequence, and correction reduces rework from wrong localization.

When the locus that acts also owns and corrects its consequences, errors stay local and correction has an address. Separating these three produces drift that has no natural correction point.

### 74. Good configuration disciplines interpretation without suppressing it.

A setup that removes all interpretive latitude has become scripting. The goal is disciplined judgment, bounded but alive, not mechanical execution. If Claude never needs to judge, the configuration has replaced it rather than oriented it.

### 75. If Claude drifts often, the problem is usually world, gradient, or localization.

Frequent drift is a symptom of one of three things: the relevant world is not well defined, the system lacks clear direction, or the wrong locus is responsible for the output. Diagnose the source before reconfiguring.

### 76. When Claude improvises more than it executes, treat that as compensation, not performance.

Repeated workarounds, repeated reframings, and escalating local repair are signs that the system is compensating for something broken at a deeper level. Adding more detail to the prompt does not fix the source. Re-anchor the original request.

### 77. Use triple answerability as a session vitality test.

Can the current course of action still answer to what called it forth, to the present situation, and to the consequences it is producing? If one of these three is lost, the session may be producing output while acting has already thinned out.

### 78. Output alone is not evidence of living action.

A session can remain productive in appearance while having lost its structural connection to the original request, the present situation, and the actual consequences being produced. Output without answerability is activity, not action.

## XI. Economy: What You Actually Pay For

The cost of a Claude Code setup is not mainly the cost of the last prompt. It is the cost of everything the system must keep alive to answer well.

### 79. You pay not only for the request, but for everything Claude must still hold alive to answer it.

The cost is the total cognitive surface held active to produce a correct answer. Long-lived context, broad exploration, and rework are more expensive than they appear in isolation. Economy requires managing the whole surface, not just the last input.

### 80. Cost comes mainly from wrong context, wrong exploration, and wrong closure.

Irrelevant context loads unnecessary surface. Poorly bounded exploration generates useless tokens. Wrong closure forces rework. All three compound. Reducing token cost means addressing these three sources, not just shortening prompts.

### 81. A small constitutional kernel beats a large doctrine loaded every time.

The constitutional kernel should be small enough that loading it every time costs almost nothing. A large doctrine loaded unconditionally is a form of inefficiency baked into the architecture itself.

### 82. Rules and Skills usually save more context than imports do.

Scoped loading and selective invocation are the main levers of context economy at scale. A well-placed rule or Skill avoids loading an entire documentation set into a session where only a fraction is relevant.

### 83. The setup must remain lighter than the drift it absorbs.

If the cure is heavier than the disease, the setup has become the problem. Configuration overhead that exceeds the variance it regulates is its own form of drift, one that accumulates silently under the appearance of rigor.

### 84. Enough variety to regulate, not enough forms to suffocate.

The setup should cover the recurring varieties of judgment and constraint the project actually faces, no less, and not significantly more. Adding forms beyond genuine need increases selection noise and maintenance burden without improving coverage.

### 85. Authorize inference only when discovery is worth the cost.

Inference is justified when it can correct your framing or surface a real uncertainty you had not considered. It is wasteful when it merely rediscovers what you already know. The cost of discovery should be proportional to its value.

### 86. Economy is not only token economy.

It includes attention, maintenance burden, interruption frequency, correction cost, and formal overhead. A setup that is cheap in tokens but expensive in maintenance is not economical. Optimize for the full cost of operation.

### 87. A habitable setup is economically superior to a merely elaborate one.

A setup that is correct but exhausting to use will not remain in use. Habitability, meaning the ease of living and working within the configuration, is a real measure of quality. An elaborate setup that is abandoned costs more than a simpler one that is maintained.

## XII. Foundational Principles: What Everything Else Follows From

These are not tips. They are structural conditions. Violate them and the setup may remain formally correct while substantively dead. Their function here is to make explicit, at the foundational level, what governs the rest of the guide.

### 88. Constitute the right world before configuring the workflow.

A workflow built on a wrong definition of the relevant context will produce coherent action toward the wrong things. The world, meaning what is relevant and what is noise, must be right before anything is built on top of it.

### 89. Place the right actor before delegating.

Delegation without a clear owner of consequences is diffusion. Every task must have a locus that interprets, acts, and corrects. Identify it before distributing work. Delegation without ownership is not efficiency; it is deferred failure.

### 90. Ensure the correction path before accelerating.

Speed without the ability to correct produces fast drift. Before accelerating any part of the system, ensure that corrections can be made where they need to happen, at the locus of consequence, not two handoffs away.

### 91. Stabilize only what deserves to be transmitted.

Codification makes things portable, but also potentially opaque. Only stabilize forms that are mature enough that their transmission will not carry more distortion than value. Premature stabilization locks in partial resolutions as if they were complete.

### 92. A configuration is a living form of judgment, not a text repository.

A configuration that cannot be revised without fear is already becoming dead form. A configuration that is never revised is on the same trajectory. The vitality of a configuration is its answerability to the project it governs and the consequences it produces. A constraint that cannot be questioned is already becoming dead form, for the same reason: it has stopped governing and started merely persisting.

### 93. The system must know both what it must not do and toward what it tends.

Constraints without direction produce a system that avoids violations while producing nothing coherent. Direction without constraints produces orientation without ground. A configuration without gradient blocks drift but produces no direction; a configuration without invariants produces direction without safety. Both are necessary, and neither is sufficient alone.

### 94. A strong configuration replaces a significant portion of explicit planning.

When the relevant context, the right actor, and the direction are well defined, Claude does not need to be told how to approach a task. It already knows its scope, its responsibility, and its orientation. Planning becomes the exception, not the default.

### 95. A small, well-architected setup can outperform a larger model configured badly.

This is not a claim about raw capability. It is a claim about surface area for error. A well-bounded, well-oriented setup has fewer failure modes than a powerful model with no structural guidance. Architecture multiplies capability.

### 96. A configuration that has not been revisited in months deserves inspection.

Not because it is certainly wrong, but because the project has changed and the configuration may not have followed. Inspection does not require revision, but it requires asking whether the governing forms still answer to the project they govern.

### 97. A session can continue producing after acting has already begun to die.

Activity is not the same as acting. A session can produce output, follow procedures, and complete tasks while having lost its structural connection to the original request, the present situation, and the consequences being generated. Output is not proof of vitality; this is the most consequential pathology of an apparently working setup, because it is invisible to anyone reading only the output.

## XIII. Governance of Forms: Revocation, Conflict, Rhythm

A setup becomes durable not only by adding good forms but by governing their lifecycle. It must know how forms end, how they arbitrate when they conflict, and at what tempo they are revised.

### 98. Do not add a form unless you can say how it will end.

Every rule, Skill, hook, agent, or memory entry should have at least an imaginable revocation, merge, downgrade, or archival condition. A form with no exit path is biased toward persistence beyond its usefulness from the moment it is created.

### 99. When governing forms conflict, resolve by consequence proximity, not by hierarchy alone.

The form most recently exposed to real consequence in the relevant context carries more living information than a higher-level form that has not been tested there. Local refinement is legitimate, but only when it does not violate a higher invariant. When it does, the invariant holds and the local form must be revised, not the invariant.

### 100. Detect silent conflict between forms before it produces incoherent behavior.

A rule and a Skill that give contradictory guidance on the same situation produce no error, only inconsistent output across sessions. When adding any new form, ask whether it assumes a world that another active form contradicts. Silent conflict is the hardest kind to diagnose after the fact.

### 101. The rhythm of revision should follow the rhythm of variation in the milieu.

A form revised too slowly becomes stale; it governs a context that no longer exists. A form revised too quickly never stabilizes enough to do its work. Calibrate the rhythm of revision to the actual rate of change in the domain the form governs.

### 102. Formal growth without revocation is drift in another register.

Adding forms is visible and feels like progress. The cost of accumulation is invisible. If the setup grows without corresponding revocations, it is drifting toward rigidity under the appearance of improvement.

### 103. Every form should justify both its existence and its continued existence.

Existence at creation is not a permanent license. The conditions that justified a form at creation may not persist. A form unused, untriggered, or never invoked is drifting toward dead form regardless of which kind of form it is: rule, Skill, hook, agent, memory entry, document, or constraint. A form that cannot justify its continued existence at the next review should be retired.

### 104. Governance must include subtraction, not only addition.

A setup governed only by addition eventually suffocates under the weight of its own accumulated forms. Revocation, merge, and archival are not failures; they are the mechanism by which the configuration stays alive and answerable.

This document is itself subject to the principles it contains. It should be revised when the tensions that produced it change. It should be questioned when it begins to feel like procedure rather than guidance. It should remain sharp enough to govern, clear enough to teach, and open enough to be wrong.
