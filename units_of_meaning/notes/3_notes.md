# Measuring Comprehensibility

## Statically Checkable Design Level Traits

https://ieeexplore.ieee.org/stamp/stamp.jsp?tp=&arnumber=732651

> Some examples of traits include mutability, const correctness, ownership, and pure functions.

- const correctness: https://isocpp.org/wiki/faq/const-correctness#overview-const
- ownership: http://pm.inf.ethz.ch/projects/student_docs/Stefan_Naegeli/Stefan_Naegeli_MA_paper.pdf

> Even a very common advise that each method is either a mutator or an inspector is not supported in any programming language we are aware of, notwithstanding C++’s const function members.

Our instinct as engineers is to create systems that make it impossible to write bad code. This might mean that we write a language with features that limit or encourage behaviors and patterns. The concept of a comprehensibility metric is to instead provide qualitative feedback on what could be better about code, instead of programming in restrictions.

> Many names were used in the literature to label the design decisions which are to be enforced. These include, for example, Jackson’s aspect [13], formal design constraints [17], laws[24], contracts [12], invariants [22], static integrity constraints [3], assertions [23], etc.

Since software design is this messy and sometimes ambiguous field, I feel like there has been a struggle to define a language that everyone agrees on. People watch industry trends, and agree that trend X indicates a good design direction, but that requires that industry produces these advances.

> These also include design patterns, pattern languages and software architectures which are very difficult to rigorously express

A. Eden, J. Y. Gil, and A. Yehudai. Formallanguage for design patterns. extended abstract, 1997.

> Traits may state that a certain method has no side effects, is a mutator, does not access global variables directly, does not make any iterations or recursive calls (at all or excluding use of a standard data-structures library), obeys the law of Demeter, does not make polymorphic cat-calls, etc.

> The need for an objective measure of good programming style has been long noted

K. Lieberherr, I. Holland, and A. Riel. Object oriented programming: An objective sense of style. In N. K. Meyrowitz, editor, Proceedings of the 3rd Annual Conference on Object-Oriented Programming Systems, Languages, and Applications, San Diego,California, Sept. 25-30 1988. OOPSLA’88, Acm SIGPLAN Notices 23(11) Nov. 1988.

## Software visualizations for improving and measuring the comprehensibility of source code

https://core.ac.uk/download/pdf/82609565.pdf

> This is in contrast to other visualization techniques that transform source code from its traditional textual form to a graphical format.

Just reading this sentence, my intuition makes me feel that this is a bad idea. I can't quite put my finger on the reason why though.

> (1) Reachability—the number of conditions that must be evaluated to reach the segment from outside of the enclosing method, function, or other top-level statement block. This is the traditional definition of reachability.
>
> (2) Content—the log of the number of significant tokens in the segment. Some punctuation, such as block-enclosing braces or a statement-ending semicolon, is not considered significant. A pair of parentheses is counted as one token.
>
> (3) Breadth—the number of statements, methods, etc. in the innermost block containing the segment.
>
> (4) Inherent—a value assigned based on the inherent complexity of the innermost enclosing structure. For example, segments in switch or case statements are assigned an inherent complexity of 3.0. This reflects the view that some structure types are inherently more complex than others.

More ideas to keep in mind.

> Fig. 12 depicts the average time participants of the first experiment took to respond correctly to each question. The correlation between the CPG values and the experimental values was 0.452 at the 0.19 level, showing no statistically significant relationship. Post-experiment analysis of the data revealed that the correlation was strong for all questions except questions 1 and 2. Further examination revealed that questions 1 and 2 were worded so as to address how the sample program was initialized at startup. Because they did not query specifics about the knapsack code itself, it was felt that the questions confused the experimental subjects as to how they truly applied to the stated goals of performing a code inspection of the knapsack code alone.

This is because most of the complexity measurements I have seen so far do not seem to try to account for memory, familiarity, etc. Mutability presents comprehension issues because it in order to understand a mutable value completely, you need to understand all the possible ways it can be changed. This does not mean its bad, it just means its slightly less understandable.

# A metrics suite for object oriented design

https://ieeexplore.ieee.org/stamp/stamp.jsp?tp=&arnumber=295895

> The need for such metrics is particularly acute when an organization is adopting a new technology for which established practices have yet to be developed.

This statement could apply to any organization I've worked for. In my experience, the craft of writing code is something you learn on the job, so on the individual bases, established practices are always being developed somewhere, by someone.

> Previous research on software metrics, while contributing to the field’s understanding of software development processes, have generally been subject to one or more types of criticisms. These include: lacking a theoretical basis [41], lacking in desirable measurement properties [47], being insufficiently generalized or too implementation technology dependent [45], and being too labor-intensive to collect [22].

Providing a theoretical basis for comprehension measurements is not a primary concern of mine, as it is mostly focused on what is happening in the mind of the engineer/reader. Therefore, I expect that it may be a collection of heuristics that "feel right" as opposed to math backed principles that you could write a CS masters thesis on.

> An automated data collection tool was then developed and implemented to collect an empirical sample of these metrics at two field sites in order to demonstrate their feasibility and to suggest ways in which managers may use these metrics for process improvement.

There are two problems at play here. One, how do you define the metrics/measurements and two, how do you make it useful to the engineer.

> J. Kim and J. F. Lerch, “Cognitive processes in logical design: Comparing object-oriented and traditional functional decomposition software methodologies,” Working Paper, Camegie Mellon Univ. Graduate School of lndus&ial Admin., -1991,

> Given the importance of class design, the metrics outlined in this paper specifically are designed to measure the complexity in the design of classes. The limitation of this approach is that possible dynamic behavior of a system is not captured.

Comprehensibility of code as I see it entails understanding two traits:

- What is the code supposed to be doing?
- What are all the possible application states?
  New coders frequently focus on the first question, because its a prerequisite for the second one. However as you gain more experience (and fix more bugs), the second question becomes more important. One of the reasons some engineers fall in love with functional programming is because it eliminates most of the ambiguity with regards to the second question. However I don't see functional programming suddenly having a watershed moment and being adopted everywhere in the very near future. (at least not by apple or google). Swift and Kotlin are meant to take a lot of the ambiguity of the second question out. Unknown whether it is a sufficient majority as to make a comprehensibility measurement unnecessary or not.

> A. Measurement Theory Base

Skipping this as I am still not concerned with a theoretical foundation. A comprehensibility measurement is an attempt to map the work done in the mind of practioners, and attempting to model that with rigorous mathematical definitions probably won't be useful. (my model for comprehension vs decoding notwithstanding)

> suggest that metrics should be sen- sitive to externally observable differences in the development environment, and must also correspond to intuitive notions about the characteristic differences between the software ar- tifacts being measured

This is exactly what I want to build

> Property 1) Noncoarseness: GivenaclassPandametricp another class Q can always be found such that: p(P)# p(Q). This implies that not every class can have the same value for a metric, otherwise it has lost its value as a measurement.
> Property 2) Nonuniqueness (Notion of Equivalence): There can exist distinct classes P and Q such that p(P)= /L(Q). This implies that two classes can have the same metric value, i.e., the two classes are equally complex.
> Property 3 ) Design Details are Important: Given two class designs, P and Q , which provide the same functionality, does not imply that p(P)= p(Q). The specifics of the class must influence the metric value. The intuition behind Property 3 is that even though two class designs perform the same function, the details of the design matter in determining the metric for the class.
> Property 4 ) Monotonicity: For all classes P and U,the following must hold: p(P)5 p(P+c))and p(Q) 5 p( P+Q) where P +Q implies combination of P and QI0. This implies that the metric for the combination of two classes can never be less than the metric for either of the component classes.
> Property 5 ) Nonequivalence of Interaction: 3 P , 3 Q , 3 R , such that p(P)=p(Q)doesnotimplythaty(P+R)=p(Q+R). This suggests that interaction between P and R can be different than interaction between Q and R resulting in different complexity values for P +R and Q +R.
> Property 6 ) Interaction Increases Complexity: 3Pand3Q such that: P(P)+/4Q)< PL(P+Q) The principle behind this property is that when two classes are combined, the interaction between classes can increase the complexity metric value.

These are interesting because they indicate what would make a metric valuable. Furthermore, they follow my intuition, but they actually do have some basic mathematical foundation.

> The inheritance tree is “full”, i.e., there is a root, intermediate nodes and leaves. This assumption merely states that an application does not consist only of stand-alone classes; there is some use of subclassing.”

The entire article is couched in the traditional "classes as real objects" type of OO design.

> Metric 1: Weighted Methods Per Class (WMC)

This is basically lines of code.

> Metric 2: Depth of Inheritance Tree (DIT)

I prefer composition personally, but I would want to see what other engineers feel about this.

> Metric3: Number of Children (NOC)
> Definition: NOC = number of immediate subclasses subordi- nated to a class in the class hierarchy.

This does not feel that interesting. However this is likely my exerience talking.

> Metric 4: Coupling between object classes (CBO)

This should actually be pretty easy to implement.

> Metric 5: Response For a Class (UFC)

I believe this measures the number of other methods that are called by a class. For instance:

```
class Foo {
  Baz mBaz;
  void bar() {
    mBaz.fooBar();
  }
}
```

> Metric 6: Lack of Cohesion in Methods (LCOM)

This one is interesting. I might actually have to figure out all the (set theory?).

> 2. intuitive appeal to practitioners and managers in organizations and 3) ease of automated collection

> Failing to meet Property 6 implies that a complexity metric could increase, rather than reduce, if a class is divided into more classes.

This is part of the reason why we need to be careful about recommendations. I think the author actually gets this wrong in the following paragraph:

> Therefore, satisfying Property 6 may not be an essential feature for 00 software design complexity metrics.

I would assume that a software metric should be able to say "1 complicated class is more/less complicated than 2 interacting classes"

> Designers may tend to keep the inheritance hierarchies shallow, forsaking reusability through inheritance for simplicity of understanding.

Avoid subclassing!

> Another demonstrable use of these metrics is in uncovering possible design flaws or violations of design philosophy.

This is what I am hoping a comprehensibility metric will be able to do.

> Using several of the metrics together can help managers and senior designers, who may be unable to review design materials for the entire application, to exercise some mea- sure of architectural control over the evolution of an 00 application.

> It is often noted that 00 may hold some of the solutions to the software crisis.

CRISIS?!?!?!?!

## Comments on “A Metrics Suite for Object Oriented Design”

> We believe that the ad hoc approach that has characterized conventional software metrics work must be avoided to enable progress to be made on the more challenging problem of developing 00 metrics.

In order for software metrics to be accepted by academia, it needs to be standardized, repeatable, and scientifically rigorous. This is not my intention at all. Individual metrics ought to reflect the choices of craft by the architect(s) who are defining or adopting them.

> To count methods, we must answer the fundamental question, “Does a method belong only to the class that defines it explicitly or does it also belong to every class that inherits it directly or indirectly?’

IMO the answer is "whatever feels right" to the people who are authoring the metric and adopting it. It is the tyrrany of intuition. Unless the answer folds into how most engineers feel about code, it will be rejected. In order to make sure that the answer to that question is sufficiently well grounded, it would need to be run on a group of similar classes and reviewed and refined by the authors. A metric that focuses on comprehension reflects memory and familiarity, which do not have absolute values.

> We do not doubt that CK have resolved, to their own satisfaction, many of the points we raise...

A comprehension metric MUST be opinionated (although the satisfaction this line refers to is more scientific rigor, etc)

## Towards Validating Prediction Systems for Process Understandability: Measuring Process Understandability

https://ieeexplore.ieee.org/document/5204871

J. Melcher and D. Seese, “Process measurement: Insights from software measurement on measuring process complexity, quality and performance,” Universitat Karlsruhe (TH), ¨Institut AIFB, Research Report, 2008, http://digbib.ubka.uni-karlsruhe.de/volltexte/1000009225.

> Mendling et al. state that “we know surprisingly little about the act of modeling and which factors contribute to a ‘good’ process model in terms of human understandability” [2, p. 48].

I think this is wide open territory.

# Automatically Assessing Code Understandability

https://ieeexplore.ieee.org/stamp/stamp.jsp?tp=&arnumber=8651396

> Developers spend most of their time (∼70%) understanding code [1].

:o
