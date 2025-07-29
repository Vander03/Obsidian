## 1 Monoids

## 2 Monadic Types
`f: a -> M<a>` - monadic type (container for other values)
An example of a monadic type is the `type Option<'t> = Some of 't | None` modifier (optional existence).

Problem is that when two functions `f` and `g` of type `a -> M<a>` can no longer be directly composed. We need to extract `a` from the monadic type to pass it into the next function

### 2.1 Monadic Bind and Return Functions
`Bind: M<b> -> (b -> M<c>) -> M<c>`
Used to control functions
```F#
f: a -> M<b>
g: b -> M<c>
(f a) >>= g = Bind (f a) g : M<c>

a -> M<a> // unit function
// used for putting a value of type a into container M<a>
```

### 2.2 Builder Classes
Create monads by using a builder function that contains a Bind and Return function.
```F#
type MaybeBuilder() =
    member this.Bind(x, f) =
        match x with
        | Some(v) -> f v
        | _ -> None
    member this.Return(v) = Some v

```

## 3 Monad
Monads allow us to focus on the logic without overcomplicating the code with "housekeeping logic". They are a very versatile concept that can be used to represent:
- Collections such as lists and sets
- External State/Environment
- Continuations
- Asynchronous Computations
- LINQ like Query Expressions



Take the following function
```F#
let bar (a:int) (b:int) (c:int) = a + b / c
// if a, b and c were of type Option<'t>, we would need to check if every value is None before calcs

```

### 3.1 Computation Expression
Monads are used by Computation Expressions. 


```F#
// Create object of a builder class
let maybe = new MaybeBuilder()

// then use it to create computational expressions
let foo (oa:Option<int>) (ob:Option<int>) (oc:Option<int>) = 
    maybe { // writes a,b and c from its Monad structure to int a,b and c
        let! (a:int) = oa
        let! (b:int) = ob
        let! (c:int) = oc
        return (a + b / c)
        }

// binding to maybe in another way:
 maybe.Bind(oa, fun a ->
      maybe.Bind(ob, fun b ->
        maybe.Bind(oc, fun c-> 
            maybe.Return (a + b / c))))
```


### 3.2 Sequences as a Monad
F# sequences are just computational expressions that use the built-in Seq Monad 
`seq { yield x; yield! Range (lower+1) }`.
`yield` and `yield!` are two optional standard methods that Builder Classes can implement

![[Pasted image 20250330224133.png]]

## 4 Haskell

### 4.1 Monads In Haskell
Haskell has a monadic type named IO to represent actions that can change the  current state of the world.
File operations which depend on and change the current state of the file system use Monadic types in their signatures:
```F#
doesFileExist :: FilePath -> IO<bool>
removeFile :: FilePath -> IO<void>
putStrLn :: String -> IO<void>
getLine :: IO<String>
```

They can be sequenced using the Haskell do notation:
```F#
main :: IO<void>
main = do
    putStrLn "What is your name?"
    name <- getLine
    putStrLn ("Hello, " ++ name ++ "!")
```

#### 4.1.1 Pure Functional Programming in Haskell
![[Pasted image 20250330223625.png]]

### 4.2 Haskell List Comprehensions
![[Pasted image 20250330224406.png|400]]


## 5 Async
![[Pasted image 20250330223831.png|400]]
![[Pasted image 20250330223844.png|400]]


## 6 Setbuilder Notation
![[Pasted image 20250330224455.png]]

### 6.1 More List Comprehensions
![[Pasted image 20250330224530.png|500]]
