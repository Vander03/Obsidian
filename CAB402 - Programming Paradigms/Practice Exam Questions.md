![[Pasted image 20250604121137.png]]
```
State	Input	Write	Move	NState		Terminate
A		0		1		R		A			No
A		1		0		R		B			No
B		0		1		R		A			No
B		1		0		R		C			No
C		0		1		R		A			No
C		1		0		R		C			Yes
```

---
![[Pasted image 20250604121404.png]]
both 3 and 4

---
 ![[Pasted image 20250604130118.png]]
 because turing machines and lambda calculus is the birth of programming, and therefore the very first paradigm of computing

![[Pasted image 20250604130207.png|400]]

```
λ x. (λ z. z z x)) z
alpha reduction z to y
λ x. (λ y. y y x)) z
beta reduction z to x
λ y. y y z
```

---
![[Pasted image 20250604141001.png]]
![[Pasted image 20250604140946.png]]

```F#
let rec totalArea (squares: List<int>): int =
    match squares with
    | [] -> 0
    | head::tail -> (head*head) + (totalArea tail)


let totalArea (squares: List<int>): int =
    squares |> List.map(fun a -> a * a) |> List.sum

printfn "%d" (totalArea [ 1; 7; 3 ])
```


![[Pasted image 20250604143859.png]]
```F#
// Define the Prereq discriminated union
type Prereq =
    | And of seq<Prereq>
    | Or of seq<Prereq>
    | Unit of string
    | CreditPoints of int
    | Nil

// Recursive function to count the number of Unit constructors
let rec numberOfUnits (prereq: Prereq) : int =
    match prereq with
    | Unit _ -> 1
    | CreditPoints _ -> 0
    | Nil -> 0
    | And prereqs
    | Or prereqs ->
        prereqs |> Seq.map numberOfUnits |> Seq.sum

// Sample test cases

let prereq1 = CreditPoints 96
let prereq2 =
    And [
        Or [ Unit "CAB201"; Unit "ITD121" ]
        Or [ Unit "MZB151"; CreditPoints 12 ]
    ]

let prereq3 =
    And [
        Or [ Unit "CAB201"; Unit "ITD121" ]
        Unit "CAB203"
    ]

let prereq4 =
    And [
        Unit "COMP101"
        Or [ Unit "MATH200"; CreditPoints 60 ]
        Nil
    ]

// Print results
printfn "IFB295 (should be 0): %d" (numberOfUnits prereq1)
printfn "CAB220 (should be 3): %d" (numberOfUnits prereq2)
printfn "CAB402 (should be 3): %d" (numberOfUnits prereq3)
printfn "Nested mix (should be 3): %d" (numberOfUnits prereq4)
```

