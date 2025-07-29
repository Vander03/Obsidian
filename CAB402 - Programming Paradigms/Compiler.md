F# Error Summary by Compiler Phase

1. Scanning (Lexical Analysis) — Compile Time

Detects: Invalid characters, unterminated strings, or illegal tokens.
Examples:
```
	•	let x = 10“ → Unexpected character: “
	•	let 9x = 3 → Identifiers can’t start with numbers
```

⸻

2. Parsing (Syntax Analysis) — Compile Time

Detects: Grammar errors — unexpected tokens or malformed structure.
Examples:
```
	•	let x = (3 + ) → Incomplete expression
	•	match x with | 1 -> ... | -> ... → Missing pattern on the second clause
```

⸻

3. Semantic Analysis — Compile Time

a. Name Resolution

Detects: Undeclared variables/functions or scoping errors.
Examples:
```
	•	let y = x + 1 → x not declared in scope
```

b. Type Checking

Detects: Type mismatches, invalid operations.
Examples:
```
	•	let x = "5" + 1 → string + int is invalid
	•	let f x = x + true → Cannot add int and bool
```

⸻

4. Runtime Errors — Run Time

Detected only after successful compilation.

Examples:
```
	•	List.head [] → Runtime exception: ArgumentException
	•	arr.[10] when arr.Length = 3 → Index out of bounds
	•	let x = 10 / 0 → Division by zero
```

⸻

Common Mistakes and Fixes in F#
![[Pasted image 20250606192541.png]]