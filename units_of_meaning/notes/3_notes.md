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
