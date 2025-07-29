## 1 Week 1
Turing machines (practical questions)
- Create a turing machines **check**
- Or given a turing machine and asked will it terminate, or when will it

Lambda Calculus **check** somehwat
- Underlying concepts like lexical scoping, and relating them to something equivalent in  C# or F#
- All about reducing and simplifying, could ask to simplify to simplest form, or if 2 are equivalent (he mentions free variables and ability to rename variables)


## 2 F\#
- "not much we can do after week 2, needs list and stuff to do anything interesting"
- Week 3
	- practical questions
	- "recursion method of least preference, prefer higher order functions"
	- "often asks heres a problem, solve it using recursion, then solve it again using higher order functions"
	- doable within 10 lines of code
- Discriminated unions, good for recursive stuff like trees


Week 4
" translate this LINQ expression into non-functional C# code or F#, or vice versa"

Week 5
general questions around monads (doing them in C# in terms of computational expressions and building)
monadic types vs monads themselves and their building blocks
Why they exist, why do we have them

week 6
also LINQ, connecting F# and C#

Week 7
React, questions dealing with the functional essence of react. How its functional in its nature and how its drawing to the strengths of functional programming

Week 8
prolog. almost certain to have one
writing prolog code to do a task
last time, looked at derivation trees and how search works recursively with backtracking and unification <- understand ideas

week 10
closures
understanding the concepts, **why we do it**, what it means and how it works in different languages (Java and C# and F#)

week 11 
dynamic languages
prototyping in javascript is one of his favourites
difference between compiled and interpreted may be of some interest
ask about some high-level elements of the van roy paper (important ideas)

week 12
too much stuff, they keep it high level
understanding the different phases of the compiler and what they are responsible for conceptually
how that would manifest itself from a end user perspective (how it would manifest itself in different behaviours, different errors and different points where problems might be detected)
used to understand the responsibilities of each different parts of the compiler

week 13
havent had a question about this in a past exam


## 3 Turing
Week 1 Tut
000000111111000000000

A, write 1 R -> B
B, write 1 L -> A
A, write 1 L -> C
C, write 1 L -> B
B, write 1 L -> A
A, write 1 R -> B
B, write 1 R -> B
B, write 1 R -> B
B, write 1 R -> B
B, write 1 L -> A
A, write 1 L -> C
C, is 1, terminate
0000000111|1|1100000000

Lambda Calc
```
(λ x. λ y. (x y)) y
alpha red y to s
(λ x. λ s. (x s)) y
beta reduction y into x
λ s. (y s)

(λ f. λ x. f (f x)) (λ x. x)
alpha reduction x to y
(λ f. λ y. f (f y)) (λ x. x)
beta red sub in fun
λ y. (λ x. x) ((λ x. x) y)
beta red y into x right
λ y. ((λ x. x) y)
beta reduction y into x
λ y. y
```

Lambda Calc

```
1. succ(x)
2. succ(succ(x))
3. L. n L.m (n succ m)
4. 
(λ succ. λ n. λ m. (n succ m)) (λ n. λ f. λ x. s(n f x)) 1 2

(λ succ. λ n. λ m. (n succ m)) (λ b. λ f. λ x. s(b f x)) 1 2 - n to b alpha r

λ n. λ m. (n (λ b. λ f. λ x. f(b f x)) m)) 1 2  - beta r

λ m. (1 (λ b. λ f. λ x. f(b f x)) m)) 2 - subs 1 for n

(1 (λ b. λ f. λ x. f(b f x)) 2)) - subs 2 for m

1 (λ f. λ x. f(2 f x)) - subs 2 for b

1 (λ f. λ x. f(λ p. λ r. p(p r) f x)) - convert 2 into lambda calc (λ p. λ r. p(p r))

1 (λ f. λ x. f(λ r. f(f r) x)) - sub f for p

1 (λ f. λ x. f(f(f x))) - sub x for r

λ p. λ r. (p r) (λ f. λ x. f(f(f x))) - sub λ p. λ r. (p r) for 1

λ r. ((λ f. λ x. f(f(f x))) r)  - sub (λ f. λ x. f(f(f x))) for p

λ r. (λ x. r(r(r x)))) - sub r for f

λ f. (λ x. f(f(f x))) - alpha r to f
```



