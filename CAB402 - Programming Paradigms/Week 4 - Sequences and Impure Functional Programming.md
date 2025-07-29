## 1 Eager vs Lazy Evaluation
Eager calculates the value as soon as possible, Lazy only calculates if/when it is needed.
For example, the `&&` and `||` in C and C# are lazily evaluated (if first part excludes or includes the path, no use in determining the second part), along with functions in Haskell.

## 2 Sequences
Sequences in F# are lazy. They are large ordered collections of data, but do not necessarily expect to use all the elements. Individual sequence elements are computed only as required.

It is due to this that a sequence can sometimes provide better performance than a list in situations where not all elements are used.

Presented by the `seq<T>` type, which is an alias for `IEnumerable<T>`.

## 3 C# Iterators

```C#
public class Tree {
	private string label;
	private Tree left, right;

	public IEnumerable<Tree> Preorder() {
		// yield returns one of the nodes, will return control when 
		// the next one is needed
		yield return this; 
		if (left != null)
			foreach (Tree node in left.Preorder())
				yield return node;
		if (right != null)
			foreach (Tree node in right.Preorder())
				yield return node
	}
}

// call the function
static void Main(string[] args) {
	IEnumerable<Tree> nodes = root.Preorder();
	foreach (var node in nodes) // iterates through the function even if only var
		Console.WriteLine(node);
}
```

## 4 F# Sequences and Yields
```F#
let rec iterate tree =
    match tree with
    | Leaf(value=v) -> seq { yield v }
    | Parent(value=v; left=l; right=r) -> seq { yield! (iterate l);
                                                yield v; 
                                                yield! (iterate r)} 
// yield! means yield a sequence in the order in which they are provided
// syntactic to foreach in C# above
let rec from a = seq { yield a; yield! from (a+1) }

let x = seq {0..100}

let products = 
  seq { for x in 2..4 do
            for y in 2..4 do
                yield x*y
      }

```

if we want to return a sequence of values we need to use `yield!`
turn sequence into list: `y |> Seq.toList`

## 5 Reference Calls
The `ref` type allows us to create an object that contains a mutable value:
```F#
let a = ref 5 // creates a mutible var a
let b = !a // accesses value associated
let c = a // creates a copy of the object reference
c := 10 // changing the current value via either object reference

```

## 6 Arrays
Similar to lists, but are mutable (elements can change after creation). 
Supports efficient random access to elements
Arrays do not support pattern matching

```F#
let a = [| 1;2;3;4;5 |]
a.[1] // access 2nd element
```

## 7 Unit
Analogous to `void`
Has a single value, indicated by the token `()`

## 8 Map
Equivalent to dictionary in C# or Hashtable in Java.
Add entires to a map with `Map.add` function:
```F#
let rec hashlist f L =
    match L with
    | [] -> Map.empty
		| head::tail -> Map.add head (f head) (hashlist tail)

// to look up value of key x in map m using array access syntax
let result = m.[x]
```

## 9 Converting Between Lists, Arrays, Sets and Sequences

```F#
// Convert to List:
Array.toList, List.ofArray, Seq.toList, List.ofSeq, Set.toList 
// Convert to Sequence:
Array.toSeq, Seq.ofArray, List.toSeq, Seq.ofList, Set.toSeq
// Convert to Array:
List.toArray, Array.ofList, Seq.toArray, Array.ofSeq, Set.toArray
// Convert to Set:
Set.ofArray, Set.ofList, Set.ofSeq
```

## 10 Standard Collection Functions
```F#
init : (size:int -> initfunc:(int -> 'a) -> seq<'a>)
	Seq.init, Array.init, List.init	
map : (func:('a -> 'b) -> collection:seq<'a> -> seq<'b>)
	Seq.map, List.map, Array.map, Set.map
map2 : (func:('a -> 'b -> 'c) -> c1:seq<'a> -> c2:seq<'b> -> seq<'c>)
	Seq.map, List.map, Array.map, Set.map
filter : (pred:('a -> bool) -> collection:seq<'a> -> seq<'a>)
	Seq.filter, Set.filter, List.filter, Array.filter 
fold : (op:('a -> 'b -> 'a) -> 'a -> collection:seq<'b> -> 'a) 
	Seq.fold, Set.fold, Array.fold, List.fold, 
iter : (visitor:('a -> unit) -> collection:seq<'a> -> unit)
	Seq.iter, Set.iter, Array.iter, List.iter
exists : (pred:('a -> bool) -> collection:seq<'a> -> bool)
	Seq.exists, Set.exists, Array.exists, List.exists
forall : (pred:('a -> bool) -> collection:seq<'a> -> bool)
	Set.forall, Array.forall, List.forall, Seq.forall
```

## 11 Sequential Composition Operator (;)
`(;) : (a:unit) -> 'b -> 'b`

use:
```F#
// semicolon is implied when on different lines, matters on single line
let foo = 
	printf "hello";
	printf "world";
	42
```


## 12 Avoiding Imperative Control Flow
![[Pasted image 20250321155742.png|500]]
Only time when these loops makes sense is its yielding values from a sequence.

## 13 Alternatives:
![[Pasted image 20250321155916.png]]
