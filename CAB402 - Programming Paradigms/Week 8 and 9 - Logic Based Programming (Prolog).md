![[Pasted image 20250508185909.png]]
## 1 Facts and Rules

### 1.1 Facts
A fact is a predicate expression that makes a declarative statement about the problem domain. Whenever a variable occurs in a Prolog expression, it is assumed to be universally quantified. Note that all Prolog sentences must end with a period.

```
likes(john, susie).                   // John likes Susie
likes(X, susie).                      // Everyone likes Susie
likes(john, Y).                       // John likes everybody
likes(john, Y), likes(Y, john).       // John likes everybody and everybody likes John
likes(john, susie); likes(john,mary). // John likes Susie or John likes Mary
not(likes(john,pizza)).               // John does not like pizza
likes(john,susie) :- likes(john,mary).// John likes Susie if John likes Mary.
```

if there are two of the same fact, eg `father(X)` and `father(X,Y)`. Prolog sees the first as `father/1` and the second as `father/2`
### 1.2 Variables
A variable is when there is a value inside a statement that is not a string and that starts with an uppercase letter.

Variables begin with an uppercase letter. Predicate names, function names, and the names for objects must begin with a lowercase letter. Rules for forming names are the same as for the predicate calculus.

    mother_of
    male
    female
    greater_than
    socrates


Assuming a statement:
`married('Husband name', 'Wife name')`
we can see who the husband is married to by doing:
`married('Husband name', Wife)`

### 1.3 Rules
**helpful hint: dont cares (`_`) works here, we dont need to name variables we don't care about**
A rule is a predicate expression that uses logical implication (:-) to describe a relationship among facts. Thus a Prolog rule takes the form

`left_hand_side :- right_hand_side .`

This sentence is interpreted as: left_hand_side if right_hand_side. The left_hand_side is restricted to a single, positive, literal, which means it must consist of a positive atomic expression. It cannot be negated and it cannot contain logical connectives.

This notation is known as a Horn clause. In Horn clause logic, the left hand side of the clause is the conclusion, and must be a single positive literal. The right hand side contains the premises. The Horn clause calculus is equivalent to the first-order predicate calculus.

In Prolog, the left-hand side of a rule is a pattern that a query is matched against. If the query matches the pattern (via unification), the resulting variable bindings are then used to evaluate the right-hand side. The rule succeeds only if the right-hand side goals succeed under those bindings.

Examples of valid rules:

```
friends(X,Y) :- likes(X,Y),likes(Y,X). // X and Y are friends if they like eachother
hates(X,Y) :- not(likes(X,Y)). // X hates Y if X does not like Y.
enemies(X,Y) :- not(likes(X,Y)),not(likes(Y,X)).  // X and Y are enemies if they don't like each other
```

Examples of invalid rules:

```
left_of(X,Y) :- right_of(Y,X)          // Missing a period
likes(X,Y),likes(Y,X) :- friends(X,Y). // LHS is not a single literal
not(likes(X,Y)) :- hates(X,Y).         // LHS cannot be negated
```

**Representing an OR**

```
motherInLaw(SonInLaw, MotherInLaw) :- married(SonInLaw, Wife), mother(Wife, MotherInLaw) // find husbands mother-in-law

// OR the following entry. If the top is false Prolog will check if this one is true

motherInLaw(DaughterInLaw, MotherInLaw) :- married(Husband, DaughterInLaw), mother(Husband, MotherInLaw) // find wifes mother-in-law 
```

## 2 Unification and Search
### 2.1 Unification
Unification is the algorithm for determining the substitutions needed to make two expressions match.
Two terms unify when they are the same term, or if they contain variables that can be substituted in such a way that the terms are equal.

Take the statement 
`married(Husband, 'Catherine') = married('James', 'Catherine')`
In order to make these clauses the same the following needs to be true:
- the name of the fact (atom) needs to be the same (`married`)
- it has to have the same number of arguments

We can also have both fields be a variable:
`parent(Child, Parent)`
and the query will return values that satisfy it. If we press the semicolon, (`;`) it'll find another way to satisfy it (look for other entries). Press full stop `.` to finish

### 2.2 Search
**Search Tree**
![[Pasted image 20250508211930.png|500]]
Here, the statement is unified and `Y=X`
We now need to prove all of the statements are true
We find `f(a)` is a possible substitute for `f(X)`, sub it in, `X=a`
`g(a)` is an axiom, evaluates to true
there is no `h(a)`, this path terminates, try `X=b` next

**another one**
![[Pasted image 20250508212233.png|500]]

### 2.3 Complex Relationships
```
relation(Husband, Wife, wife) :- married(Husband, Wife).
relation(Wife, Husband, husband) :- married(Husband, Wife).

relation(Child, Mother, mother) :- mother(Child, Mother).
relation(Child, Father, father) :- father(Child, Father).

relation(GrandChild, Grandma, grand(mother)) 
	:- grandmother(GrandChild, Grandma).
relation(GrandChild, Grandpa, grand(father)) 
	:- grandfather(GrandChild, Grandpa).

relation(ChildInLaw, MotherInLaw, motherInLaw) 
	:- motherInLaw(ChildInLaw, MotherInLaw).
```

if the grand relation is called above, like `relation(GrandChiild, Grandpa, grand(Gender)`. it will return all the relations AND set the Gender to either `mother` or `father`, depending on **which rule was called**.
## 3 Recursion and Control
### 3.1 Recursion
Prolog predicates can be defined recursively. 

![[Pasted image 20250508221634.png|400]]

```prolog
?- descend(anna, donna).

Try base case:
descend(anna, donna) :- child(anna, donna).      % fails

Try recursive case:
descend(anna, donna) :- child(anna, Z), descend(Z, donna).
Z = bridget → descend(bridget, donna)

descend(bridget, donna) :- child(bridget, Z), descend(Z, donna).
Z = caroline → descend(caroline, donna)

descend(caroline, donna) :- child(caroline, donna).   % succeeds

→ descend(anna, donna) = true
```

### 3.2 Control

## 4 Lists
List elements are enclosed in square brackets.
Head is the first item in the list. Tail is everything else
The `|` operator is a key tool for writing Prolog list manipulation predictes

**for example:**
```
[Head|Tail] = [mia, vincent, jules, yolanda]

Head = mia
Tail = [vincent, jules, yolanda]
yes

?-

// also, for empty lists
[X|Y] = []
no
```

