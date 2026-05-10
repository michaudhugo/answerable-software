# Debt and Overengineering (for a grammar of code quality under trial)

The vocabulary the software industry uses to talk about code quality treats *debt*, *clean code*, and *overengineering* as if they were properties of code. They are not. They are relations between code, the trajectories of change that test it, and the surrounding apparatus that keeps it performable.

This dossier makes that case in six essays:

1. [Debt Cannot Be Measured](./01-debt-cannot-be-measured.md)
2. [Developers Cannot Report It Either](./02-developers-cannot-report-it-either.md)
3. [Overengineering Is Debt Whose Trial Has Not Come](./03-overengineering-is-debt-whose-trial-has-not-come.md)
4. [Code Is Never Clean Before Trial](./04-code-is-never-clean-before-trial.md)
5. [Code as Score](./05-code-as-score.md)
6. [Designing for Local Return](./06-designing-for-local-return.md)

The dossier is not anti-metric, anti-developer, anti-abstraction, nor anti-clean-code. If it is *anti-something*, it is anti-reification. Its claim is that the industry often treats relational, temporal, and situated phenomena as if they were stable properties of code. We do not.

The argument is accumulative. Each essay closes a habit of thinking that the previous essays leave open, and the closures compose.

The first essay closes the metrological reflex: technical debt is not a stock that dashboards can measure. The second closes the testimonial reflex: developer reports are not ground truth either, for reasons that are structural rather than circumstantial. The third closes the categorial reflex: overengineering is not a separate phenomenon from debt but another mode of the same condition, with two distinct revelations of its own. The fourth closes the substantialist reflex: the categories of *clean*, *indebted*, and *over-engineered* are not kinds of code but states of trajectory. The fifth closes the objectualist reflex: code does not have the mode of existence of an object, and what good engineering attends to is the performability of inscriptions across the apparatus that conditions their performance. The sixth opens onto what the closures leave standing: a criterion of design that names what remains for the practitioner who has accepted the displacements.

## Order of reading

1. [**Debt Cannot Be Measured**](./01-debt-cannot-be-measured.md)  
   Why dashboards measure substrates and not debt; what can still be estimated, and what cannot.

2. [**Developers Cannot Report It Either**](./02-developers-cannot-report-it-either.md)  
   Why situated knowledge of debt resists extraction by survey or workshop; how epistemic, cognitive, and sociological mechanisms compose; where self-admitted technical debt fits.

3. [**Overengineering Is Debt Whose Trial Has Not Come**](./03-overengineering-is-debt-whose-trial-has-not-come.md)  
   Why overengineering and debt are failure modes of one condition rather than opposites; how non-use and over-mediation reveal overengineering; why the justification horizon matters.

4. [**Code Is Never Clean Before Trial**](./04-code-is-never-clean-before-trial.md)  
   Why the categories of *clean*, *indebted*, and *over-engineered* dissolve into states of trial; why quality belongs to the pair `(code, trajectory)` rather than to code alone.

5. [**Code as Score**](./05-code-as-score.md)  
   Why code has the mode of existence of an inscription rather than an object; why performability erodes even when the code does not change; what design must attend to under this view.

6. [**Designing for Local Return**](./06-designing-for-local-return.md)  
   What criterion of design remains once the prior habits are displaced; what local return is; why it is not modularity; what kind of judgment it requires.

## Progression

The essays form an arc. Each closes a habit of thinking and leaves something more modest in its place.

| Essay | Reflex closed | What remains | Forbidden inference |
| --- | --- | --- | --- |
| [Debt Cannot Be Measured](./01-debt-cannot-be-measured.md) | The metrological reflex | Signals worth inspecting | "The dashboard says 47 days, therefore the codebase has 47 days of debt." |
| [Developers Cannot Report It Either](./02-developers-cannot-report-it-either.md) | The testimonial reflex | Triangulated knowledge | "The workshop list is the team's ground truth." |
| [Overengineering Is Debt Whose Trial Has Not Come](./03-overengineering-is-debt-whose-trial-has-not-come.md) | The debt vs overengineering opposition | Modes of trial | "Debt and overengineering are opposite pathologies." |
| [Code Is Never Clean Before Trial](./04-code-is-never-clean-before-trial.md) | Quality as intrinsic property | The pair `(code, trajectory)` | "This code is clean before the trajectory has tested it." |
| [Code as Score](./05-code-as-score.md) | Code as object | Performability | "The unchanged file has unchanged engineering meaning." |
| [Designing for Local Return](./06-designing-for-local-return.md) | Design as adequate form | Local return of consequences | "Good modularity guarantees answerability." |

The right-hand column is what the dossier leaves the reader with. None of these is a method. Each is a way of asking the question more accurately than the closed reflex allowed.

## What the dossier does and does not provide

The dossier does not produce a theory of code. It does not give a method for distinguishing good code from bad. It does not propose new metrics or new dashboards.

It proposes a grammar: a different way of asking the questions engineering already asks, and a different vocabulary for the answers.

What this grammar is good for, and what it is not, the essays say in their own time. The reader who finishes [Designing for Local Return](./06-designing-for-local-return.md) will have a way of holding the conversation about code quality that does less violence to what code actually is. They will not have a rule for what to do tomorrow morning. The substitution is deliberate.

The essays were written to be read in order. They can be read out of order, but each assumes the closures of those before it, and a reader who skips will encounter arguments whose weight has been built elsewhere. The total length is around twenty thousand words. It is meant to be slow reading, not because it is difficult, but because the displacements it proposes need time to settle.

## What would weaken the dossier

The dossier would be weakened if technical debt could be shown to remain measurable as a stable stock independently of future change trajectories; if developer reports could reliably recover inadvertent, normalized, distributed, and future-facing debt; if overengineering could be diagnosed without reference to later use, non-use, carrying cost, or justification horizon; or if code quality could be established independently of the trajectory through which the code is exercised.

The dossier does not require that every metric fail, every developer report distort, every abstraction become overengineering, or every clean-looking form later break.

It requires only the weaker claim: that the strongest industrial categories of code quality are relational, temporal, and situated rather than intrinsic properties of code.
