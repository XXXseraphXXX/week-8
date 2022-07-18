# Week-8 Prolog Tutorial by Jimmy Zhang
## Logic language
**What is a logic progamming?**

Logic programming is when Rules and facts derived by the programmer, logic engine infer answers to question.
example of this is Prolog.

## Prolog programing and Characteristics
### First-order logic(FOL)
- Prolog is a **first-order logic**.
  - includes variables and thus allows for abstraction.
  - variables like **Quantified variables and predicates.**
    - there are two type of Quantified variables :
      - **universal quantification** ∀X – for All objects X
      - **existential quantification** - ∃Y – there Exists an object Y

  - **predicate** : map the aurguement to be true or false
    - p: Objects → { true, false }
    - example plant(X)
    - plant: Objects → { true, false }
    - plant(grass) = true
    - plant(moe) = false

- let combine them now ∃X[plant(X,grass)]
- ∃X[plant(X,grass)] - there exists an object X such that X is the plant of grass.
- ∀Y[plant(Y)] - for all objects Y such that Y is plant

 - **logical connectives** : and, or, not
    - ∃A∀B[parent(A,B) and female(B)] :There exists an object F for all object B such that A is a parent of B and A is female. 
    - ∀X[months(X) and (hot(X) or cold(X))] : For all objects X such that X is a month and X is either hot or cold.
 -**if-then rules**
  - ∀X∀Y[parent(X,Y) and female(X) → mother(X,Y)]
    - For all objects X and for all objects Y such that if X is a parent of Y and X is female then X is a mother.
  - ∀Q[human(Q) → mortal(Q)]
    - For all objects Q such that if Q is human then Q is mortal.

- **Propostions** - statement that are either true or false.
- **inference** - is the act of drawing up a conclusion basic on what is known.
- **Rule of inference** - is a scheme for constructing valid inferences.
- **Propostional Logic = Propostions + rules of the inferences
  - example: if i am at church then today is Sunday.
  - i am at church
  - therefore today is Sunday.
- Every program is a set of Horn clauses.(facts, rules, question(queries))
  - **Fact**: a fact constitutes a declaration of a truth
    - parent(bob,diana).
  - **Rules**: parent(X,Y) :- father(X,Y).
  - to run a program, we ask **question or queries** about the database
- Program is facts + rules. (horn clauses).
- Inference is by **resolution**.
- use resolution with clause expressions
- Search is by backtracking with unification.
- Basic data structure is term or tree.
- Variables are unknowns not locations.
- Prolog does not distinguish between inputs and outputs. It solves relations/predicates.
- A **compound query** is the conjunction of individual simple queries.
- example: - parent(X,Y) , parent(Y,ann).
- 
## Declarative vs. Procedural
- Interpreting rules purely as Horn clause logic statement → declarative
- Interpreting rules as “specialized queries” → procedural
- example :mfather(X,Y) :-male(X), parent(X,Y)

## List& pattern matching.
**What is unification operator?**
- =/3
- Two terms unify, if there is a common substitution for all variables which makes them identical.
- ?- a = a.
 true
?- a = b.
 false
?- a = X.
 X = a
?- X = Y.
 true

## Lists
- [a,b,c] is a list in Prolog.
- [H|T] = [a,b,c] results in
- H = a    i.e. the head of list
- T = [b,c] i.e. the tail of the list.
- ?-[a,b] = [a,X] 
- X = b

**the First Predicate**
- accept a list in the first argument and return the first element of the list as the second argument.
  - first(list,E) :-List = [H|T],E = H

**the Last Predicate**
- accept a list in the first argument and return the last element of the list as the second argument.
  - last(list,E) :-List = [H|T],E = L
**Recursion** is a technique in which one predicate uses itself (may be with some other predicates) to find the truth value.

example −

is_digesting(X,Y) :- just_ate(X,Y).

is_digesting(X,Y) :-just_ate(X,Z),is_digesting(Z,Y).

**append/3s predicate** : accept two lists in the first two parameters, append the second list to be the first and retirn the resulting list in the third parameter.
- **Note:** use recursion.

**example**
- append([],list, list)
- append([H|T], List, [H|Result]) :- append(T, List, Result).

##Practice
https://riptutorial.com/prolog

## reference 

- Webber, Adam. Modern Programming Languages: A Practical Introduction. Franklin, Beedle &amp; Associates, 2002. 
- Benoist, Louis de. “Logic Programming - Rethinking the Way We Program.” Medium, Towards Data Science, 3 Jan. 2020, https://towardsdatascience.com/logic-programming-rethinking-the-way-we-program-8706b2adc3f1. 
- “Prolog Language Tutorial =&gt; Recursion.” Prolog Language Tutorial =&gt; Recursion, https://riptutorial.com/prolog/example/10528/recursion. 
- “Prolog Recursion: How Recursion Works in Prolog?” EDUCBA, 23 July 2021, https://www.educba.com/prolog-recursion/. 
- Triska, Markus. Facets of Prolog, https://www.metalevel.at/prolog/facets. 
- Triska, Markus. Introduction, https://www.metalevel.at/prolog/introduction. 
- Triska, Markus. Logical Foundations of Prolog, https://www.metalevel.at/prolog/logic. 
