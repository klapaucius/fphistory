History of the Application and Evaluation of Functional Programming
=====

[github](https://github.com/klapaucius/fphistory)  
[telegram](https://t.me/hateHaskellers)   
[support the project](https://boosty.to/fphistory/donate)   

- [History of the Application and Evaluation of Functional Programming](#history-of-the-application-and-evaluation-of-functional-programming)
- [What was when functional programming was not?](#what-was-when-functional-programming-was-not)
  - [_What_ was not?](#what-was-not)


What was when functional programming was not?
=============================================

_What_ was not?
-------------

> Functional programming is an engineering branch of constructive mathematics.  
>              Oleg Nizhnikov.  

We do not aim to define functional programming. However, we are compelled to establish practical boundaries for our study — to choose the history of _what exactly_ we are writing about and to focus on something manageable.  
Many definitions of functional programming are impractical from this perspective. The history of languages with first-class functions today is virtually synonymous with the history of programming languages. Even the few languages that still lack them — such as C++ or Rust — are historically connected in various ways to languages that do have first-class functions.   
Similarly unworkable is the less vast but still unwieldy group of languages historically regarded as functional, which is often the focus of those writing about history of functional programming.   
The main reason this definition of functional languages does not suit us is that this group includes Lisp. And we do not want to write a history of Lisp. Primarily because Lisp’s history is too monumental a topic to allow room for the histories of other languages in this traditional group. Moreover, there is a modern complication that did not exist when the conventional list of functional languages was formed: Lisp is now a typical example of a broad category of languages that were not functional at their inception but became so over time. Just like Java, Lisp had first-class functions added to it. Writing a history of Lisp's functionalization would require comparing it with other languages that underwent the same process — that is, nearly all modern programming languages.   
We would like to set ourselves a realistic goal: to focus on a narrower definition of functional languages and explore their history in greater depth than would be possible if we covered all languages.   
To narrow down our selection, we will add several additional features to first-class functions. Parametric polymorphism and type inference (reconstruction) significantly reduce the scope of our study, though not enough. Therefore, we will also include algebraic data types and pattern matching. This last feature, finally, gives us a reasonably sized family of languages.
Unfortunately, this combination of features appears rather arbitrary. Furthermore, if algebraic data types and pattern matching ever become as ubiquitous as first-class functions (we wouldn’t bet on it), the problem of an all-encompassing language history will return to haunt our successors — if we have any.
This set of language features may seem arbitrary, but we did not invent the idea of grouping languages by these traits. Languages with this combination are sometimes called "ML-like." However, there is little consensus on which languages qualify as ML-like. Not all MLs are particularly similar to other MLs, let alone non-MLs. Worse, not all MLs even have the features listed — a fact perhaps less widely known.  
Let us try to identify the first language with these features and define the family around it. The good news: such a language exists—Hope. As far as we know, no one has independently reinvented this exact combination of features. Hope emerged as a "fusion" of languages, each of which had an incomplete set of the features we are interested in. Bad news: not all languages whose history we wish to write descend from Hope. Thus, our hopes for "Hope-like languages" are dashed, just as they were for "ML-like" ones — and for the same reasons.   
"Fusion" is probably not the best perspective here. Relationships between languages do not neatly form convenient trees or graphs. It is more accurate to speak of a group of languages that, through their evolution, borrowed missing features from one another to complete our defining set. Hope was simply the first complete result of this process, which we will refer to as "Hopification." ML did not undergo this process as a single language. At least three separate languages with "ML" in their names did.   
At the time, interactions between languages, projects, and their creators would have been difficult if the participants were geographically distant. But they were not. The research programme whose history we are writing began in Edinburgh and the nearby town of St Andrews. Finally, we have found suitable boundaries — albeit geographic ones, which are not ideal, but they are what we have.   
Nearly all languages descended from the original group of the Edinburgh research programme retained the discussed features. Certainly, the relatively popular and widely used languages that descended from them still possess these characteristics. If we step further back to examine their ancestors, such uniformity disappears.  
We are writing the history of the "Edinburgh Research Programme." But that name is a bit too long, so going forward, we will usually refer to the group of languages we have chosen to study as simply "functional languages"—just as our esteemed predecessors did when writing about the history of functional programming. In this sense, our work is no different from other historical accounts of functional programming. But in what ways _is_ it different?   

