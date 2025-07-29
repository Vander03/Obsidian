
8.1 Logic Programming
	•	Declarative: define what is true, not how to compute it.
	•	Built from facts, rules, and queries.

---

8.2 Learn Prolog Now
	•	Use interactive query shell: ?-
	•	Facts/rules stored in .pl files.
	•	use `swipl` to launch
	•	load logic using `consult("filepath").`
	

---

8.3 Prolog Facts

```
parent(john, mary).
is_mammal(dog).
```

	•	Facts are unconditional truths.

---

8.4 Prolog Variables

```
parent(john, X).
```

	•	Variables begin with uppercase.
	•	Used to find values in queries.

---

8.5 Prolog Rules

```
ancestor(X, Y) :- parent(X, Y).
ancestor(X, Y) :- parent(X, Z), ancestor(Z, Y).
```

	•	:- means “if”; rules allow inference.

---

8.6 Prolog Search
	•	Uses depth-first search with backtracking.
	•	Example:

```
?- ancestor(john, X).
```

	•	May produce multiple solutions.

---

8.7 Complex Terms

```
date(2024, may, 6).
event(concert, date(2024, may, 6)).
```

	•	Structured data terms.
	•	Pattern matching works on inner structure.

---

8.8 Arithmetic with Logic

```
X is 3 + 4.
```

	•	is evaluates right-hand side.
	•	Comparisons: =:=, =\=, >, =<, etc.

---

8.9 Prolog Recursion

```
length([], 0).
length([_|T], N) :- length(T, N1), N is N1 + 1.
```

	•	Core for processing lists and trees.

--- 

9.1 Prolog Lists

```
member(X, [X|_]).
member(X, [_|T]) :- member(X, T).
```
	•	Lists are recursive: [Head|Tail]

---

9.2 Cuts and Negation

Cut (!):

```
grade(Mark, fail) :- Mark < 50, !.
grade(_, pass).
```

Negation:

```
\+ Condition.
```


---

9.3 Arithmetic Again

```
sum(A, B, S) :- S is A + B.
```

	•	All variables on RHS of is must be bound.

---

9.4 Assignment 1 Pattern

```
nextSemester(semester(Y, 1), semester(Y, 2)).
nextSemester(semester(Y, 2), semester(Y, summer)).
nextSemester(semester(Y, summer), semester(Y1, 1)) :- Y1 is Y + 1.
```
	•	Handle semester transitions.

---


Common Patterns:

Membership:

```
member(X, [X|_]).
member(X, [_|T]) :- member(X, T).
```

Append:

```
append([], L, L).
append([H|T], L2, [H|R]) :- append(T, L2, R).
```

Length:

```
length([], 0).
length([_|T], N) :- length(T, N1), N is N1 + 1.
```

