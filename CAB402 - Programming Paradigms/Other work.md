![[Pasted image 20250225144554.png]]

Show that ifthenelse true 2 3 evaluates to 2

```
Show that ifthenelse true 2 3 evaluates to 2
true = λ a. λ b. a
false = λ a. λ b. b
ifthenelse = λ p. λ a. λ b. p a b

λ p. λ a. λ b. p a b
true 2 3 ->
(λ p. λ a. λ b. p a b) true 2 3

sub in values for lambda calc vals
(λ p. λ a. λ b. p a b) (λ a. λ b. a) (λ f. λ x. f(f(x))) (λ f. λ x. f(f(f(x))))

alpha reduction a and b for c and d
(λ p. λ c. λ d. p c d) (λ a. λ b. a) (λ f. λ x. f(f(x))) (λ f. λ x. f(f(f(x))))

beta reduction p for (λ a. λ b. a)
(λ c. λ d. (λ a. λ b. a) c d)  (λ f. λ x. f(f(x))) (λ f. λ x. f(f(f(x))))

beta reduction c for 2: (λ f. λ x. f(f(x)))
(λ d. (λ a. λ b. a) (λ f. λ x. f(f(x))) d) (λ f. λ x. f(f(f(x))))

alpha reduction f and x for g and z
(λ d. (λ a. λ b. a) (λ g. λ z. g(g(z))) d) (λ f. λ x. f(f(f(x))))

beta reduction d for (λ f. λ x. f(f(f(x))))
(λ a. λ b. a) (λ g. λ z. g(g(z))) (λ f. λ x. f(f(f(x)))))

beta reduction a for (λ g. λ z. g(g(z)))
λ b. (λ g. λ z. g(g(z))))  (λ f. λ x. f(f(f(x)))))

beta reduction b for  (λ f. λ x. f(f(f(x))))) [no reduction, falls away]
(λ g. λ z. g(g(z)))) = 2, proof done

```