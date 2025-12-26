History of the Application and Evaluation of Functional Programming
=====

- [What was when functional programming was not?](#what-was-when-functional-programming-was-not)
  - [_What_ was not?](#what-was-not)
  - [What is the purpose of this work, and how does it differ from others](#what-is-the-purpose-of-this-work-and-how-does-it-differ-from-others)
    - [Cryptolambdian](#cryptolambdian)
    - [Phanerolambdian](#phanerolambdian)
  - [Lambda the Ultimate Misunderstanding](#lambda-the-ultimate-misunderstanding)
    - [John McCarthy](#john-mccarthy)
    - [Not a lot of silly parentheses (for now)](#not-a-lot-of-silly-parentheses-for-now)
    - [LAMBDA does not construct a function](#lambda-does-not-construct-a-function)
    - [THE GARBAGE COLLECTOR HAS BEEN CALLED](#the-garbage-collector-has-been-called)
    - [Core War](#core-war)
  - [REFERENCES](#references)

What was when functional programming was not?
=============================================

_What_ was not?
-------------

> Functional programming is an engineering branch of constructive mathematics.  
>              Oleg Nizhnikov.  

We do not aim to define functional programming. However, we are compelled to establish practical boundaries for our study - to choose the history of _what exactly_ we are writing about and to focus on something manageable.  
Many definitions of functional programming are impractical from this perspective. The history of languages with first-class functions today is virtually synonymous with the history of programming languages. Even the few languages that still lack them - such as C++ or Rust - are historically connected in various ways to languages that do have first-class functions.   
Similarly unworkable is the less vast but still unwieldy group of languages historically regarded as functional, which is often the focus of those writing about history of functional programming.   
The main reason this definition of functional languages does not suit us is that this group includes Lisp. And we do not want to write a history of Lisp. Primarily because Lisp's history is too monumental a topic to allow room for the histories of other languages in this traditional group. Moreover, there is a modern complication that did not exist when the conventional list of functional languages was formed: Lisp is now a typical example of a broad category of languages that were not functional at their inception but became so over time. Just like Java, Lisp had first-class functions added to it. Writing a history of Lisp's functionalization would require comparing it with other languages that underwent the same process - that is, nearly all modern programming languages.   
We would like to set ourselves a realistic goal: to focus on a narrower definition of functional languages and explore their history in greater depth than would be possible if we covered all languages.   
To narrow down our selection, we will add several additional features to first-class functions. Parametric polymorphism and type inference (reconstruction) significantly reduce the scope of our study, though not enough. Therefore, we will also include algebraic data types and pattern matching. This last feature, finally, gives us a reasonably sized family of languages.
Unfortunately, this combination of features appears rather arbitrary. Furthermore, if algebraic data types and pattern matching ever become as ubiquitous as first-class functions (we wouldn't bet on it), the problem of an all-encompassing language history will return to haunt our successors - if we have any.
This set of language features may seem arbitrary, but we did not invent the idea of grouping languages by these traits. Languages with this combination are sometimes called "ML-like." However, there is little consensus on which languages qualify as ML-like. Not all MLs are particularly similar to other MLs, let alone non-MLs. Worse, not all MLs even have the features listed - a fact perhaps less widely known.  
Let us try to identify the first language with these features and define the family around it. The good news: such a language exists-Hope. As far as we know, no one has independently reinvented this exact combination of features. Hope emerged as a "fusion" of languages, each of which had an incomplete set of the features we are interested in. Bad news: not all languages whose history we wish to write descend from Hope. Thus, our hopes for "Hope-like languages" are dashed, just as they were for "ML-like" ones - and for the same reasons.   
"Fusion" is probably not the best perspective here. Relationships between languages do not neatly form convenient trees or graphs. It is more accurate to speak of a group of languages that, through their evolution, borrowed missing features from one another to complete our defining set. Hope was simply the first complete result of this process, which we will refer to as "Hopification." ML did not undergo this process as a single language. At least three separate languages with "ML" in their names did.   
At the time, interactions between languages, projects, and their creators would have been difficult if the participants were geographically distant. But they were not. The research programme whose history we are writing began in Edinburgh and the nearby town of St Andrews. Finally, we have found suitable boundaries - albeit geographic ones, which are not ideal, but they are what we have.   
Nearly all languages descended from the original group of the Edinburgh research programme retained the discussed features. Certainly, the relatively popular and widely used languages that descended from them still possess these characteristics. If we step further back to examine their ancestors, such uniformity disappears.  
We are writing the history of the "Edinburgh Research Programme." But that name is a bit too long, so going forward, we will usually refer to the group of languages we have chosen to study as simply "functional languages"-just as our esteemed predecessors did when writing about the history of functional programming. In this sense, our work is no different from other historical accounts of functional programming. But in what ways _is_ it different?   

What is the purpose of this work, and how does it differ from others
--------------------------------------------------------------------

> The development of the theory of types that eventually led to the Standard ML type system goes back more than a hundred years.   
> David MacQueen, Robert Harper, and John Reppy. "The history of Standard ML." [^MacQ20]   


It's not that there's a lack of literature on the history of functional programming. There are already general overviews of functional programming [^Huda89] [^Turn12], as well as histories of specific languages or language families [^Huda07] [^MacQ20] [^McCa78] [^Stee96], and biographies of researchers [^Camp85] [^MacQ14]. So why do we need yet another one?  

### Cryptolambdian

When, yet again, gigabytes of memory are insufficient for compiling Haskell code, the question naturally arises: in what _sense_ did functional programming exist in, say, 1973? Unfortunately, materials on the history of functional programming usually don't pay much attention to this. For histories of functional programming, they often contain too little history of _programming_.   
We don't aim to define "programming," but in this work, we assume it's the process of writing programs. And our great predecessors, in their works on the history of functional programming, don't particularly like to write about what programs resulted from this process.   
Worse, programming historians often venture so far back that it's questionable whether "programming" existed at all in those periods.   
For example, MacQueen, Harper, and Reppy start the prehistory of Standard ML in 1874 [^MacQ20]. Obviously, functional programming didn't exist in 1874. It's not so obvious whether it existed in 1974. What programs had been written in functional languages by that year? What implementations were available, and for whom? Until what year could functional programming languages be said to exist only in the same sense as in 1874, as notations in books, notebooks, on chalkboards, and so on?   
For example, it's often claimed that ML appeared in 1973, but what exactly happened that year? That year, Robin Milner had the desire to write an interactive theorem prover not in Lisp. Did Milner succeed, and in what year? What part of the interactive theorem prover was written in ML? How many lines of code did it have? Who wrote an interactive theorem prover entirely in ML, and how many years later? And who wrote an interactive theorem prover entirely using ML implementation, in turn, itself written in ML, and when? And how many lines of code were in that implementation? Our work will answer these and other questions.   
There's a vast difference - and a significant time gap - between dreaming of functional programming and actually writing a program in a functional language. We believe this perspective is useful for those who don't think history begins and ends with an idea, and that implementing it is trivial and uninteresting.   
It's not that the question of functional language implementation usability is never raised, but our great predecessors weren't particularly interested in it. Some surveys list implementations considered "non-toy," "efficient" [^Huda89], or "fast" [^SPJ87], but their criteria are vague, and you might get a different impression if you knew more about those implementations. We certainly did. In such lists, compilers that compiled themselves and other large projects are mentioned alongside ones that didn't.   
Therefore, we will try to establish what size programs were written using functional languages and what the performance of these programs was.   
All this is mostly a consequence of our great predecessors writing primarily histories of ideas. And they didn't do that because it's easy - tracing the history of ideas is very hard. That's one reason we're not writing a history of ideas. We're writing a history of implementations first, and only then a history of ideas.   
For every idea, one can trace a predecessor, and each one pulls further into the depths of centuries. It's ideas all the way down. That's how a historian of functional programming ends up in 1874. A history of implementations solves that problem neatly - perhaps _too_ neatly.   
Ideas leave fewer traces, and the ones they leave are less convenient for a historian. An implementation (even a failed one) leaves behind different versions of code, notes in it, bug reports, release announcements - evidence of what worked and when.   
Ideas leave behind papers, which might be published years later and "cleaned up" in ways that erase history. The related work section documents the relationships between ideas, but not their history. Influences are often declared, but the "influencing" idea might only be discovered after the "influenced" one has already been reinvented independently.   
Sometimes, an author explicitly states this. For example, Xavier Leroy writes that he reinvented some ideas from Krivine's machine without knowing about it and only added citations after other people pointed out the similarity. The creator of Chez Scheme independently rediscovered some ideas found in VAX ML, while others were directly borrowed. But not everyone feels the need to disclose this.   
Attempts to trace the history of ideas are also complicated by the fact that the opinions of language authors about which languages they influenced may not coincide with the opinions of the authors of those languages about which languages influenced them.   
This shouldn't be surprising. Ideas for how to design programming languages often arise independently. Even the Hindley-Milner algorithm - a nontrivial and precisely defined concept - was independently reinvented. But no one has ever independently written two identical compilers.   
It's easier to cite a paper than to reuse compiler code. So, when we write histories of ideas, the graph ends up with too many edges.   
To group implementations into families, we'll use rarer but more reliable connections: shared code, common authors, and bootstrapping one implementation with another.   
Historians of functional programming often face the same challenge we've outlined - how to define the scope of their study. If you're writing a language's history, where do you draw the line? One approach is to define a language by its syntax and semantics - trees or sequences of symbols that can be compared. This enables building trees and graphs that show how programming languages evolved and diverged. Of course, that level of analysis is very demanding. We'll analyze not the syntax/semantics descriptions (the most suitable targets for such analysis), but the next best thing - actual implementations in functional languages.   
Unfortunately, our great predecessors often chose simpler criteria. Names. If anything can prevent a historian from endlessly digging into the past, it's names. But using names to decide where one language ends and another begins may not be a great solution.   
Some authors love a name so much that they keep using it for ever-new and increasingly unrelated things. Syntaxes of many FP languages in the '80s resembled each other more than they resembled their own earlier versions from the '70s, despite sharing names. Fortunately, something was first called "ML" a very long time ago, and there are no obstacles to starting the history of ML from its beginning, or even long before its beginning.   
Unfortunately, many authors use different names for the same thing. The first Haskell compiler was created in just a few months from a non-Haskell compiler. This clearly indicates that a great deal of work had already been done, which can justifiably be considered work towards creating Haskell. Three of the first five Haskell compilers were developed for many years before the idea to design this language even emerged. Alas, non-Haskell wasn't called "Haskell," so nothing could be done - in the history of Haskell [^Huda07], no more than a few lines could be devoted to this.   
The authors of Haskell chose a different non-Haskell as the basis for the first Haskell Report. And this non-Haskell resembles Haskell 1.0 more than ML in '82 resembled ML in '83. But sorry - it wasn't called "Haskell," so our great predecessors can't write its history.   
We can.   

### Phanerolambdian

What is our history of implementations? Primarily, it's a history of compilers for general-purpose machines, and to a lesser extent of interpreters and specialized hardware implementations. We chose compilers for conventional machines because they're the most successful implementation path for functional languages: they've survived to this day (unlike special hardware), they've been used for substantial programs (unlike many interpreters and hardware), more is simply known about them; there is something to write about. Compilers are complex enough that there aren't _too_ many of them - unlike interpreters. So we end up with a manageable set of fairly detailed histories, rather than endless lists with terse descriptions.   
Of course, we'll touch on interpreter and hardware history where it's needed to understand compiler history, but we don't aim for completeness there.   
Still, the history of implementations has its problems. The history of programming is not very eventful during times when functional programmers weren't writing many non-trivial programs. What are non-trivial programs? We'll consider such programs to be the code of a compiler for a functional language or the code of a theorem prover.   
This may not seem like a high bar, but for functional programming it definitely is. Frankly, it's not like we had much choice in setting this bar. Outside of micro-benchmark speeds and how fast a compiler written in a functional language compiles, there isn't much information.   
About some implementations, one can read that Fibonacci numbers are computed not much slower than in C, and that a compiler written in the language compiles something in an acceptable time. About others, one can read that no compiler is written in them, and performance is not that important anyway.   
Since the history of programming and working implementations is heavily skewed towards the end of the history of ideas, it doesn't fit well with the typical "progress" and "formation" structure of idea histories, where everything starts with Lisp, continues with strict functional languages, and concludes with lazy ones. Instead, we have a period where nothing worked, followed by a period where everything did - all at once.   
Our history is structured by the lifecycle of implementations, or more precisely, their families. We will begin with implementations whose developers planned or even attempted to create a functional language compiler from a non-functional language compiler, or to turn a non-compiler functional system into a compiler. For a long time, such plans were either not implemented at all, or attempts were made but were unsuccessful. We will discuss this period in Part Zero of our history.   
When several such attempts finally succeeded, the first part of the history began. In it, we will discuss the first compilers for functional languages that do not yet resemble those we defined above as the functional languages whose history we are writing.   
In the second part, we will describe how these implementations were transformed into implementations of precisely such languages - the languages of the Edinburgh research programme, whose history we are writing. And about new implementations that were implementations of such languages from the very beginning.   
In the third part, we will discuss the next period, in which these implementations were used to write the first serious programs: provers and a new generation of functional language compilers. This is when functional programming finally _arrives_.   
The history of implementations poses a question for us, the answer to which requires considering the history of conventional machines and operating systems as well. Which, of course, we will also describe without any claim to completeness. If the idea of functional programming, as our great predecessors discovered, existed for as long as programming itself, or even longer, then why wasn't there functional programming? When could it have already appeared? And what existed when functional programming did not?   


Lambda the Ultimate Misunderstanding
------------------------------------

Why was there no functional programming? Because there were no usable implementations and no machines suitable for running such implementations.

And when the past, in which functional programming did not exist, was replaced by a present in which functional programming exists (for now), this present was unevenly distributed.

By choosing a narrower definition of a functional language, we also limited the resources of the resulting research program.

The Edinburgh research program brought together a relatively small number of researchers, so it is quite natural to expect that they used many of the developments of other research programs—developments that, as it happened, were also useful for implementing the functional languages of the Edinburgh program.

And in order to build on a foundation already laid by researchers and implementers, to take advantage of the successes of an earlier and richer programme, there was a suitable candidate: LISP.

### John McCarthy

> the FORTRAN idea of writing programs algebraically was attractive.   
> McCarthy J. History of LISP [^McCa78]   

John McCarthy received a bachelor’s degree in mathematics from the California Institute of Technology in 1948, and in 1949 he accidentally walked into a symposium on cybernetics held at that university. There he heard a talk by von Neumann and became interested in what he would later call “artificial intelligence” [^Stoy79].

McCarthy received his PhD in mathematics from Princeton in 1951 and taught mathematics first at Princeton, then at Stanford, and finally at Dartmouth.

McCarthy was a mathematician, but when, no later than 1955, he began thinking about a programming language for artificial intelligence, he described it not as a mathematical notation like the lambda calculus with extensions. He described it by drawing parallels with natural language. This is a fairly common view of programming languages among their authors—but probably not among the authors of the languages whose history we are writing.

However, in 1955, they didn't know how to make programming languages that looked like natural languages (whatever that meant), nor languages based on mathematical notation. But soon, some ideas appeared.

In 1956 McCarthy organized the famous Dartmouth Summer Research Project on Artificial Intelligence. At this seminar McCarthy encountered the first building block of the language of his dreams—lists. List processing existed in the language of Allen Newell and Herbert A. Simon, IPL (Information Processing Language).

But IPL itself did not make a very good impression on McCarthy; it seemed too low-level. And what language did he consider high-level enough? FORTRAN [^Stoy84].

McCarthy was impressed by the fact that in Fortran one could use expressions like arithmetic operations and nested function calls.

He believed that to get a high-level language for working with lists, one needed to add list-processing functions to Fortran. And already in 1957, McCarthy had the opportunity to add the missing piece—lists—to the cutting-edge high-level Fortran. In that year, N. Rochester, who was then a department head at one of IBM's research centers, decided to realize Marvin Minsky's idea: a program for proving geometric theorems.

McCarthy became a consultant on this project. IPL was originally intended to be used for the implementation, but McCarthy managed to prevent that. Instead of writing their own IPL implementation for the IBM 704 machines, McCarthy advised extending FORTRAN with list-processing facilities. IBM followed this advice, creating what later became FLPL (FORTRAN List Processing Language).

At first, it was difficult for the programmers implementing the extensions—and even for McCarthy himself—to think of list constructors as functions. Functions were things that took and returned numbers, not some sort of constructions in memory. And in general it was hard to see lists as an abstraction behind operations on addresses. As a result, procedures for constructing lists initially did not compose into nested expressions natural for functional languages.

These difficulties were overcome first not by McCarthy, but by programmers Herbert Gelernter and Carl L. Gerberich, who decided that functions could return not only mathematical objects but also “lists,” for which one could perhaps invent strict definitions and laws—but programmers managed without them. McCarthy would later return to those definitions and laws.

This seems to have been the end of these programmers’ contribution to the creation of functional programming. But in that same year, 1957, McCarthy met a programmer whose contribution was still to come.

Steven Russell studied mathematics at Dartmouth, but decided he did not particularly like mathematics. Programming interested him much more, so he abandoned mathematics and began working at the university as a programmer. But in 1957 he wrote nothing for McCarthy other than an assembler manual.

Thanks to contacts established during the Dartmouth seminar, between September 1957 and April 1958 McCarthy worked at MIT on a chess program. He wrote it in FORTRAN and decided that although the expressions available in FORTRAN were good, they were not enough. What FORTRAN lacked was a *conditional* expression.

There were no plans to add such an expression to FORTRAN at that time, but McCarthy was soon presented with the opportunity to work on the creation of a new high-level language from scratch.

At the end of 1957, J. Carr III formed the ACM committee on programming languages. The organizers were looking for participants, and McCarthy became one of them. The committee’s first meeting took place in January 1958, and in April of the same year a subcommittee was formed to work on an international algorithmic language. The members of this subcommittee were J. Backus, J. McCarthy, A. Perlis, and W. Turanski. During April and May of 1958 they wrote “Proposal for a Programming Language.”

McCarthy’s conditional expressions made it into this document—albeit in an unfinished and overcomplicated form. They were not expressions returning values, but producers of labels for `GOTO`. This, of course, made them far less attractive than modern conditionals. Why they ended up this way is understandable: in the international algorithmic language, returning anything nontrivial was not handled particularly well. But more on that later.

Conditional expressions were not McCarthy’s only proposal for the international algorithmic language, but the others were rejected already by the subcommittee.

In June, a meeting of the subcommittee with their European colleagues took place in Zurich. Conditional expressions were rejected there as well.

McCarthy recalls that the conditional expressions were too unusual and that he explained them poorly. This seems like a harbinger of many problems in the history of functional languages—because all their other components are even harder to explain.

In May 1958 McCarthy gave a guest lecture for Minsky’s course. James R. Slagle, who attended McCarthy’s lecture, took notes on how McCarthy described his dream language: "FORTRAN plus variable functions, composite functions (Church lambda), multiple functions, several valued functions of several variables, direct sum of functions, label portion of program with facility to make symbolic substitutions therein...".

Conceptualizing the language as “FORTRAN with lambdas,” rather than “lambda calculus with practical extensions,” again looks more like the reasoning of typical programming language authors than that of the authors of the languages whose history we are writing.

In the summer of 1958 McCarthy worked at IBM on a program for symbolic differentiation. McCarthy did not consider recursion important until he wrote the differentiation program—it was obviously recursive. Working on this program strengthened his conviction that a programming language must have higher-order functions. He came up with the idea of such a function: `maplist`.

That same summer, in early June 1958, McCarthy also tried once more to challenge the decisions of the Zurich meeting. He proposed adding functional variables, lambdas, function composition, arithmetic operations on functions from numbers to numbers, and even standard higher-order functions for differentiation and integration to IAL (International Algorithmic Language). To no avail.

It now became obvious to McCarthy that he would not be able to add all the features needed to turn FORTRAN or IAL into a language for programming artificial intelligence. McCarthy needed to create his own language. And soon he had such an opportunity.

### Not a lot of silly parentheses (for now)

> Without any doubt it is hard to imagine that this program could ever run correctly. However, McCarthy himself had this feeling, too.
> Herbert Stoyan. Early LISP history [^Stoy84]

In the summer of 1958 McCarthy met a student from the University of Michigan who was looking for a programming job—Klim Maling. McCarthy hired Russell and Maling for his new joint project with Minsky in September 1958. As part of this project, the first LISP was designed and implemented.

What did McCarthy end up with after combining all the components of his language for programming artificial intelligence? In the very first report [^McCa58] of the MIT AI Laboratory, we see code with lists, conditional expressions, recursion, FORTRAN with its `goto` and mutability, as well as something resembling higher-order functions—but looking rather strange. The function `maplist` is applied like this:

```
maplist(cdr(J),K,diff(K))
```

and like this:

```
maplist (cdr(J),L,(L = K → diff(K), L ≠ K → copy (L)))
```

which means roughly:

```haskell
maplist (tail j) (\l -> if l == k then diff l else copy l)
```

but the “lambda” is somehow passed to `maplist` via two parameters: the bound variable separately and the body of the lambda separately. How does that even work? You need to know which variables are bound and which are free at the point of function construction.
But such oddities did not last long. In later reports, `map` looks like this:

```
maplist(L,f)=(L=0→0,1→consls(f(L),maplist(cdr(L),f)))
```

and is applied as:

```
maplist (cdr(J),λ(L,(L = K → diff(L), L ≠ K → copy (L))))
```

which is perfectly normal.

In McCarthy’s article “Recursive functions of symbolic expressions and their computation by machine” [^McCa60], Lisp looks like this:

```haskell
maplist[x; f] = [null[x] → NIL;
                 T → cons[f[x]; maplist[cdr[x]; f]]]

maplist[(1,2,3); λ[[x]; x + y]]
```

This `maplist` differs from the more familiar `map` function in the standard libraries of today’s functional languages in that the function passed to it is applied not to the elements of the list but to its tails. But this is not a fundamental difference.

Naturally, this article made an indelible impression on future authors and implementers of functional languages.

Does this Lisp look unlike modern Lisp? It does not resemble the Lisp that actually existed at the time either. This is pseudocode for articles about Lisp—more or less resembling M-expressions, which looked like this [^LISP61]:

```
MAPCON(L,F)=
    (L=0 YIELDS 0,
     1 YIELDS NCONC(F(L),MAPCON(CDR(L),F)))
```

M-expressions were intended to be implemented, but nobody knew how. No one in McCarthy’s group knew how to write a compiler. The example of FORTRAN was not particularly inspiring—it took 30 man-years to write its compiler, which was quite a lot for that time, and especially for McCarthy’s group. Clearly, creating your own language has disadvantages compared to adding features to existing ones.

So M-expressions remained only pseudocode—not in articles, but in comments to real code written in assembler and Lisp. And the real Lisp code—S-expressions—looked [^McCa62] much the same as they do today:

```lisp
(MAPLIST (LAMBDA (X FN) (COND
      ((NULL X) NIL)
      (T (CONS (FN X) (MAPLIST (CDR X) FN))))))
```

But for those who wanted to use Lisp implementations to create implementations of functional languages in the narrower sense, this was not a problem. Translating code into S-expressions is even easier. The main thing was that such implementations existed—and they did.

In 1958, to gain experience with translation, programmers Russell and Maling began rewriting simple programs from proto-Lisp into IBM assembler. By early April of the following year, they had rewritten 20 functions. McCarthy wrote programs in the M-expression language, and the two programmers wrote the corresponding assembler code.

The naive Lisp interpreter was initially a specification in M-expressions, and Russell, on his own initiative, made this specification executable. Naturally, the first specification executed incorrectly, but after several iterations of writing new specifications and manually translating them, the interpreter began to work.

For writing real programs, a naive interpreter is not enough, but more serious implementations were not long in coming.

No later than April 1959, Klim Maling began writing a Lisp compiler in Lisp, but the project was abandoned. Lisp programmers considered that a compiler written in assembly was obviously more practical.

Robert Brayton and David Park, who assisted him, wrote the LISP 1 compiler in assembly. This compiler became operational in January 1960. The code it generated ran 50 times faster than the interpreter [^Stoy79].

But in 1960 Brayton left MIT, and without him the Lisp programmers could no longer understand or develop the compiler [^Blai70]. McCarthy briefly described this experience as “unsuccessful” [^McCa78].

So the Lisp programmers decided to try writing a Lisp compiler in Lisp after all. This experiment ended in success, which became clear no later than August 1962. Timothy P. Hart and Michael Levin, better known for their other work, wrote the LISP 1.5 compiler, which is considered the first compiler to compile itself [^Hart62] [^McCa62]. The Lisp programmers were able to develop this Lisp-in-Lisp compiler.

The Hart and Levin compiler produced code that ran 40 times faster than the interpreter [^Hart62], or from 10 to 100 times faster depending on the program [^McCa62]. Depending on which properties of the program? A good question.

Bootstrapping took only 5 minutes, despite the fact that most of the time most of the compiler was still being interpreted.

McCarthy writes that the speed of compiled Lisp code is 10–100 times slower than FORTRAN code on numerical tasks. But there is no comparison with list processing written in a more traditional programming language, such as FORTRAN with appropriate extensions. Such a comparison would have been more interesting.

However, a compiler is a real application, so it can be concluded that Lisp programming existed in 1962.

And if already in 1962—or even in 1960, if you were brave enough—it was possible to compile a language with first-class functions, then functional programming in the broad sense existed from the early 1960s. And for functional programming in the narrow sense, on the languages of the Edinburgh research program, it remained only to invent and implement pattern matching and parametric polymorphism. After all, Lisp is a functional language with first-class functions, right?


That’s what David Turner, an important hero of our story, thought when he began studying Lisp in 1972. But he quickly noticed that the code was not doing what he would expect from a language that has lambda [^Turn12]. Turner read the documentation [^McCa62] and realized that...
### LAMBDA does not construct a function

> We suspect that McCarthy simply had forgotten the functional arguments – a mistake of lasting importance.
> Herbert Stoyan. Early LISP history [^Stoy84]

The problem was first discovered in 1959 by James Slagle—the same one who took notes on "Fortran with lambdas." Slagle worked with the first Lisp implementation. In his history of Lisp [^McCa78], McCarthy even gives pseudocode corresponding to Slagle’s code, while debugging which Lisp programmers first realized that something was not working as expected:

```haskell
testr[x, p, f, u] <- if p[x] then f[x] else if atom[x] then u[] else
        testr[cdr[x], p, f, λ:testr[car[x], p, f, u]].
```

Yes, as was customary in the first couple of decades of Lisp’s existence, code examples were usually pseudocode. After all, you wouldn’t publish all those parentheses in a paper.

Slagle thought he had written something like this:

```haskell
data Lisp = Atom String | Cons Lisp Lisp deriving (Show, Eq)

testr x p f u | p x = f x
testr (Atom _) p f u = u ()
testr (Cons h t) p f u = testr t p f $ \() -> testr h p f u
```

but in reality he had written something more like this:

```haskell
testr x p f u | p x = f x
testr h@(Atom _) p f u = u h p f u -- <==
testr (Cons h t) p f u = testr t p f testr -- <==
```

But why? Slagle tried to find out from the programmers, but they did not know why. So Slagle and the programmers turned to McCarthy. But that did not help either—at least not immediately. Let us give the floor to McCarthy himself [^Stoy79]:

“…naturally he complained. And I never understood the complaint very well, namely, I said: ‘oh, there must be a bug somewhere, fix it!’ And Steve Russell and Dan Edwards said, there is a fundamental difficulty and I said, there can’t be, fix it, and eventually they fixed it and there was something they called the funarg device. He tried to explain it to me but I was distracted or something and I didn’t pay much attention so I didn’t really learn what the funarg thing did until really quite a few years later.”

What can one say? This is rather unexpected.

In his talks and articles on the history of Lisp in the 1970s, McCarthy said that he had not fully read Church’s work on the lambda calculus, and that what he had read he had not fully understood. Lisp historian Herbert Stoyan initially thought this was a joke [^Stoy79], but later reconstructed McCarthy’s path to mastering lambda [^Stoy84].

Remember the strange higher-order functions from the first report? When that report came out in the fall of 1958, McCarthy had only a vague idea of what lambda was. After unsuccessful attempts to write such a `maplist` in assembly, McCarthy decided to read about lambdas and entered the state he himself described as “not fully read, not fully understood.” But that was already enough for the appearance of HOFs in later reports to stop looking suspicious.

Stoyan finds it strange that McCarthy had only a vague understanding of lambda, yet months earlier spoke of dreaming of FORTRAN with lambdas and recommended adding them to the international algorithmic language. Stoyan suggests something might be wrong with the dates. But if the code from the first report was written earlier, it is still strange that no one noticed the suspicious HOFs.

Stoyan discussed this with McCarthy, and McCarthy himself was surprised, certain that only an unsuccessful attempt to implement such a `maplist` led him to using lambda. Why, then, did he recommend adding lambda to other languages long before that moment?

We are not inclined to treat this as a mystery and see no reason why one should not recommend that other programming language designers pay attention to lambdas, even if one only knows of their existence and does not yet properly understand them before attempting implementation.

So, the obviously incorrect lambda first became non-obviously incorrect. What was wrong with this one?

A not-so-obviously wrong lambda is a metaprogramming tool. It creates a description of function code that the interpreter can execute using the environment at the call site. The function code description has a free variable named `x`; the interpreter goes through a list of pairs and looks for the first key `"x"`. And which pair will be found first when executing Slagle's code? The one added during the function call, corresponding to one of its parameters. This is so-called "dynamic scope."

Functional programming, however, requires lexical scope. Lambda must construct a closure over the environment at the point where the lambda expression is evaluated. The Haskell code above works because closures form a stack for traversing the tree. But the Lisp interpreter did not construct closures. Closures as an implementation technique for functional languages had not yet been invented. The interpreter was looking in the wrong list of pairs—and it did not even have the right one.

Today one might assume that a metaprogramming “lambda” makes sense in Lisp, known for its use of metaprogramming. But “lambda” as a code fragment and an object of metaprogramming, rather than as a function, was not the result of careful design. Stoyan came to this conclusion by studying the process of its emergence. McCarthy wrote an interpreter for S-expressions of proto-Lisp in M-pseudocode. Russell or another programmer tried to rewrite it in assembly, discovering errors. The process repeated. Stoyan believes that during these iterations, at some point McCarthy simply forgot about functional arguments. And one of the programmers—most likely Russell—invented the metaprogramming “lambda” when he could not find a corresponding implementation in the pseudocode specification written by McCarthy. It seems that not all components of the language for programming artificial intelligence were equally important. Conditional expressions occupied McCarthy more than first-class functions.

It turned out that Russell most likely created the problem with the non-obviously incorrect lambda. But he also fixed it in the same year, 1959—with some help from Patrick Fischer. Russell added closures to Lisp: a pair of code and the very list in which linear search by variable name finds the correct variable from the environment at the point where the closure is constructed. At the point of lambda application, this list is added to the front of the environment list at the application site. After that, the interpreter interprets the lambda code as Slagle—or anyone else familiar with lambda calculus—would expect.

Technically, the error was not fixed. The error was classified as a feature, and the fix as another feature that one could choose not to use. The default scoping did not change, and closure construction was made explicit.

It is not entirely clear why the default behavior was not changed. It was not as if enough Lisp code had been written by then to worry about backward compatibility. Perhaps performance was the issue. Perhaps the fix was not considered important. Russell could not explain either the solution or the problem even to McCarthy, according to McCarthy himself.

Fortunately, for someone translating a functional language into Lisp, this does not matter: one can explicitly specify that a closure should be constructed for a lambda. And so—is the problem solved? Alas, no.

Unfortunately, this explicit construction of closures is only one manifestation of the indifference of Lisp programmers of that time to functional programming. Another, more important issue for compiling functional languages by translation into Lisp, was that advances in Lisp compilation and performance optimization were usually not applied to these closures.

Remember the caveat that the compiler compiles different Lisp code with varying degrees of success? Lambdas are precisely such code. In the case of selected functions like `map` and a known lambda, an advanced compiler can inline both, solving both the scoping and performance problems. But in the case of an unknown function, as in Slagle’s example, compilation will not occur at all. The lambda code will be interpreted, and the interpreter will traverse a singly linked list of pairs in search of a string with the desired name. This is not merely an explanation of semantics—it is, for the time being, the actual implementation.

Instead of working on an implementation that would execute Slagle’s code better, Lisp programmers abandoned functions that handled errors by calling a passed-in handler, in favor of functions that reported errors by returning the empty list.

All right—perhaps Lisp programmers did not yet want to create a practical implementation of first-class functions themselves. Still, Lisp implementations could be useful to a functional language implementer. Functional language implementers can implement functions by themselves, provided there is garbage collection. And Lisp was the first language with garbage collection.

### THE GARBAGE COLLECTOR HAS BEEN CALLED

> Once we decided on garbage collection, its actual implementation could be postponed, because only toy examples were being done.
> McCarthy J. History of LISP [^McCa78]

Early Lisp programmers did not want to manage memory manually as in IPL, and chose between reference counting and garbage collection. They chose garbage collection because they wanted a `cons` cell to fit into a single word. On the IBM 704, this was 36 bits. An address was 15 bits. Two groups of three bits were too small for a reference count [^McCa78].

This was a rather fortunate coincidence for functional programming, which often creates cyclic references. But this fortunate coincidence was probably not critical for the emergence of functional languages. For example, the authors of SIMULA eventually abandoned reference counting in favor of garbage collection because they conducted experiments and compared the performance of reference counting combined with garbage collection for collecting heap cycles with that of a compacting garbage collector. At least, they recall this [^Dahl78]. But perhaps it was still beneficial that Lisp programmers began working on garbage collection earlier.

Having chosen garbage collection over reference counting, Lisp programmers postponed its implementation because they were writing only toy programs for the time being. But they did not postpone it for long. Dan Edwards wrote a garbage collector in June–July 1959 [^Stoy84].

The first public demonstration of Lisp, in 1960 or 1961, also became the first public demonstration of garbage collection—although this was not planned. It didn't trigger during the rehearsal, but the rehearsal took up enough memory that the garbage collector started working during the demonstration and ran for the rest of the time allotted to it, printing statistics [^McCa78]. It is hard to say why Lisp programmers did not want to show off what was, in Turner's opinion [^Turn12], their greatest achievement. But fortunately, everything ended well and they did show it.

In the printed statistics, the collector is already proudly called a garbage collector, but in the first Lisp paper [^McCa60] they are still shy about calling it that. McCarthy is too serious there, but this is compensated by other Lisp programmers in other papers.


McCarthy writes that the "reclamation" process takes "a few seconds." This is true when memory is 8192 words. But by the time of the collector demonstration, it was already 32768 words, and the process took at least four times "a few" seconds. Not great.

The main problem [^Wilk92] with McCarthy's collector: even if almost no live objects remain at the time of collection, the entire heap must still be traversed; the collector's run time depends on the size of the heap.

Proponents of reference counting criticized McCarthy’s method almost from the very beginning [^Coll60] for the fact that the collector’s running time does not depend on how much memory is freed. But the fact that the running time does not depend on how much memory is freed is actually a good thing. What is bad is that the running time depends not only on the number of live objects.

It turns out that memory growth brings not only new opportunities but also new challenges. More time passes before the next collection—time that can accommodate not just a demonstration (but not along with its rehearsal), but some more interesting work. But the break in work also becomes increasingly painful.

Of course, such a view of the problem is entirely unsuitable for functional programming. Functional code allocates enough to quickly fill memory. Functional programming can benefit from memory growth only if collection time does not grow as fast as memory size.

McCarthy's collector has another problem that is very important for functional languages. Since the work of a functional program boils down to allocation to such a significant extent, allocation must be fast. And searching for memory in a free-list is not the fastest way to allocate.

And Lisp programmers thought less about how to make garbage collection more efficient, and more about how to reduce heap allocations, reducing the load on the collector.

Abandoning garbage collection and keeping Lisp as it was was practically impossible. But if one allocates less on the heap, reuses data structures by modifying them in place, one can preserve this illusion of a solution—pushing collection into the future, where perhaps the computation will already be finished and no collection will be needed at all.

Thus, for functional programming and for use as a basis for implementing functional languages, Lisp compilers were not yet suitable.

In the summer of 1962 McCarthy left MIT and went to work at Stanford [^Stoy79]. And however indifferent he may have been to functional programming, the Lisp programmers remaining at MIT seem to have been even more indifferent. This marked the end of the first unsuccessful attempt to implement a functional language.

### Core War

The next page in the history of Lisp began with the arrival of a new computer at MIT. IBM machines were replaced by DEC computers. This decision had serious consequences and requires explanation.

How did it come about that MIT began using PDP-6/10 mainframes instead of the much more popular IBM mainframes, especially considering that Lisp development began on IBM machines? One reason was a delay in the release of IBM’s new line [^Chio2001]. The main reason was that relations between MIT and IBM deteriorated due to a patent dispute [^Stee96] [^Chio2001].

MIT claimed the invention of core memory and demanded IBM pay two cents for every bit. Meanwhile, in 1965, the production of core memory cost IBM 1–3 cents per bit, depending on its speed. IBM was so reluctant to pay that it developed several new types of memory to replace core. None of them were practical or were ready to be practical fast enough. But Jay Wright Forrester, to whom IBM demonstrated its developments, did not know this.

And MIT, mistakenly believing that IBM was about to render their patent worthless, agreed in February 1964 to a one-time payment of $13 million ($134 million in 2025). At the time this was a record patent settlement, but had MIT not been frightened by non-working inventions, it could have obtained much more [^Emer91].

Feeling cheated, MIT decided not to buy new IBM machines.

Why not IBM is clear. But why choose the DEC PDP-10? DEC was founded by MIT alumni, who had also been members of the Tech Model Railroad Club. The trains were controlled by a computer, so McCarthy and Minsky used the club to recruit programmers for the AI Laboratory.

It was there that they found Richard D. Greenblatt, the implementer of Lisp on the new DEC machine.

MIT was not yet offended by DEC’s founders. Not yet.

Another reason was probably the same as before with IBM. IBM donated an IBM 704 to MIT in 1957, and DEC donated a PDP-1 in 1960. And just as MIT later bought newer IBM machines, the AI Laboratory acquired the PDP-6, and then its newer, more reliable and more popular version, the PDP-10 [^Chio2001].

Yet another reason was that the PDP-6/10, in the opinion of Lisp programmers, was well suited for implementing Lisp—because a `cons` cell fit into a single word, and because of instructions needed to implement some new ideas for improving memory management in Lisp.

Lisp programmers even claim that the PDP-6 designers listened to their wishes [^Stee96]. This is not so obvious. For example, the IBM 704 also fits two pointers into a single word, and no one intended to make it a “Lisp machine.” And when Lisp programmers actually designed a computer for Lisp, it had little in common with the PDP-6/10.

Lisp programmers participated in pre-release testing of the PDP-6 in 1964, and Greenblatt’s new Lisp implementation was one of the first programs to run on that computer [^Whit77]. MIT Lisp programmers received the PDP-6 in December 1964 [^Stoy79], and the PDP-10 in 1968.

Since Lisp programmers were not yet particularly interested in functional programming, they could concentrate on improving the non-functional subset, reducing the load on the garbage collector and increasing allocation speed. And in 1966 Greenblatt decided to abandon searching for variable names in a singly linked list and instead use techniques developed by implementers of another language—or rather, McCarthy's first language.

And although McCarthy’s colleagues did not immediately accept his ideas about adding lambdas to the language, that struggle was not yet over. Its implementers had something to borrow not only for anti-functional Lisp programmers. In fact, this language was the second likely candidate to become the basis for the first practical functional language.

*To be continued...*

REFERENCES
----------

[^Abda74]: Abdali, Syed Kamal. "A combinatory logic model of programming languages." PhD diss., University of Wisconsin--Madison, 1974.   
[^Abda76]: Abdali, S. K. (1976). An Abstraction Algorithm for Combinatory Logic. The Journal of Symbolic Logic, 41(1), 222. doi:10.2307/2272961   
[^Abra81]: Harvey Abramson, D. A. Turner, SASL Reference Manual. TM-81-26, October 1981 https://www.cs.ubc.ca/sites/default/files/tr/1981/TM-81-26.pdf   
[^Acke28]: Ackermann, W. (1928). Zum Hilbertschen Aufbau der reellen Zahlen. Mathematische Annalen, 99(1), 118–133. doi:10.1007/bf01459088   
[^Aiel74]: Aiello, Jack Michael. An Investigation of Current Language Support for the Data Requirements of Structured Programming. Massachusetts Institute of Technology, Project MAC, 1974. https://ia802901.us.archive.org/34/items/bitsavers_mitlcstmMI_32305830/MIT-LCS-TM-051_text.pdf   
[^ALGOL71]: AB32.3.3 C, Modals. Algol Bulletin No. 32, May 1971 http://archive.computerhistory.org/resources/text/algol/algol_bulletin/A32/P33.HTM    
[^ALGOL72]: AB33.3.3 IFIP WG2.1 Subcommittee: Maintenance of and Improvements to ALGOL 68, Algol Bulletin No. 33, March 1972 http://archive.computerhistory.org/resources/text/algol/algol_bulletin/A33/P33.HTM   
[^ALGOL72a]: AB34.3.1 Report on the meeting of WG2.1 at Fontainebleau Algol Bulletin No. 34, July 1972 http://archive.computerhistory.org/resources/text/algol/algol_bulletin/A34/P31.HTM   
[^ALGOL72b]: AB34.3.2 Report on considered improvements (Fontainebleau 9), Algol Bulletin No. 34, July 1972 http://archive.computerhistory.org/resources/text/algol/algol_bulletin/A34/P32.HTM   
[^ALGOL73]: AB35.3.1 Further Report on Improvements to ALGOL 68, Algol Bulletin No. 35, March 1973 http://archive.computerhistory.org/resources/text/algol/algol_bulletin/A35/P31.HTM    
[^ALGOL78]: AB42.1.1 Modules and Separate Compilation, Algol Bulletin No. 42, May 1978 http://archive.computerhistory.org/resources/text/algol/algol_bulletin/A42/P11.HTM   
[^ALGOL80]: AB45.4.2 ALGOL 68 Implementations - ALGOL 68C - Release 1, Algol Bulletin No. 45, January 1980 http://archive.computerhistory.org/resources/text/algol/algol_bulletin/A45/P42.HTM   
[^ALGOL81]: AB47.3.3 Survey of viable ALGOL 68 Implementations, Algol Bulletin No. 47, August 1981 http://archive.computerhistory.org/resources/text/algol/algol_bulletin/A47/P33.HTM   
[^Arnb72]: Stefan Arnborg. 1972. Storage administration in a virtual memory Simula system. BIT 12, 2 (Jun 1972), 125–141. doi:10.1007/BF01932808   
[^ATLAS]: London Atlas http://www.chilton-computing.org.uk/acl/technology/atlas/p010.htm   
[^Atki78]: Atkinson, M. P., & Jordan, M. J. (1978). An effective program development environment for BCPL on a small computer. Software: Practice and Experience, 8(3), 265–275. doi:10.1002/spe.4380080304    
[^Augu84]: Lennart Augustsson, A compiler for lazy ML. LFP '84: Proceedings of the 1984 ACM Symposium on LISP and functional programming August 1984 Pages 218–227 doi:10.1145/800055.802038    
[^Augu89]: L. Augustsson, T. Johnsson, The Chalmers Lazy-ML Compiler. In The Computer Journal, Volume 32, Issue 2, 1989, Pages 127–141 DOI:10.1093/comjnl/32.2.127   
[^Augu21]: The Haskell Interlude 02: Lennart Augustsson https://www.buzzsprout.com/1817535/9286902   
[^Baba79]: Babaoglu O, Joy W, Porcar J. Design and implementation of the Berkeley virtual memory extensions to the UNIX operating system. Department of Electrical Engineering and Computer Science, University of California, Berkeley. 1979 Dec 10.   
[^Baba81]: Babaoglu, Özalp and William N. Joy. “Converting a swap-based system to do paging in an architecture lacking page-referenced bits.” TR 81-474 October 1981.   
[^Back59]: J. W. Backus. The Syntax and Semantics of the Proposed International Algebraic Language of the Zurich ACM-GAMM Conference. Proceedings of the International Conference on Information Processing, UNESCO, 1959, pp.125-132. Typewritten preprint.   
[^Back63]: J. W. Backus, F. L. Bauer, J. Green, C. Katz, J. McCarthy, A. J. Perlis, H. Rutishauser, K. Samelson, B. Vauquois, J. H. Wegstein, A. van Wijngaarden, M. Woodger, and P. Naur. 1963. Revised report on the algorithm language ALGOL 60. Commun. ACM 6, 1 (Jan. 1963), 1–17. doi:10.1145/366193.366201   
[^Baec72]: H. D. Baecker. 1972. On a missing mode in ALGOL 68. SIGPLAN Not. 7, 12 (December 1972), 20–30. doi:10.1145/987059.987062   
[^Baec72b]: H. D. Baecker. 1972. Garbage collection for virtual memory computer systems. Commun. ACM 15, 11 (Nov. 1972), 981–986. doi:10.1145/355606.361886   
[^Bake77]: Henry G. Baker. 1978. List processing in real time on a serial computer. Commun. ACM 21, 4 (April 1978), 280–294. doi:10.1145/359460.359470   
[^Bake78]: Henry G. Baker. 1978. Shallow binding in Lisp 1.5. Commun. ACM 21, 7 (July 1978), 565–569. https://doi.org/10.1145/359545.359566   
[^Bare92]: Barendregt, Henk P. "Lambda calculi with types." (1992).   
[^Barr63]: Barron, D.W., Buxton, J.N., Hartley, D.F., Nixon, E., and Strachey, C. The main features of CPL. Computer Journal 6(2) (1963) 134–143.   
[^Barr68]: Barron, David William. Recursive Techniques in Programming (1968)   
[^Bask80]: Forest Baskett, Andreas Bechtolsheim, Bill Nowicki and John Seamons, The SUN Workstation. March 1980   
[^Bate82]: Raymond L. Bates, David Dyer, and Johannes A. G. M. Koomen. 1982. Implementation of Interlisp on the VAX. In Proceedings of the 1982 ACM symposium on LISP and functional programming (LFP '82). Association for Computing Machinery, New York, NY, USA, 81–87. doi:10.1145/800068.802138   
[^Baue76]: F. L. Bauer. 1976. Programming as an evolutionary process. In Proceedings of the 2nd international conference on Software engineering (ICSE '76). IEEE Computer Society Press, Washington, DC, USA, 223–234. doi:10.5555/800253.807679   
[^Baue79]: Bauer, F.L. (1979). Program development by stepwise transformations — The project CIP. In: Bauer, F.L., et al. Program Construction. Lecture Notes in Computer Science, vol 69. Springer, Berlin, Heidelberg. doi:10.1007/BFb0014671   
[^Baue79b]: Bauer, F.L. (1979). From specification to implementation — The formal approach. In: Bauer, F.L., et al. Program Construction. Lecture Notes in Computer Science, vol 69. Springer, Berlin, Heidelberg. doi:10.1007/BFb0014670   
[^Baue79c]: Bauer, F.L. (1979). Detailization and lazy evaluation, infinite objects and pointer representation. In: Bauer, F.L., et al. Program Construction. Lecture Notes in Computer Science, vol 69. Springer, Berlin, Heidelberg. https://doi.org/10.1007/BFb0014675   
[^Baue81]: Bauer, F. L., Broy, M., Dosch, W., Gnatz, R., Krieg-Brückner, B., Laut, A., … Wössner, H. (1981). Programming in a wide spectrum language: a collection of examples. Science of Computer Programming, 1(1-2), 73–114. doi:10.1016/0167-6423(81)90006-x   
[^BBC73]: The Lighthill debate on Artificial Intelligence https://www.youtube.com/watch?v=03p2CADwGF8&t=1682s   
[^Bech82]: Andreas Bechtolsheim, Forest Baskett, Vaughan Pratt. The SUN Workstation Architecture. Technical Report No. 229, March 1982   
[^Beki84]: Bekić, H. (1984). Towards a mathematical theory of processes. In: Jones, C.B. (eds) Programming Languages and Their Definition. Lecture Notes in Computer Science, vol 177. Springer, Berlin, Heidelberg. doi:10.1007/BFb0048944   
[^Bell98]: Bell G, Strecker WD. Retrospective: what have we learned from the PDP-11—what we have learned from VAX and Alpha. In 25 years of the international symposia on Computer Architecture (selected papers) 1998 Aug 1 (pp. 6-10). doi:10.1145/285930.285934   
[^Birr77]: Andrew Birrell. System Programming in a High Level Language. Ph.D. Thesis, University of Cambridge. December 1977.   
[^Bish75]: Bishop, Peter B. "Garbage collection in a very large address space." (1975).   
[^Blai70]: Fred W. Blair. Structure of the Lisp Compiler. IBM Research, Yorktown Heights, circa 1970. https://www.softwarepreservation.org/projects/LISP/ibm/Blair-StructureOfLispCompiler.pdf   
[^Blai79]: Blair, F. W. "The Definition of LISP 1.8+0.3i." IBM Thomas J Watson Research Center, Internal Report (1979). https://www.softwarepreservation.org/projects/LISP/ibm/Blair-Definition_of_LISP1_8_0_3i-1979.pdf   
[^Bour72]: S.R.Bourne and M.J.T.Guy. AB33.3.8: Comments on suggested improvements to ALGOL 68, Algol Bulletin No. 33, March 1972 http://archive.computerhistory.org/resources/text/algol/algol_bulletin/A33/P38.HTM   
[^Boye75]: Robert S. Boyer and J Strother Moore. 1975. Proving Theorems about LISP Functions. J. ACM 22, 1 (Jan. 1975), 129–144. doi:10.1145/321864.321875   
[^Bobr66]: Bobrow, Daniel G., D. Lucille Darley, Daniel L. Murphy, Cynthia Ann Solomon and Warren Teitelman. “THE BBN-LISP SYSTEM.” (1966).   
[^Bobr67]: Daniel G. Bobrow and Daniel L. Murphy. 1967. Structure of a LISP system using two-level storage. Commun. ACM 10, 3 (March 1967), 155–159. https://doi.org/10.1145/363162.363185   
[^Bobr73]: Daniel G. Bobrow and Ben Wegbreit. 1973. A model and stack implementation of multiple environments. Commun. ACM 16, 10 (Oct. 1973), 591–603. doi:10.1145/362375.362379   
[^Bond77]: Bond, Susan Gillian, Philip Mayne Woodward, and ROYAL RADAR ESTABLISHMENT MALVERN (ENGLAND). Introduction to the 'RS' Portable Algol 68 Compiler. Royal Radar Establishment, Procurement Executive, Ministry of Defence, 1977.   
[^Bond2001]: Susan Bond. An oral history conducted in 2001 by Janet Abbate, IEEE History Center, New Brunswick, NJ, USA. https://ethw.org/Oral-History:Susan_Bond   
[^Brat86]: Bratko, Ivan. Prolog programming for artificial intelligence. 1986.    
[^Broo14]: Stephen Brookes, Peter W. O'Hearn, and Uday Reddy. 2014. The essence of Reynolds. SIGPLAN Not. 49, 1 (January 2014), 251–255. doi:10.1145/2578855.2537851   
[^Bund84]: Bundy, Alan, ed. "Catalogue of artificial intelligence tools." (1984).   
[^Bund21]: Alan Bundy, The early years of AI in Edinburgh https://www.youtube.com/watch?v=VSdnsfGcz_A    
[^Burg64]: W. H. Burge. 1964. The evaluation, classification and interpretation of expressions. In Proceedings of the 1964 19th ACM national conference (ACM '64). Association for Computing Machinery, New York, NY, USA, 11.401–11.4022. doi:10.1145/800257.808888    
[^Burg66]: William H. Burge. 1966. A reprogramming machine. Commun. ACM 9, 2 (Feb. 1966), 60–66. doi:10.1145/365170.365174    
[^Burg71]: W. H. Burge. 1971. Some examples of the use of function-producing functions. In Proceedings of the second ACM symposium on Symbolic and algebraic manipulation (SYMSAC '71). Association for Computing Machinery, New York, NY, USA, 238–241. doi:10.1145/800204.806292    
[^Burg72]: Burge, W. H. (1972). Combinatory Programming and Combinatorial Analysis. IBM Journal of Research and Development, 16(5), 450–461. doi:10.1147/rd.165.0450   
[^Burg75]: Burge, William H. "Recursive programming techniques." (1975).   
[^Burg75b]: Burge, W. H. (1975). Stream Processing Functions. IBM Journal of Research and Development, 19(1), 12–25. doi:10.1147/rd.191.0012   
[^Burg89]: Burge, W.H., Watt, S.M. (1989). Infinite structures in scratchpad II. In: Davenport, J.H. (eds) Eurocal '87. EUROCAL 1987. Lecture Notes in Computer Science, vol 378. Springer, Berlin, Heidelberg. doi:10.1007/3-540-51517-8_103   
[^Burg90]: Burg, Jennifer J. "Constraint-based programming: A survey." (1990). https://core.ac.uk/download/pdf/236248615.pdf   
[^Burs04]: ROD BURSTALL and VICTOR LESSER, Robin Popplestone https://www-robotics.cs.umass.edu/ARCHIVE/remembrance.html     
[^Burs67]: Burstall, R. M., & Fox, L. (1967). Advances in Programming and Non-Numerical Computation. The Mathematical Gazette, 51(377), 277. doi:10.2307/3613292   
[^Burs68]: Burstall, Rodney Martineau, John Stuart Collins, and Robin John Popplestone. POP-2 papers. Edinburgh & London: Oliver & Boyd, 1968.   
[^Burs69]: Burstall, Rod M. "Proving properties of programs by structural induction." The Computer Journal 12.1 (1969): 41-48. doi:10.1093/comjnl/12.1.41    
[^Burs70]: Burstall, R. M. Formal description of program structure and semantics in first—order logic. Machine Intelligence 5 (Meltzer & Michie, Eds.). American Elsevier, New York 79 (1970): 98.   
[^Burs71]: Burstall, R. M., J. S. Collins, R. J. Popplestone. Programming in POP-2 (1971).   
[^Burs72]: Burstall, Rodney M. "Some techniques for proving correctness of programs which alter data structures." Machine intelligence 7, no. 23-50 (1972): 3.   
[^Burs77]: R. M. Burstall and J. A. Goguen. 1977. Putting theories together to make specifications. In Proceedings of the 5th international joint conference on Artificial intelligence - Volume 2 (IJCAI'77). Morgan Kaufmann Publishers Inc., San Francisco, CA, USA, 1045–1058.   
[^Burs77b]: R. M. Burstall. Design considerations for a functional programming language. In Infotech State of the Art Conference, Copenhagen, Denmark, 1977.   
[^Burs79]: Burstall, Rod M.. “Applicative programming.” International Conference on Software Engineering (1979).   
[^Burs80]: R. M. Burstall, D. B. MacQueen, and D. T. Sannella. 1980. HOPE: An experimental applicative language. In Proceedings of the 1980 ACM conference on LISP and functional programming (LFP '80). Association for Computing Machinery, New York, NY, USA, 136–143. DOI:10.1145/800087.802799   
[^Burs80b]: Burstall, R. M. (1980). Electronic category theory. Lecture Notes in Computer Science, 22–39. doi:10.1007/bfb0022493   
[^Burs92]: Burstall, R.M. (1992). Computing: Yet Another Reality Construction. In: Floyd, C., Züllighoven, H., Budde, R., Keil-Slawik, R. (eds) Software Development and Reality Construction. Springer, Berlin, Heidelberg. doi:10.1007/978-3-642-76817-0_6   
[^Burs2000]: Burstall, R. Christopher Strachey—Understanding Programming Languages. Higher-Order and Symbolic Computation 13, 51–55 (2000). doi:10.1023/a:1010052305354   
[^Burs2006]: Burstall, R. (2006). My Friend Joseph Goguen. In: Futatsugi, K., Jouannaud, JP., Meseguer, J. (eds) Algebra, Meaning, and Computation. Lecture Notes in Computer Science, vol 4060. Springer, Berlin, Heidelberg. doi:10.1007/11780274_2   
[^Burstall]: Rod Burstall's home page https://web.archive.org/web/20181021215651/http://homepages.inf.ed.ac.uk/rburstall/   
[^Böhm72]: Böhm, C., & Dezani, M. (1972). A CUCH-machine: The automatic treatment of bound variables. International Journal of Computer & Information Sciences, 1(2), 171–191. doi:10.1007/bf00995737   
[^Cadi72]: J. M. Cadiou and Zohar Manna. 1972. Recursive definitions of partial functions and their computations. In Proceedings of ACM conference on Proving assertions about programs. Association for Computing Machinery, New York, NY, USA, 58–65. doi:10.1145/800235.807072   
[^Camp85]: Campbell-Kelly, Martin. “Christopher Strachey, 1916-1975: A Biographical Note.” Annals of the History of Computing 7 (1985): 19-42.   
[^Card2006]: Cardone, Felice and Roger Hindley. “History of Lambda-calculus and Combinatory Logic.” (2006).   
[^Chen70]: C. J. Cheney. 1970. A nonrecursive list compacting algorithm. Commun. ACM 13, 11 (Nov 1970), 677–678. doi:10.1145/362790.362798   
[^Chio2001]: S. Chiou et al., "A Marriage of Convenience: The Founding of the MIT Artificial Intelligence Laboratory"     
[^Coel82]: Coelho, H., Cotta JC, and L. M. Pereira. "How to Solve it in Prolog, July 1982." Laboratório Nacional de Engenhara Civil, Lisbon, Portugal.   
[^Cohe81]: Jacques Cohen. 1981. Garbage Collection of Linked Data Structures. ACM Comput. Surv. 13, 3 (Sept. 1981), 341–367. doi:10.1145/356850.356854   
[^Cohe88]: Jacques Cohen. 1988. A view of the origins and development of Prolog. Commun. ACM 31, 1 (Jan. 1988), 26–36. doi:10.1145/35043.35045   
[^Coll60]: George E. Collins. 1960. A method for overlapping and erasure of lists. Commun. ACM 3, 12 (Dec. 1960), 655–657. doi:10.1145/367487.367501   
[^Colm96]: Alain Colmerauer and Philippe Roussel. 1996. The birth of Prolog. History of programming languages---II. Association for Computing Machinery, New York, NY, USA, 331–367. doi:10.1145/234286.1057820   
[^Conr74]: R. Conradi, P. Holager, MARY Textbook, RUNIT rapport, 1974   
[^Coro83]: Corovessis, Jiannis. A parallel implementation of SASL. University of St. Andrews (United Kingdom), 1983.   
[^Coul68]: Coulouris, George, T. J. Goodey, R. W. Hill, R. W. Keeling and D. Levin. “The London CPL1 compiler.” Comput. J. 11 (1968): 26-30.   
[^Coul]: George Coulouris http://www.eecs.qmul.ac.uk/~gc/   
[^Crev93]: Crevier, Daniel, AI: the tumultuous history of the search for artificial intelligence, 1993.   
[^Curr58]: Haskell B. Curry, Robert Feys, William Craig. "Combinatory Logic: Volume I" (1958).   
[^Curr70]: Currie, Ian F., Susan G. Bond and J. D. Morison. “Algol 68-R.” ALGOL 68 Implementation (1970).   
[^Curr76]: I.F. Currie, AB39.4.1: Modular Programming in ALGOL 68, Algol Bulletin No. 39, February 1976 http://archive.computerhistory.org/resources/text/algol/algol_bulletin/A39/P41.HTM   
[^Dahl78]: Kristen Nygaard and Ole-Johan Dahl. 1978. The development of the SIMULA languages. History of programming languages. Association for Computing Machinery, New York, NY, USA, 439–480. doi:10.1145/800025.1198392   
[^Darl72]: Darlington, John. "A semantic approach to automatic program improvement." (1972).   
[^Darl73]: J. Darlington and R. M. Burstall. 1973. A system which automatically improves programs. In Proceedings of the 3rd international joint conference on Artificial intelligence (IJCAI'73). Morgan Kaufmann Publishers Inc., San Francisco, CA, USA, 479–485.   
[^Darl75]: R. M. Burstall and John Darlington. 1975. Some transformations for developing recursive programs. In Proceedings of the international conference on Reliable software. Association for Computing Machinery, New York, NY, USA, 465–472. doi:10.1145/800027.808470    
[^Darl76]: Darlington, J., & Burstall, R. M. (1976). A system which automatically improves programs. Acta Informatica, 6(1). doi:10.1007/bf00263742    
[^Darl77]: Burstall, R. M., Darlington, J. (1977). A Transformation System for Developing Recursive Programs. Journal of the ACM, 24(1), 44–67. doi:10.1145/321992.321996    
[^Darl81]: Darlington, J. (1981). An experimental program transformation and synthesis system. Artificial Intelligence, 16(1), 1–46. doi:10.1016/0004-3702(81)90014-x   
[^Davi76]: D. J. M. Davies, POP-10 User's Manual, 29 May 1976. http://www.cs.otago.ac.nz/staffpriv/ok/pop2.d/POP-10.pdf   
[^Dewa79]: Dewar, Robert BK. The SETL programming language. Bell Laboratories, 1979.   
[^Dijk60]: Dijkstra, E. W. (1960). Recursive Programming. Numerische Mathematik, 2(1), 312–318. doi:10.1007/bf01386232    
[^Dijk62]: DIJKSTRA, E. W. (1962). "An ALGOL60 Translator for the X1" Automatic Programming Bulletin, No. 13.   
[^Dijk70]: AB31.1.1.1 "Minority Report", Algol Bulletin No. 31, March 1970 http://archive.computerhistory.org/resources/text/algol/algol_bulletin/A31/P111.HTM   
[^Dijk2001]: Dijkstra, Edsger Wybe. "Oral history interview with Edsger W. Dijkstra." (2001).   
[^Dugg96]: Dominic Duggan and Constantinos Sourelis. 1996. Mixin modules. SIGPLAN Not. 31, 6 (June 15, 1996), 262–273. doi:10.1145/232629.232654   
[^Dunn70]: Raymond D. Dunn. "POP-2/4100 Users' Manual". School of Artificial Intelligence. University of Edinburgh (February 1970)   
[^Eager]: Bob Eager, More on the ICL 2900 Series http://www.tavi.co.uk/icl/bob.htm   
[^Eage22]: Bob Eager, Edinburgh Multi Access System (EMAS) https://www.youtube.com/watch?v=khnu7R3Pffo   
[^Emde76]: M. H. Van Emden and R. A. Kowalski. 1976. The Semantics of Predicate Logic as a Programming Language. J. ACM 23, 4 (Oct. 1976), 733–742. doi:10.1145/321978.321991   
[^Emde90]: Cheng, Mantis HM, Maarten H. van Emden, and B. E. Richards. "On Warren's method for functional programming in logic." In ICLP, pp. 546-560. 1990.   
[^Emde06]: Maarten van Emden, The Early Days of Logic Programming: A Personal Perspective https://dtai.cs.kuleuven.be/projects/ALP/newsletter/aug06/nav/articles/article4/article.html    
[^Emde19]: Emden, Maarten van. “Reflecting Back on the Lighthill Affair.” IEEE Annals of the History of Computing 41 (2019): 119-123.   
[^Emer91]: Emerson W. Pugh, Lyle R. Johnson, and John H. Palmer. IBM's 360 and Early 370 Systems. Cambridge, Mass.: MIT Press, 1991   
[^Earl73]: Earley, J. (1973). Relational level data structures for programming languages. Acta Informatica, 2(4), 293–309. doi:10.1007/bf00289502   
[^Edinburgh]: https://www.ed.ac.uk/informatics/about/history-school-of-informatics/brief-history-of-the-school-of-informatics   
[^Evan68]: Evans Jr, Arthur. "Pal—a language designed for teaching programming linguistics." In Proceedings of the 1968 23rd ACM national conference, pp. 395-403. 1968.    
[^Evan68b]: A. Evans. PAL - A Reference Manual and a Primer. Department of Electrical Engineering, Massachusetts Institute of Technology, February 1968, 185 pages.   
[^EventML]: EventML https://nuprl.org/software/   
[^Fate71]: Richard J. Fateman. 1971. The user-level semantic matching capability in MACSYMA. In Proceedings of the second ACM symposium on Symbolic and algebraic manipulation (SYMSAC '71). Association for Computing Machinery, New York, NY, USA, 311–323. doi:10.1145/800204.806300   
[^Fate73]: R. J. Fateman. 1973. Reply to an editorial. SIGSAM Bull., 25 (March 1973), 9–11. doi:10.1145/1086803.1086804   
[^Fate81]: Fateman RJ. Views on transportability of lisp and lisp-based systems. InProceedings of the fourth ACM symposium on Symbolic and algebraic computation 1981 Aug 5 (pp. 137-141).   
[^Feat79]: Feather, Martin S. “A system for developing programs by transformation.” (1979).   
[^Feni69]: Robert R. Fenichel and Jerome C. Yochelson. 1969. A LISP garbage-collector for virtual-memory computer systems. Commun. ACM 12, 11 (Nov. 1969), 611–612. doi:10.1145/363269.363280   
[^Feni71]: Robert R. Fenichel. 1971. List tracing in systems allowing multiple cell-types. Commun. ACM 14, 8 (Aug. 1971), 522–526. doi:10.1145/362637.362646   
[^Finn83]: Gavin Finnie, AB49.2.1 RS ALGOL 68 Implementors Group (RIG), Algol Bulletin No. 49, May 1983 http://archive.computerhistory.org/resources/text/algol/algol_bulletin/A49/P21.HTM   
[^Fisc93]: Fischer, M. J. (1993). Lambda-calculus schemata. LISP and Symbolic Computation, 6(3-4), 259–287. doi:10.1007/bf01019461   
[^Fode81]: Foderaro JK, Fateman RJ. Characterization of VAX Macsyma. InProceedings of the fourth ACM symposium on Symbolic and algebraic computation 1981 Aug 5 (pp. 14-19).   
[^Fode83]: Foderaro JK, Sklower KL, Layer K. The FRANZ Lisp Manual. Regents of the University of California; 1983 Jun.   
[^Fox66]: FOX, Leslie (ed.). Advances in programming and non-numerical computation. 1966 ISBN:978-0-08-011356-2, 0080113567   
[^Franz]: History of Franz Inc. https://franz.com/about/company.history.lhtml
[^Frie76]: Friedman, Daniel P., and David S. Wise. CONS should not evaluate its arguments. Computer Science Department, Indiana University, 1976. https://help.luddy.indiana.edu/techreports/TRNNN.cgi?trnum=TR44   
[^Frie76b]: Friedman, Daniel P. and David S. Wise. “CONS Should Not Evaluate its Arguments.” International Colloquium on Automata, Languages and Programming (1976).   
[^Full76]: Samuel H. Fuller. 1976. Price/performance comparison of C.mmp and the PDP-10. In Proceedings of the 3rd annual symposium on Computer architecture (ISCA '76). Association for Computing Machinery, New York, NY, USA, 195–202. doi:10.1145/800110.803580   
[^Gabb98]: Gabbay, Dov M., Christopher John Hogger, and John Alan Robinson, eds. Handbook of logic in artificial intelligence and logic programming: Volume 5: Logic programming. Clarendon Press, 1998.   
[^Gard77]: P. J. Gardner. 1977. A transportation of ALGOL68C. In Proceedings of the Strathclyde ALGOL 68 conference. Association for Computing Machinery, New York, NY, USA, 95–101. doi:10.1145/800238.807148   
[^GEDANK]: GEDANKEN. Scanned source listing. https://www.softwarepreservation.org/projects/GEDANKEN/Reynolds-GEDANKEN-MakeTranslator.pdf   
[^GEDANKb]: GEDANKEN. Scanned execution listing https://www.softwarepreservation.org/projects/GEDANKEN/Reynolds-GEDANKEN-Test_Ch_II_Run.pdf    
[^GHC23]: GHC User’s Guide https://downloads.haskell.org/ghc/latest/docs/users_guide/   
[^Gilm63]: GILMORE, P. C. (1963). "An Abstract Computer with a LISP-like Machine Language without a Label Operator," in Computer Programming and Formal Systems, ed. Braffort, P., and Hirschberg, D., Amsterdam, North Holland Publishing Co.    
[^Gira72]: Girard, Jean-Yves. "Interprétation fonctionnelle et élimination des coupures de l'arithmétique d'ordre supérieur." PhD diss., Éditeur inconnu, 1972.   
[^Gogu79]: Goguen, J.A. (1979). Some design principles and theory for OBJ-0, a language to express and execute algebraic specifications of programs. In: Blum, E.K., Paul, M., Takasu, S. (eds) Mathematical Studies of Information Processing. Lecture Notes in Computer Science, vol 75. Springer, Berlin, Heidelberg. doi:10.1007/3-540-09541-1_36   
[^Gogu82]: Joseph Goguen and Jose Meseguer. 1982. Rapid prototyping: in the OBJ executable specification language. SIGSOFT Softw. Eng. Notes 7, 5 (December 1982), 75–84. doi:10.1145/1006258.1006273   
[^Gogu85]: Futatsugi, K., Goguen, J. A., Jouannaud, J.-P., & Meseguer, J. (1985). Principles of OBJ2. Proceedings of the 12th ACM SIGACT-SIGPLAN Symposium on Principles of Programming Languages  - POPL  ’85. doi:10.1145/318593.318610   
[^Gogu88]: Goguen, Joseph. Higher order functions considered unnecessary for higher order programming. SRI International, Computer Science Laboratory, 1988.   
[^Gogu2000]: Goguen, J. A., Winkler, T., Meseguer, J., Futatsugi, K., & Jouannaud, J.-P. (2000). Introducing OBJ. Software Engineering with OBJ, 3–167. doi:10.1007/978-1-4757-6541-0_1   
[^Gold70]: Golden, Jeffrey P. "A User's Guide to the AI Group LISCOM LISP Complier: Interim Report." (1970).   
[^Gord78]: Gordon, Michael J. C., Robin Milner, L. Morris, Malcolm C. Newey and Christopher P. Wadsworth. “A Metalanguage for interactive proof in LCF.” Proceedings of the 5th ACM SIGACT-SIGPLAN symposium on Principles of programming languages (1978): n. pag. DOI:10.1145/512760.512773   
[^Gord79]: Gordon, Michael J. C.. “Edinburgh LCF: A mechanised logic of computation.” (1979).   
[^Gord2000]: Gordon M. From LCF to HOL: a short history. In Proof, language, and interaction 2000 Jul 24 (pp. 169-186).   
[^Gord2000b]: Gordon, M. Christopher Strachey: Recollections of His Influence. Higher-Order and Symbolic Computation 13, 65–67 (2000). doi:10.1023/a:1010097524009    
[^Gord10]: Gordon, M. ICFP 2010 - Tribute to Robin Milner https://vimeo.com/15325077   
[^Gree69]: GREEN, Cordell. "APPLICATION OF THEOREM PROVING TO PROBLEM SOLVING." In Proc. of IJCAI-69. 1969.   
[^Gree74]: Richard Greenblatt, THE LISP MACHINE, Working Paper 79 November 1974   
[^Gree75]: E. M. Greenwalt, Robert A. Amsler, Jonathon Slocum, and Mabry Tyson. LISP Reference Manual : CDC - 6000. CCUM 2, Computation Center, University of Texas at Austin, December 1975.   
[^Gree77]: Bawden A, Greenblatt R, Holloway J, Knight T. LISP Machine Progress Report. MASSACHUSETTS INST OF TECH CAMBRIDGE ARTIFICIAL INTELLIGENCE LAB; 1977 Aug 1.   
[^Gree96]: Greenberg BS. The Multics MACLISP Compiler. The Basic Hackery–a Tutorial. MIT Press. 1977;1988:1996. https://multicians.org/lcp.html   
[^Gree96b]: Greenberg BS. Multics Emacs: The History, Design and Implementation. Technical report, 1996 http://www.multicians.org/mepap.html   
[^Gunt93]: Gunter, Carl A.. “Semantics of programming languages - structures and techniques.” Foundations of computing (1993).   
[^Guti82]: Claudio Gutierrez. 1982. Prolog compared with LISP. In Proceedings of the 1982 ACM symposium on LISP and functional programming (LFP '82). Association for Computing Machinery, New York, NY, USA, 143–149. doi:10.1145/800068.802144   
[^Gutt76]: John V. Guttag, Ellis Horowitz, and David R. Musser. 1976. The design of data type specifications. In Proceedings of the 2nd international conference on Software engineering (ICSE '76). IEEE Computer Society Press, Washington, DC, USA, 414–420.   
[^Gutt78]: John V. Guttag, Ellis Horowitz, and David R. Musser. 1978. Abstract data types and software validation. Commun. ACM 21, 12 (Dec. 1978), 1048–1064. doi:10.1145/359657.359666   
[^Harr70]: M. C. Harrison. BALM-SETL: A simple implementation of SETL. 5 November 1970. https://www.softwarepreservation.org/projects/SETL/setl/newsletter/setl_001_1970-11-05.pdf   
[^Hart62]: T. Hart and M. Levin. The New Compiler. Memo 39, Artificial Intelligence Project, RLE and MIT Computation Center, no date (circa 1962?) http://www.bitsavers.org/pdf/mit/ai/aim/AIM-039.pdf   
[^Hart88]: Hartel, P. H., & Veen, A. H. (1988). Statistics on graph reduction of SASL programs. Software: Practice and Experience, 18(3), 239–253. doi:10.1002/spe.4380180305   
[^Hart13]: Hartley, D. (2013). CPL: Failed Venture or Noble Ancestor? IEEE Annals of the History of Computing, 35(3), 55–63. doi:10.1109/mahc.2012.37    
[^Hart2000]: Hartley, D. (2000). Higher-Order and Symbolic Computation, 13(1/2), 69–70. doi:10.1023/a:1010001708080    
[^Heer80]: Heering J. The Intel 8086, the Zilog Z8000, and the motorola MC68000 microprocessors. Euromicro Newsletter. 1980 May 1;6(3):135-43.   
[^Hend76]: Peter Henderson and James H. Morris. 1976. A lazy evaluator. In Proceedings of the 3rd ACM SIGACT-SIGPLAN symposium on Principles on programming languages (POPL '76). Association for Computing Machinery, New York, NY, USA, 95–103. doi:10.1145/800168.811543   
[^Hewi74]: Hewitt, C., Bishop, P., Steiger, R., Greif, I., Smith, B., Matson, T., & Hale, R. (1974). Behavioral semantics of nonrecursive control structures. Programming Symposium, 385–407. doi:10.1007/3-540-06859-7_147     
[^Hewi09]: Carl Hewitt. Middle History of Logic Programming. 2009 doi:10.48550/arXiv.0904.3036   
[^Hind07]: Hindley, J. R. (2007). M. H. Newman’s Typability Algorithm for Lambda-calculus. Journal of Logic and Computation, 18(2), 229–238. doi:10.1093/logcom/exm001    
[^Hoar64]: C. A. R. Hoare. AB18.3.7: Case expressions, pages 20-22, Algol Bulletin No. 18, October 1964   
[^Hoar65]: C. A. R. Hoare. AB21.3.6: Record Handling, Algol Bulletin No. 21, November 1965   
[^Hoar72]: Hoare, Charles Antony Richard. "Chapter II: Notes on data structuring." In Structured programming, pp. 83-174. 1972.   
[^Hoar75]: Hoare, C.A.R. Recursive data structures. International Journal of Computer and Information Sciences 4, 105–132 (1975). doi:10.1007/BF00976239   
[^Hoar89]: Hoare, C.A.R. Recursive data structures. Essays in computing science. Prentice-Hall, Inc., USA. (1989) doi:10.5555/63445.C1104369   
[^Holm98]: Holmevik, Jan Rune. "Compiling Simula: A historical study of technological genesis." (1998) https://staff.um.edu.mt/jskl1/simula.html   
[^Honeywell72]: Honeywell Series 6000 User Manual 
[^Howe07]: Jim Howe - ARTIFICIAL INTELLIGENCE AT EDINBURGH UNIVERSITY : A PERSPECTIVE http://www.inf.ed.ac.uk/about/AIhistory.html   
[^Huda07]: Paul Hudak, John Hughes, Simon Peyton Jones, and Philip Wadler. 2007. A history of Haskell: being lazy with class. In Proceedings of the third ACM SIGPLAN conference on History of programming languages (HOPL III). Association for Computing Machinery, New York, NY, USA, 12–1–12–55. DOI:10.1145/1238844.1238856   
[^Huda89]: Paul Hudak. 1989. Conception, evolution, and application of functional programming languages. ACM Comput. Surv. 21, 3 (Sep. 1989), 359–411. DOI:10.1145/72551.72554   
[^Hugh83]: Hughes, Robert John Muir. "The design and implementation of programming languages." Ph. D. Thesis, Oxford University 130 (1983).   
[^Hulz83]: Van Hulzen, J. A., & Calmet, J. (1983). Computer Algebra Systems. Computer Algebra, 221–243. doi:10.1007/978-3-7091-7551-4_14   
[^Hunt77]: R.B. Hunter et al. AB41.4.6 Some ALGOL 68 compilers, Algol Bulletin No. 41, July 1977 http://archive.computerhistory.org/resources/text/algol/algol_bulletin/A41/P46.HTM   
[^IFIP21]: IFIP Working Group 2.1 on Algorithmic Languages and Calculi https://ifipwg21wiki.cs.kuleuven.be/IFIP21/WebHome   
[^Ilif61]: ILIFFE, J. K. (1961). "The use of the GENIE System in numerical calculation," Annual Review in Automatic Programming, Vol. 2, Pergamon Press DOI:10.1016/S0066-4138(61)80002-5   
[^IRON77]: High Order Language Working Group. "Department of Defense Requirement for High-Order Computer Programming Languages-Revised IRONMAN." (1977). 5D. RESTRICTIONS ON VALUES   
[^Jenk71]: Griesmer, J. H., & Jenks, R. D. (1971). SCRATCHPAD/1. Proceedings of the Second ACM Symposium on Symbolic and Algebraic Manipulation  - SYMSAC  ’71. doi:10.1145/800204.806266   
[^Jenk74]: Jenks, R. D. (1974). The SCRATCHPAD language. ACM SIGSAM Bulletin, 8(2), 20–30. doi:10.1145/1086830.1086834   
[^Jenk75b]: Griesmer, J. H., Jenks, R. D., & Yun, D. Y. Y. (1975). A SCRATCHPAD solution to problem #7. ACM SIGSAM Bulletin, 9(3), 13–17. doi:10.1145/1088309.1088314   
[^Jenk76]: Richard D. Jenks. 1976. A pattern compiler. In Proceedings of the third ACM symposium on Symbolic and algebraic computation (SYMSAC '76). Association for Computing Machinery, New York, NY, USA, 60–65. doi:10.1145/800205.806324    
[^Jenk79]: Jenks, R. D. (1979). SCRATCHPAD/360. ACM SIGSAM Bulletin, 13(1), 16–26. doi:10.1145/1088282.1088285    
[^Jenk84]: Jenks, R. Scratchpad II, an experimental computer algebra system, abbreviated primer and examples. IBM Thomas Watson Research Center, Yorktown Heights, NY (1984)   
[^Jone78]: Jones, C.B. (1978). The meta-language: A reference manual. In: Bjørner, D., Jones, C.B. (eds) The Vienna Development Method: The Meta-Language. Lecture Notes in Computer Science, vol 61. Springer, Berlin, Heidelberg. doi:10.1007/3-540-08766-4_10   
[^Jone78b]: Henhapl, W., Jones, C.B. (1978). A formal definition of ALGOL 60 as described in the 1975 modified report. In: Bjørner, D., Jones, C.B. (eds) The Vienna Development Method: The Meta-Language. Lecture Notes in Computer Science, vol 61. Springer, Berlin, Heidelberg. doi:10.1007/3-540-08766-4_12   
[^Jone99]: Jones, C.B. (1999). Scientific Decisions which Characterize VDM. In: Wing, J.M., Woodcock, J., Davies, J. (eds) FM’99 — Formal Methods. FM 1999. Lecture Notes in Computer Science, vol 1708. Springer, Berlin, Heidelberg. doi:10.1007/3-540-48119-2_2   
[^Kidd81]: Tracy Kidder,	The Soul Of A New Machine. 1981   
[^Klee52]: S.C. Kleene. Introduction to Metamathematics, North-Holland Publishing Co. (1952)   
[^Knut64]: Donald Knuth, AB17.2.4: Man or boy?, Algol Bulletin No. 17, July 1964 http://archive.computerhistory.org/resources/text/algol/algol_bulletin/A17/P24.HTM   
[^Knut73]: Knuth, Donald Ervin. A Review of "Structured Programming". Stanford, California: Computer Science Department, Stanford University, 1973.   
[^Korn22]: Körner P, Leuschel M, Barbosa J, Costa VS, Dahl V, Hermenegildo MV, Morales JF, Wielemaker J, Diaz D, Abreu S, Ciatto G. Fifty years of Prolog and beyond. Theory and Practice of Logic Programming. 2022 Nov;22(6):776-858.   
[^Kowa74]: Kowalski, Robert. Logic for problem solving. Department of Computational Logic, Edinburgh University, 1974.   
[^Kowa88]: Robert A. Kowalski. 1988. The early years of logic programming. Commun. ACM 31, 1 (Jan. 1988), 38–43. doi:10.1145/35043.35046   
[^KRC81]: EMAS KRC https://www.cs.kent.ac.uk/people/staff/dat/krc/emas-krc.tgz   
[^KRC2016]: UNIX KRC https://www.cs.kent.ac.uk/people/staff/dat/krc/krc-2016-03-31.tgz   
[^Land64]: Landin, Peter J. "The mechanical evaluation of expressions." The computer journal 6, no. 4 (1964): 308-320. DOI: 10.1093/comjnl/6.4.308   
[^Land65a]: Landin, Peter J. "Correspondence between ALGOL 60 and Church's Lambda-notation: part I." Communications of the ACM 8, no. 2 (1965): 89-101. DOI: 10.1145/363744.363749    
[^Land65b]: Landin, Peter J. "A correspondence between ALGOL 60 and Church's Lambda-notations: Part II." Communications of the ACM 8, no. 3 (1965): 158-167. DOI: 10.1145/363791.363804    
[^Land66]: Landin PJ. The next 700 programming languages. Communications of the ACM. 1966 Mar 1;9(3):157-66. DOI: 10.1145/365230.365257    
[^Land66b]: Landin, Peter J. A λ-Calculus Approach in Advances in programming and non-numerical computation. 1966    
[^Land98]: Landin, Peter J. "A generalization of jumps and labels." Higher-Order and Symbolic Computation 11, no. 2 (1998): 125-143. doi:10.1023/a:1010068630801    
[^Landin]: Archive of Peter Landin https://archives.bodleian.ox.ac.uk/repositories/2/resources/9658   
[^Lavi12]: Lavington, Simon. "The Atlas story." In Atlas Symposium, vol. 6. 2012.   
[^LCF77]: Code for LCF Version 5, Oct 1977 https://github.com/theoremprover-museum/LCF77   
[^Leav71]: B. M. Leavenworth. 1971. Transition functions: A method for semantic extensions. In Proceedings of the international symposium on Extensible languages. Association for Computing Machinery, New York, NY, USA, 96–103. doi:10.1145/800006.807989   
[^Lennox]: The GTL Programming Language http://web.archive.org/web/20020601161934/http://www.lennox.com.au/products/gtl.html   
[^Levi75]: Levi, G., Sirovich, F. (1975). Proving program properties, symbolic evaluation and logical procedural semantics. In: Bečvář, J. (eds) Mathematical Foundations of Computer Science 1975 4th Symposium, Mariánské Lázně, September 1–5, 1975. MFCS 1975. Lecture Notes in Computer Science, vol 32. Springer, Berlin, Heidelberg. doi:10.1007/3-540-07389-2_211   
[^Levi82]: Bellia, Marco, Pierpaolo Degano, and Giorgio Levi. "The call by name semantics of a clause language with functions." Logic Programming 1 (1982): J82.   
[^Li96]: Li, X. (1996). Program Sharing: A new implementation approach for Prolog. Programming Languages: Implementations, Logics, and Programs, 259–273. doi:10.1007/3-540-61756-6_90   
[^Lieb80]: Lieberman H, Hewitt C. A Real Time Garbage Collector that can Recover Temporary Storage Quickly. MASSACHUSETTS INST OF TECH CAMBRIDGE ARTIFICIAL INTELLIGENCE LAB; 1980 Apr.   
[^Ligh72]: James Lighthill, Artificial Intelligence: A General Survey (1972) http://www.chilton-computing.org.uk/inf/literature/reports/lighthill_report/p001.htm   
[^Lind74a]: C.H. Lindsey, AB37.4.2: Partial Parametrization, Algol Bulletin No. 37, July 1974 http://archive.computerhistory.org/resources/text/algol/algol_bulletin/A37/P42.HTM   
[^Lind74b]: C.H. Lindsey, AB37.4.3: Modals, Algol Bulletin No. 37, July 1974 http://archive.computerhistory.org/resources/text/algol/algol_bulletin/A37/P43.HTM   
[^Lind76]: C.H. Lindsey, AB39.3.1: Specification of Partial Parametrization Proposal, Algol Bulletin No. 39, February 1976 http://archive.computerhistory.org/resources/text/algol/algol_bulletin/A39/P31.HTM   
[^Lind76b]: C.H. Lindsey, AB39.4.2: Proposal for a Modules Facility in ALGOL 68, Algol Bulletin No. 39, February 1976 http://archive.computerhistory.org/resources/text/algol/algol_bulletin/A39/P42.HTM   
[^Lind78]: C. H. Lindsey and H. J. Boom, AB43.3.2: A Modules and Separate Compilation facility for ALGOL 68, Algol Bulletin No. 43, December 1978 http://archive.computerhistory.org/resources/text/algol/algol_bulletin/A43/P32.HTM   
[^Lind83]: C. H. Lindsey. AB49.1.1 Hans Bekic, Algol Bulletin No. 49, May 1983 http://archive.computerhistory.org/resources/text/algol/algol_bulletin/A49/P11.HTM   
[^Lind93]: C. H. Lindsey. 1993. A history of ALGOL 68. In The second ACM SIGPLAN conference on History of programming languages (HOPL-II). Association for Computing Machinery, New York, NY, USA, 97–132. doi:10.1145/154766.155365   
[^Lisk74]: Barbara Liskov and Stephen Zilles. 1974. Programming with abstract data types. In Proceedings of the ACM SIGPLAN symposium on Very high level languages. Association for Computing Machinery, New York, NY, USA, 50–59. doi:10.1145/800233.807045   
[^Lisk93]: Liskov, B. (1993). A history of CLU. ACM SIGPLAN Notices, 28(3), 133–147. doi:10.1145/155360.155367    
[^LISP61]: LISP system assembly listing. “FIELD TEST ASSEMBLY OF LISP 1.5 SEPTEMBER 1961”, labeled “Bonnie’s Birthday Assembly”. Science and Technology Collection, M.I.T. Museum, Cambridge, Massachusetts, catalog number 1993.053, donated by Timothy P. Hart.   
[^Lond78]: London, Thomas B., and John F. Reiser. "A UNIX™ Operating System for the DEC VAX-11/780 Computer."   
[^MACLISP]: MACLISP changelog LISP-NEWS.DOC   
[^MacQueen]: David MacQueen at LinkedIn https://www.linkedin.com/in/david-macqueen-463788b   
[^MacQ14]: Luca Cardelli and the Early Evolution of ML, by David MacQueen. A paper presented at the Luca Cardelli Fest at Microsoft Research Cambridge on Sept. 8, 2014.   
[^MacQ15]: MacQueen, David B. The History of Standard ML: Ideas, Principles, Culture https://www.youtube.com/watch?v=NVEgyJCTee4
[^MacQ20]: MacQueen, David B., Robert Harper and John H. Reppy. “The history of Standard ML.” Proceedings of the ACM on Programming Languages 4 (2020): 1 - 100.DOI:10.1145/3386336   
[^MacQ22]: D. MacQueen, A New Match Compiler for Standard ML of New Jersey https://icfp22.sigplan.org/details/mlfamilyworkshop-2022-papers/3/A-New-Match-Compiler-for-Standard-ML-of-New-Jersey   
[^Mann70]: Manna, Zohar, and John McCarthy. Properties of programs and partial function logic. Machine Intelligence 5 (Meltzer & Michie, Eds.). American Elsevier, New York 79 (1970): 27.   
[^Mann71]: Zohar Manna and Richard J. Waldinger. 1971. Toward automatic program synthesis. Commun. ACM 14, 3 (March 1971), 151–165. doi:10.1145/362566.362568   
[^Mart76]: Martelli A., Montanari U. Unification in linear time and space: a structured presentation. Internal note IEI-B76-16, 1976.   
[^Mart82]: Alberto Martelli and Ugo Montanari. 1982. An Efficient Unification Algorithm. ACM Trans. Program. Lang. Syst. 4, 2 (April 1982), 258–282. doi:10.1145/357162.357169   
[^Mart2008]: Martelli, A. (2008). The Seventies. In: Degano, P., De Nicola, R., Meseguer, J. (eds) Concurrency, Graphs and Models. Lecture Notes in Computer Science, vol 5065. Springer, Berlin, Heidelberg. doi:10.1007/978-3-540-68679-8_49   
[^Matt83]: Matthews, David Charles James. Programming language design with polymorphism. No. UCAM-CL-TR-49. University of Cambridge, Computer Laboratory, 1983.   
[^McBr69]: McBride, F. V., D. J. T. Morrison, and R. M. Pengelly. "A symbol manipulation system." Machine Intelligence 5 (1969): 337-347.   
[^McCa58]: J. McCarthy: An Algebraic Language for the Manipulation of Symbolic Expressions. MIT AI Lab., AI Memo No. 1, Cambridge, Sept. 1958.   
[^McCa60]: John McCarthy. 1960. Recursive functions of symbolic expressions and their computation by machine, Part I. Commun. ACM 3, 4 (April 1960), 184–195. doi:10.1145/367177.367199   
[^McCa60b]: J. McCarthy, R. Brayton, D. Edwards, P. Fox, L. Hodes, D. Luckham, K. Maling, D. Park and S. Russell. LISP I Programmer's Manual. Computation Center and Research Laboratory of Electronics, Massachusetts Institute of California, March 1, 1960. https://www.softwarepreservation.org/projects/LISP/book/LISP%20I%20Programmers%20Manual.pdf   
[^McCa61]: John McCarthy. 1961. A basis for a mathematical theory of computation, preliminary report. In Papers presented at the May 9-11, 1961, western joint IRE-AIEE-ACM computer conference (IRE-AIEE-ACM '61 (Western)). Association for Computing Machinery, New York, NY, USA, 225–238. doi:10.1145/1460690.1460715   
[^McCa62]: McCarthy, J., Abrahams, P. W., Edwards, D. J., Hart, T. P., & Levin, M. I. (1962). LISP 1.5 programmer's manual. MIT press.    
[^McCa64]: J. McCarthy, AB18.3.12: Definition of new data types in ALGOL x, Algol Bulletin No. 18, October 1964   
[^McCa74]: McCarthy, J. (1974). Artificial intelligence: a paper symposium. Artificial Intelligence, 5(3), 317–322. doi:10.1016/0004-3702(74)90016-2   
[^McCa78]: McCarthy J. History of LISP. In History of programming languages 1978 Jun 1 (pp. 173-185).   
[^McDe84]: Drew McDermott et al., "The Dark Ages of AI: A Panel Discussion at AAAI-84," AI Magazine, Fall 1984, pp. 122-34.   
[^McKus]: Marshall Kirk McKusick. A BERKELEY ODYSSEY: Ten years of BSD history.   
[^Miln72]: Robin Milner. 1972. Implementation and applications of Scott's logic for computable functions. SIGPLAN Not. 7, 1 (January 1972), 1–6. doi:10.1145/942578.807067   
[^Miln75]: Milner, R., Morris, L., Newey, M.: A logic for computable functions with reflexive and polymorphic types. Proving and improving programs, Arc et Senans 1975, pp. 371-394. IRIA, Cahier, 1975   
[^Miln76]: Milner R. Program Semantics and mechanized proof. In Mathematical Centre Tracts. Vol. 82. Amsterdam: Mathematisch Centrum. 1976. p. 3-44   
[^Miln78]: Milner, R. (1978). A theory of type polymorphism in programming. Journal of Computer and System Sciences, 17(3), 348–375. doi:10.1016/0022-0000(78)90014-4    
[^Miln82]: Milner, Robin. “How ML evolved.” (1982).   
[^MilnBird84]: Milner, R., & Bird, R. S. (1984). The Use of Machines to Assist in Rigorous Proof [and Discussion]. Philosophical Transactions of the Royal Society A: Mathematical, Physical and Engineering Sciences, 312(1522), 411–422. doi:10.1098/rsta.1984.0067   
[^Miln90]: Milner, Robin, Mads Tofte, and Robert Harper. "The definition of Standard ML." (1990).   
[^Miln93]: Frenkel, Karen A. and Robin Milner. “An interview with Robin Milner.” Commun. ACM 36 (1993): 90-97. DOI:10.1145/151233.151241   
[^Miln2003]: interview with Robin Milner, held in Cambridge on the 3. September 2003 http://users.sussex.ac.uk/~mfb21/interviews/milner/   
[^Moon74]: David A. Moon. MacLISP Reference Manual, Revision 0. Project MAC, Massachusetts Institute of Technology, April 8, 1974   
[^Moor73]: Moore, J Strother. Computational Logic: Structure sharing and proof of program properties. http://hdl.handle.net/1842/2245   
[^Moor75]: Moore, J Strother. Introducing iteration into the pure LISP theorem prover. IEEE Transactions on Software Engineering 3 (1975): 328-338.   
[^Moor82]: Ian W. Moor. 1982. An applicative compiler for a parallel machine. SIGPLAN Not. 17, 6 (June 1982), 284–293. DOI:10.1145/872726.807002   
[^Moor13]: Moore, J Strother and Claus-Peter Wirth. “Automation of Mathematical Induction as part of the History of Logic.” ArXiv abs/1309.6226 (2013)   
[^Moor18]: J Strother Moore, The PLTP Archive. https://www.cs.utexas.edu/users/moore/best-ideas/pltp/index.html   
[^Moor18b]: J Strother Moore, The PLTP Archive. Listing I https://www.cs.utexas.edu/users/moore/best-ideas/pltp/scanned-images/Listing-I-OCR.pdf   
[^Moor18c]: J Strother Moore, Structure Sharing https://www.cs.utexas.edu/users/moore/best-ideas/structure-sharing/index.html   
[^Morr68]: Morris, J.H.: Lambda calculus models of programming languages. M.I.T. MAC-TR-57, 1968   
[^Morr72]: James H. Morris. 1972. A bonus from van Wijngaarden's device. Commun. ACM 15, 8 (Aug. 1972), 773. doi:10.1145/361532.361558   
[^Morr73a]: James H. Morris. 1973. Types are not sets. In Proceedings of the 1st annual ACM SIGACT-SIGPLAN symposium on Principles of programming languages (POPL '73). Association for Computing Machinery, New York, NY, USA, 120–124. doi:10.1145/512927.512938   
[^Morr73b]: James H. Morris. 1973. Protection in programming languages. Commun. ACM 16, 1 (Jan. 1973), 15–21. doi:10.1145/361932.361937     
[^Morr93]: Morris, L. The next 700 formal language descriptions. LISP and Symbolic Computation 6, 249–257 (1993). doi:10.1007/BF01019460   
[^Mose70]: Joel Moses. 1970. The function of FUNCTION in LISP or why the FUNARG problem should be called the environment problem. SIGSAM Bull., 15 (July 1970), 13–27. doi:10.1145/1093410.1093411   
[^Mose74]: Joel Moses. 1974. MACSYMA - the fifth year. SIGSAM Bull. 8, 3 (August 1974), 105–110. doi:10.1145/1086837.1086857   
[^Mose08]: Moses, J. (2012). Macsyma: A personal history. Journal of Symbolic Computation, 47(2), 123–130. doi:10.1016/j.jsc.2010.08.018   
[^Mull73]: Mullish, Henry, and Max Goldstein. A SETLB Primer: With Over 100 Illustrative Programettes. Courant Institute of Mathematical Sciences, New York University, 1973.   
[^MULTICS1]: https://www.multicians.org/benchmarks.html#INRIA   
[^Muss74]: Ralph L. London and David R. Musser. 1974. The application of a symbolic mathematical system to program verification. In Proceedings of the 1974 annual conference - Volume 1 (ACM '74). Association for Computing Machinery, New York, NY, USA, 265–273. doi:10.1145/800182.810412   
[^Muss80a]: Musser, D. R. (1980). Abstract Data Type Specification in the Affirm System. IEEE Transactions on Software Engineering, SE-6(1), 24–32. doi:10.1109/tse.1980.230459   
[^Muss80b]: David R. Musser. 1980. On proving inductive properties of abstract data types. In Proceedings of the 7th ACM SIGPLAN-SIGACT symposium on Principles of programming languages (POPL '80). Association for Computing Machinery, New York, NY, USA, 154–162. doi:10.1145/567446.567461   
[^Naur64]: P. Naur. Proposals for a new language, Algol Bulletin No. 18, October 1964 http://archive.computerhistory.org/resources/text/algol/algol_bulletin/A18/P39.HTM   
[^Naur66]: P. Naur. The form of specifications, Algol Bulletin No. 22, February 1966 http://archive.computerhistory.org/resources/text/algol/algol_bulletin/A22/P37.HTM   
[^Naur78]: Naur, Peter. "The European side of the last phase of the development of ALGOL 60." In History of programming languages, pp. 92-139. 1978.   
[^Neum23]: Von JOHANN v. NEUMANN, Zur Einführung der transfiniten Zahlen. Acta litt. Acad. Sc. Szeged X. 1(1923) p.199-208
[^Newe75]: Newey, Malcolm C.. “Formal semantics of lisp with applications to program correctness.” (1975).   
[^NUPRL2002]: NuPRL Manual https://nuprl.org/html/02cucs-NuprlManual-appendixB.pdf   
[^O'Do82]: Christoph M. Hoffmann and Michael J. O'Donnell. 1982. Programming with Equations. ACM Trans. Program. Lang. Syst. 4, 1 (Jan. 1982), 83–112. doi:10.1145/357153.357158   
[^O'Do84]: Christoph M. Hoffmann and Michael J. O'Donnell. 1984. Implementation of an interpreter for abstract equations. In Proceedings of the 11th ACM SIGACT-SIGPLAN symposium on Principles of programming languages (POPL '84). Association for Computing Machinery, New York, NY, USA, 111–121. doi:10.1145/800017.800522   
[^O'Do87]: O'Donnell, M.J. (1987). Term-rewriting implementation of equational logic programming. In: Lescanne, P. (eds) Rewriting Techniques and Applications. RTA 1987. Lecture Notes in Computer Science, vol 256. Springer, Berlin, Heidelberg. doi:10.1007/3-540-17220-3_1   
[^O'Ke83]: R. A. O'Keefe. 1983. Prolog compared with LISP? SIGPLAN Not. 18, 5 (May 1983), 46–56. doi:10.1145/948249.948255   
[^Padg88]: Padget, Julian. "Three Uncommon Lisps." In First International Workshop on Lisp Evolution and Standardization. 1988.   
[^PAL360]: PAL https://www.softwarepreservation.org/projects/lang/PAL/   
[^Part84]: Partsch, H. (1984). The CIP Transformation System. In: Pepper, P. (eds) Program Transformation and Programming Environments. NATO ASI Series, vol 8. Springer, Berlin, Heidelberg. doi:10.1007/978-3-642-46490-4_27   
[^Pate76]: M. S. Paterson and M. N. Wegman. 1976. Linear unification. In Proceedings of the eighth annual ACM symposium on Theory of computing (STOC '76). Association for Computing Machinery, New York, NY, USA, 181–186. doi:10.1145/800113.803646   
[^Perl78]: Alan J. Perlis. 1978. The American side of the development of ALGOL. History of programming languages. Association for Computing Machinery, New York, NY, USA, 75–91. doi:10.1145/800025.1198352    
[^Pett78]: Pettorossi, A. (1978). Improving memory utilization in transforming recursive programs. In: Winkowski, J. (eds) Mathematical Foundations of Computer Science 1978. MFCS 1978. Lecture Notes in Computer Science, vol 64. Springer, Berlin, Heidelberg. doi:10.1007/3-540-08921-7_89   
[^Pigo95]: Diarmuid Pigott, HOPL: an interactive Roster of Programming Languages, HOPE https://hopl.info/showlanguage.prx?exp=810   
[^Plot2000]: Plotkin, Gordon D., Colin Stirling, and Mads Tofte. "A brief scientific biography of Robin Milner." In Proof, Language, and Interaction, pp. 1-18. 2000. DOI:10.7551/mitpress/5641.003.0004   
[^Plot10]: Gordon Plotkin - Robin Milner: A Craftsman of Tools for the Mind https://www.youtube.com/watch?v=Jg5VCLb2cMo   
[^Popp2002]: Robin Popplestone. 2002. POP, A Broad-Spectrum Programming Language, 1967–2002. Form. Asp. Comput. 13, 3–5 (Jul 2002), 196–213. doi:10.1007/s001650200009    
[^Popplestone]: Popplestone, R. J. The Early Development of POP https://www-robotics.cs.umass.edu/Popplestone/pop_development.html    
[^Prat73]: Vaughan R. Pratt. 1973. Top down operator precedence. In Proceedings of the 1st annual ACM SIGACT-SIGPLAN symposium on Principles of programming languages (POPL '73). Association for Computing Machinery, New York, NY, USA, 41–51. doi:10.1145/512927.512931   
[^Prolog]: Prolog and Logic Programming Historical Sources Archive https://www.softwarepreservation.org/projects/prolog/index.html#Edinburgh   
[^Prolog75]: PROLOG to DEC 10 Machine Code Compiler, Version 13 Sep 1975 https://www.softwarepreservation.org/projects/prolog/edinburgh/src/Warren-Prolog_Compiler-1975_09_13.pdf   
[^Prolog81]: DEC10 Prolog version 3 https://saildart.org/[PRO,SYS]/   
[^Quar86]: JOHN S. QUARTERMAN, ABRAHAM SILBERSCHATZ, and JAMES L. PETERSON. 4.2BSD and 4.3BSD as Examples of the UNIX System   
[^RABBIT]: RABBIT Scheme compiler http://www.cs.cmu.edu/afs/cs/project/ai-repository/ai/lang/scheme/impl/rabbit/rabbit.lsp   
[^Rand64]: Randell, Brian. & Russell, L. J.  (1964).  ALGOL 60 implementation : the translation and use of ALGOL 60 programs on a computer.  London ; New York :  Published for the Automatic Programming Information Centre, Brighton College of Technology, England, by Academic Press     
[^Rees2010]: Jonathan Rees, The T Project http://mumble.net/~jar/tproject/
[^Reev86]: Peter G. Harrison and Mike Reeve. 1986. The parallel graph reduction machine, Alice. In Proceedings of the Workshop on Graph Reduction. Springer-Verlag, Berlin, Heidelberg, 181–202.   
[^Reyn69]: Reynolds, John C.. “GEDANKEN: A SIMPLE TYPELESS LANGUAGE WHICH PERMITS FUNCTIONAL DATA STRUCTURES AND COROUTINES.” (1969).   
[^Reyn70]: Reynolds, John C.. “GEDANKEN—a simple typeless language based on the principle of completeness and the reference concept.” Communications of the ACM 13 (1970): 308 - 319.   
[^Reyn72]: John C. Reynolds. 1972. Definitional interpreters for higher-order programming languages. In Proceedings of the ACM annual conference - Volume 2 (ACM '72). Association for Computing Machinery, New York, NY, USA, 717–740. doi:10.1145/800194.805852   
[^Reyn74]: Reynolds, John C. "Towards a theory of type structure." In Programming Symposium, pp. 408-425. Springer, Berlin, Heidelberg, 1974.    
[^Reyn93]: Reynolds, John C. "The discoveries of continuations." Lisp and symbolic computation 6, no. 3 (1993): 233-247. doi:10.1007/bf01019459     
[^Reyn98]: Reynolds, John C. "Definitional interpreters revisited." Higher-Order and Symbolic Computation 11, no. 4 (1998): 355-361. doi:10.1023/A:1010075320153   
[^Reyn2012]: John C. Reynolds https://www.softwarepreservation.org/projects/lang/GEDANKEN   
[^Rich13]: Richards, Martin. “How BCPL Evolved from CPL.” Comput. J. 56 (2013): 664-670.   
[^Rich2000]: Richards, M. Christopher Strachey and the Cambridge CPL Compiler (2000). Higher-Order and Symbolic Computation, 13(1/2), 85–88. doi:10.1023/a:1010014110806   
[^Rich69]: Richards, M. (1969, May). BCPL: A tool for compiler writing and system programming. In Proceedings of the May 14-16, 1969, spring joint computer conference (pp. 557-566). doi:10.1145/1476793.1476880   
[^Rich74]: RICHARDS, Martin; EVANS JR, Arthur; MABEE, Robert F. The BCPL reference manual. MASSACHUSETTS INST OF TECH CAMBRIDGE PROJECT MAC, 1974.   
[^Ritc93]: Ritchie, Dennis M. "The development of the C language." ACM Sigplan Notices 28.3 (1993): 201-208.   
[^Robi76]: Robinson, Lawrence, and Oliver Roubine. Special: A specification and assertion language. Menlo Park, Ca.: Stanford Research Institute, 1976.   
[^Roch71]: Arnold Rochfeld. 1971. New LISP techniques for a paging environment. Commun. ACM 14, 12 (Dec. 1971), 791–795. doi:10.1145/362919.362937   
[^Rosetta1]: Man or boy test in Pascal https://rosettacode.org/wiki/Man_or_boy_test#Pascal   
[^Ross61]: ROSS, DOUGLAS T., and STEVEN A. COONS. INVESTIGATIONS IN COMPUTER-AIDED DESIGN. MASSACHUSETTS INST OF TECH CAMBRIDGE ELECTRONIC SYSTEMS LAB, 1961.   
[^Ruti67]: Rutishauser, Heinz. "Description of ALGOL 60, volume 1, edited by Bauer, FL." (1967).   
[^Ryde82]: Rydeheard, David Eric. "Applications of category theory to programming and program specification." (1982).   
[^Ryde2002]: RYDEHEARD, D. E., & SANNELLA, D. T. (2002). A Collection of Papers and Memoirs Celebrating the Contribution of Rod Burstall to Advances in Computer Science. Formal Aspects of Computing, 13(3-5), 187–193. doi:10.1007/s001650200006    
[^Salu94]: Salus PH. A quarter century of UNIX. ACM Press/Addison-Wesley Publishing Co.; 1994 Dec.   
[^Same65]: K. Samelson, AB20.3.3. Functionals and functional transformations, Algol Bulletin No. 20, July 1965 https://archive.computerhistory.org/resources/text/algol/algol_bulletin/A20/P33.HTM   
[^Sann82]: Sannella, Donald. "Semantics, implementation and pragmatics of Clear, a program specification language." (1982).   
[^Sann94]: Sannella, Donald and Martin Wirsing. “Specification Languages” (1994).   
[^Sann14]: D. Sannella, CV https://homepages.inf.ed.ac.uk/dts/cv.html   
[^Scho67]: H. Schorr and W. M. Waite. 1967. An efficient machine-independent procedure for garbage collection in various list structures. Commun. ACM 10, 8 (Aug. 1967), 501–506. doi:10.1145/363534.363554   
[^Schu74]: S.A. Schuman, AB37.4.1: Toward Modular Programming in High-Level Languages, Algol Bulletin No. 37, July 1974 http://archive.computerhistory.org/resources/text/algol/algol_bulletin/A37/P41.HTM   
[^Schw71]: Jacob T. Schwartz. Abstract algorithms and a set theoretic language for their expression. Computer Science Department, Courant Institute of Mathematical Sciences, New York University. Preliminary draft, first part. 1970-1971, 16+289 pages. This copy scanned from NYU Library, courtesy of Alex Kennedy-Grant. http://www.softwarepreservation.net/projects/SETL/setl/doc/Schwartz-Abstract_Algorithms-1971.pdf    
[^Schw82]: Schwarz, J. (1982). Using Annotations to Make Recursion Equations Behave. IEEE Transactions on Software Engineering, SE-8(1), 21–33. doi:10.1109/tse.1982.234771   
[^Somm77]: Sommerville JF. An experiment in high-level microprogramming. University of St. Andrews (United Kingdom); 1977.   
[^SPJ82]: Simon L Peyton Jones. 1982. An investigation of the relative efficiencies of combinators and lambda expressions. In Proceedings of the 1982 ACM symposium on LISP and functional programming (LFP '82). Association for Computing Machinery, New York, NY, USA, 150–158. doi:10.1145/800068.802145   
[^SPJ85]: Jones, S. L. P. (1985). Yacc in sasl — an exercise in functional programming. Software: Practice and Experience, 15(8), 807–820. doi:10.1002/spe.4380150807   
[^SPJ87]: Peyton Jones, Simon L. The implementation of functional programming languages (prentice-hall international series in computer science). Prentice-Hall, Inc., 1987.   
[^Scot93]: Dana S. Scott, A type-theoretical alternative to ISWIM, CUCH, OWHY, Theoretical Computer Science, Volume 121, Issues 1–2, 1993, Pages 411-440, ISSN 0304-3975, doi:10.1016/0304-3975(93)90095-B    
[^Shivers]: Olin Shivers, History of T http://www.paulgraham.com/thist.html   
[^Slom89]: Sloman, Aaron. "The Evolution of Poplog and Pop-11 at Sussex University." POP-11 Comes of Age: The Advancement of an AI Programming Language (1989): 30-54.   
[^Smit73]: Smith, David Canfield and Enea, Horace J. (1973) MLISP 2 http://i.stanford.edu/TR/CS-TR-73-356.html   
[^Stee75]: Sussman, Gerald J. and Guy L. Steele. “An Interpreter for Extended Lambda Calculus: SCHEME,.” (1975).   
[^Stee75b]: Guy L. Steele. 1975. Multiprocessing compactifying garbage collection. Commun. ACM 18, 9 (Sept. 1975), 495–508. doi:10.1145/361002.361005   
[^Stee76]: Steele Jr, Guy Lewis. "LAMBDA: The ultimate declarative." (1976).   
[^Stee76b]: Steele, Guy L. and Gerald J. Sussman. “Lambda: The Ultimate Imperative.” (1976).   
[^Stee77]: Guy Lewis Steele. 1977. Debunking the “expensive procedure call” myth or, procedure call implementations considered harmful or, LAMBDA: The Ultimate GOTO. In Proceedings of the 1977 annual conference (ACM '77). Association for Computing Machinery, New York, NY, USA, 153–162. doi:10.1145/800179.810196   
[^Stee77m]: Guy Lewis Steele. 1977. Macaroni is better than spaghetti. In Proceedings of the 1977 symposium on Artificial intelligence and programming languages. Association for Computing Machinery, New York, NY, USA, 60–66. https://doi.org/10.1145/800228.806933   
[^Stee77b]: Steele Jr GL. Fast Arithmetic in MacLISP. MASSACHUSETTS INST OF TECH CAMBRIDGE ARTIFICIAL INTELLIGENCE LAB; 1977 Sep 1.   
[^Stee78]: Steele, Jr. Guy L. “Rabbit: A Compiler for Scheme.” (1978).   
[^Stee82]: Guy L. Steele. 1982. An overview of COMMON LISP. In Proceedings of the 1982 ACM symposium on LISP and functional programming (LFP '82). Association for Computing Machinery, New York, NY, USA, 98–107. doi:10.1145/800068.802140   
[^Stee96]: Guy L. Steele and Richard P. Gabriel. 1996. The evolution of Lisp. History of programming languages---II. Association for Computing Machinery, New York, NY, USA, 233–330. doi:10.1145/234286.1057818   
[^Stee98]: Sussman, Gerald Jay, and Guy L. Steele Jr. "The first report on Scheme revisited." Higher-Order and Symbolic Computation 11, no. 4 (1998): 399-404.   
[^Stoy79]: Herbert Stoyan. 1979. LISP history. Lisp Bull., 3 (December 1979), 42–53.   
[^Stoy84]: Herbert Stoyan. 1984. Early LISP history (1956–1959). In *Proceedings of the 1984 ACM Symposium on LISP and Functional Programming (LFP ’84)*, 299–310.   
[^Stra61]: Strachey, C., & Wilkes, M. V. (1961). Some proposals for improving the efficiency of ALGOL 60. Communications of the ACM, 4(11), 488-491.   
[^Stra66]: BARRON D. W. and STRACHEY C. Programming in Advances in programming and non-numerical computation. 1966   
[^Stra66b]: CPL Elementary Programming Manual https://web.archive.org/web/20190813130006/http://www.ancientgeek.org.uk/CPL/CPL_Elementary_Programming_Manual.pdf   
[^Stra67]: Strachey, Christopher S.. “Fundamental Concepts in Programming Languages.” Higher-Order and Symbolic Computation 13 (2000): 11-49. DOI:10.1023/A:1010000313106   
[^Strachey]: Catalogue of the papers and correspondence of Christopher Strachey https://archives.bodleian.ox.ac.uk/repositories/2/resources/2561   
[^Stro70]: H. R. Strong. 1970. Translating recursion equations into flow charts. In Proceedings of the second annual ACM symposium on Theory of computing (STOC '70). Association for Computing Machinery, New York, NY, USA, 184–197. doi:10.1145/800161.805164   
[^Stro93]: Bjarne Stroustrup. 1993. A history of C++: 1979–1991. In The second ACM SIGPLAN conference on History of programming languages (HOPL-II). Association for Computing Machinery, New York, NY, USA, 271–297. doi:10.1145/154766.155375   
[^Thom90]: Lins, Rafael Dueire, and Simon J. Thompson. "Implementing SASL using categorical multi-combinators." Software - Practice and Experience 20, no. 11 (1990): 1137-1165.   
[^TITAN]: Cambridge Atlas http://www.chilton-computing.org.uk/acl/technology/atlas/p011.htm   
[^Teit74]: Teitelman, Warren. “The interlisp reference manual.” (1974). https://www.softwarepreservation.org/projects/LISP/interlisp/Interlisp-Oct_1974.pdf   
[^Teit78]: Warren Teitelman with contributions by J. W. Goodwin, A. K. Hartley, D. C. Lewis, J. J. Vittal, M. D. Yonke, D. G. Bobrow, R. M. Kaplan, L. M. Masinter, and B. A. Sheil. Interlisp Reference Manual. Bolt, Beranek & Newman and Xerox Corporation, October 1978. https://www.softwarepreservation.org/projects/LISP/interlisp/Interlisp-Oct_1978.pdf   
[^Teit2008]: Teitelman, W. (2008). History of Interlisp. Celebrating the 50th Anniversary of Lisp on - LISP50. doi:10.1145/1529966.1529971   
[^Tenn77]: Tennent, R. D. (1977). On a new approach to representation independent data classes. Acta Informatica, 8(4), 315–324. doi:10.1007/bf00271340   
[^Turn79]: Turner, D. A. (1979). A new implementation technique for applicative languages. Software: Practice and Experience, 9(1), 31–49. doi:10.1002/spe.4380090105   
[^Turn79b]: Turner, D. A. (1979). Another algorithm for bracket abstraction . The Journal of Symbolic Logic, 44(02), 267–270. doi:10.2307/2273733   
[^Turn81]: D. A. Turner. 1981. The semantic elegance of applicative languages. In Proceedings of the 1981 conference on Functional programming languages and computer architecture (FPCA '81). Association for Computing Machinery, New York, NY, USA, 85–92. doi:10.1145/800223.806766   
[^Turn82]: Turner, D.A. (1982). Recursion Equations as a Programming Language. In: Darlington, John, David Turner and Peter B. Henderson. “Functional Programming and its Applications: An Advanced Course.”   
[^Turn83]: Turner, D. A. "SASL language manual (revised version)." University of Kent (1983).   
[^Turn12]: Turner DA. Some history of functional programming languages. In International Symposium on Trends in Functional Programming 2012 Jun 12 (pp. 1-20). Springer, Berlin, Heidelberg.   
[^Turn16]: Kent Recursive Calculator https://www.cs.kent.ac.uk/people/staff/dat/krc/   
[^Turn19]: David Turner. 2019 Peter Landin Semantics Seminar https://www.youtube.com/watch?v=ezFZIPuSQU8   
[^Vase85]: Vasey, Philip Edgar. First-order logic applied to the description and derivation of programs. (1985).   
[^Vuil73]: Jean Vuillemin. 1973. Correct and optimal implementations of recursion in a simple programming language. In Proceedings of the fifth annual ACM symposium on Theory of computing (STOC '73). Association for Computing Machinery, New York, NY, USA, 224–239. doi:10.1145/800125.804054   
[^Vuil74]: B. Courcelle and J. Vuillemin. 1974. Semantics and axiomatics of a simple recursive language. In Proceedings of the sixth annual ACM symposium on Theory of computing (STOC '74). Association for Computing Machinery, New York, NY, USA, 13–26. doi:10.1145/800119.803880   
[^Wads71]: Wadsworth, P. L. "Semantics and paragmatics of the lambda calculus." PhD thesis, Oxford Univ. (1971).   
[^Wads2000]: Wadsworth, C.P. Continuations Revisited. Higher-Order and Symbolic Computation 13, 131–133 (2000). doi:10.1023/a:1010074329461     
[^Walt75]: Waltz, David L. "Understanding line drawings of scenes with shadows." The psychology of computer vision (1975): 19-91. http://www1.cs.columbia.edu/~waltz/Papers/Understanding%20Line%20Drawing%20of%20Scenes%20with%20Shadows%20PH%20Winston%201975.pdf   
[^Wand77]: Wand, M. Algebraic theories and tree rewriting systems. Indiana University. Computer Science Department Technical Report 66 (1977).   
[^Wand80]: Wand, M. First-order identities as a defining language. Acta Informatica 14, 337–357 (1980). doi:10.1007/BF00286491   
[^Warr75]: David H. D. Warren. Example 1: Quicksort. Circa 1975. Example of generated code from PROLOG to DEC 10 Machine Code Compiler. https://www.softwarepreservation.org/projects/prolog/edinburgh/src/Warren-Prolog_Compiler_Example_1.pdf   
[^Warr77]: David H D Warren, Luis M. Pereira, and Fernando Pereira. 1977. Prolog - the language and its implementation compared with Lisp. In Proceedings of the 1977 symposium on Artificial intelligence and programming languages. Association for Computing Machinery, New York, NY, USA, 109–115. doi:10.1145/800228.806939   
[^Warr77b]: David H D Warren. 1977. Prolog - the language and its implementation compared with Lisp. Slides https://www.softwarepreservation.org/projects/prolog/edinburgh/doc/slides-ACM1977.pdf   
[^Warr78]: Warren, David HD. "Applied logic: its use and implementation as a programming tool." (1978).   
[^Warr81]: Warren, David HD. Higher-order extensions to Prolog - are they needed? Department of Artificial Intelligence, University of Edinburgh, 1981.   
[^Weinreb]: Dan Weinreb on NIL http://www.paulgraham.com/weinreb.html   
[^Weiz68]: Weizenbaum, Joseph. "The FUNARG Problem Explained. unpublished memorandum." (1968).   
[^Well76]: Welliver, Leon. "IDEA: a symbolic integration program." PhD diss., University of St Andrews, 1976.   
[^Whit70]: White, John L.. “An Interim LISP User's Guide.” (1970).    
[^Whit77]: White, Jon L. "Lisp: Program is Data: A historical perspective on MACLISP." In Proceedings of the 1977 MACSYMA Users' Conference, MIT Laboratory for Computer Science, Cambridge, Mass, pp. 181-189. 1977.   
[^Whit78]: Jon L White. 1978. LISP/370: a short technical description of the implementation. SIGSAM Bull. 12, 4 (November 1978), 23–27. doi:10.1145/1088276.1088280   
[^Whit79]: Jon L. White. NIL: A perspective. Proceedings of 1979 MACSYMA Users' Conference, Washington, D.C., June 1979. https://www.softwarepreservation.org/projects/LISP/MIT/White-NIL_A_Perspective-1979.pdf   
[^Whit80]: White JL. Address/memory management for a gigantic Lisp environment or, GC considered harmful. InProceedings of the 1980 ACM Conference on LISP and Functional Programming 1980 Aug 25 (pp. 119-127).   
[^Wich76]: Wichmann, B.A. Ackermann's function: A study in the efficiency of calling procedures. BIT 16, 103–110 (1976). doi:10.1007/BF01940783   
[^Wijn66]: van Wijngaarden, Adriaan. Recursive Definition of Syntax and Semantics : (proceedings IFIP Working Conference on Formal Language Description Languages, Vienna 1966, P 13-24). Stichting Mathematisch Centrum. Rekenafdeling. Stichting Mathematisch Centrum, 1966.   
[^Wijn69]: A. van Wijngaarden (Ed.), Mailloux, B. J., Peck, J. E. L., & Koster, C. H. A. (1969). Report on the Algorithmic Language ALGOL 68. Numerische Mathematik, 14(2), 79–218. doi:10.1007/bf02163002   
[^Wijn77]: A. van Wijngaarcien, B. J. Mailloux, J. E. L. Peck, C. H. A. Kostcr, M. Sintzoff, C. H. Lindsey, L. G. L. T. Meertens, and R. G. Fisker. 1977. Revised Report on the Algorithmic Language ALGOL 68. SIGPLAN Not. 12, 5 (May 1977), 1–70. doi:10.1145/954652.1781176   
[^Wilk92]: Wilkes, M. V. (1992). EDSAC 2. IEEE Annals of the History of Computing, 14(4), 49–56. doi:10.1109/85.194055   
[^Wils92]: Wilson, P.R. (1992). Uniprocessor garbage collection techniques. In: Bekkers, Y., Cohen, J. (eds) Memory Management. IWMM 1992. Lecture Notes in Computer Science, vol 637. Springer, Berlin, Heidelberg. doi:10.1007/BFb0017182   
[^Wirs95]: Wirsing, M. (1995). Algebraic specification languages: An overview. Lecture Notes in Computer Science, 81–115. doi:10.1007/bfb0014423   
[^Wirt66]: Niklaus Wirth and C. A. R. Hoare. 1966. A contribution to the development of ALGOL. Commun. ACM 9, 6 (June 1966), 413–432. doi:10.1145/365696.365702   
[^Wirt76]: Wirth, Niklaus. "MODULA: a language for modular multiprogramming." Berichte des Instituts für Informatik 18 (1976). doi:10.3929/ethz-a-000199440   
[^Wood66]: Woodward, Philip M. List Programming in Advances in programming and non-numerical computation. 1966   
[^Wood72]: Woodward, Philip M.. “Practical experience with algol 68.” Software: Practice and Experience 2 (1972) doi:10.1002/spe.4380020103   
[^Woze71]: J. M. Wozencraft and A. Evans. Notes on Programming Linguistics. M.I.T. Department of Electrical Engineering, February 1971    
[^Wray86]: Wray, Stuart Charles. Implementation and programming techniques for functional languages. No. UCAM-CL-TR-92. University of Cambridge, Computer Laboratory, 1986. https://www.cl.cam.ac.uk/techreports/UCAM-CL-TR-92.pdf    
[^Wulf73]: Wulf, William Allan et al. "The design of an optimizing compiler." (1973).   
[^Zill70]: Stephen N. Zilles. An Expansion of the Data Structuring Capabilities of PAL. Report MIT-LCS-TM-015, Laboratory for Computer Science, Massachusetts Institute of Technology, October 1, 1970.   
[^Zill74]: Zilles, Stephen N. "Algebraic specification of data types." Project MAC Progress Report 11 (1974): 28-52.   
[^Zill75]: Barbara Liskov and Stephen Zilles. 1975. Specification techniques for data abstractions. In Proceedings of the international conference on Reliable software. Association for Computing Machinery, New York, NY, USA, 72–87. doi:10.1145/800027.808426   
