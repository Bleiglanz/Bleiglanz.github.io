###Knowledge base

## Scala Collections

Use `+(k->v)` to add elements to a Map

## Scala Functions and Methods

Syntax for a lambda 
```scala
val lambda = (x:Int)=>expression
```
Note: the bracketes around `x:Int` are probably necessary

Suppose you have defined a funktion
```scala
def f(x:Type):ResultType = expression
```
then the literal `f` cannot be used as a value (because the compiler would like to apply this to some argument),
use Eta-expansion in this situation
```scala
val fAsLambda = f _
```
The underscore transforms the function to a lambda value.

## Scala implicits
If one declares a variable 
```scala
implicit val foo = 3
```
it will be sucked into implicit parameters of functions.

## Scala Traversable
Important methods
```scala
++  // left followed by right, left determines type of result
++: // left followed by right, right determans type of result
/:  // fold left
:\  // fold right
addString     // add everything to StringBuilder
aggregate     // aggregate using to operators (B,A)=>B (like map) and (B,B)=>B (like fold)
              // more general than fold or reduce
collect       // apply a partial function
collectFirst  // apply a partial function to the first element where it is defined
companion     // factory companion to build Traversable
copyToArray   // copies elements to Array
copyToBuffer  // copies elements to Buffer
count         // number of elements for which predicate is true
drop          // new collection with all but the first n
dropWhile     // drop elements not satisfying a predicate
exists        // does there exist an element satisfying this predicate
filter        // ignore some
filterNot     // invert given predicate
find          // headOption circ filter (find the first)
flatMap       // apply collection producing function and flatten
flatten       // remove package level
fold          // use associative binary operator
foldLeft      // /:
foldRight     // :\
forall        // do all elements satisfy the predicate?
```
## Scala Curry
If you want real currying, then define your function like this
```scala 
def foo(x:Int)(y:Int):ResType = ... 
def hoo = f(3)(_:Int) 
def normalf(a:Int):Res = ...
def normalc = (f_).curried
```
In this case ```scala foo(3)``` evaluates to a function from integers to Restype!
Nice application: Since we can write single arguments with curly braces, a definition like
```scala 
def repeate(x:Int)(x :=> Unit):ResType = ... 
```
gives you a way to create a nice syntax like ```scala repeat(3){block}```


## Scala Implicits
There are implicit functions arguments, there are implicit values (single named in scope)
and there are implicit conversions to allow reciever conversion `3.getFibonacci` is not defined,
but the `3` can be automatically converted to something that understands the method call.

## Scala Lists
A list is a cons cell. First element is a A, second element is a List
`Nil` is the empty list, of type `Nothing`, and `List(1)==1::Nil`

## Scala case classes
Nice: `apply, unapply, copy, equals, hashcode, toString`
Nice: don't have to use `new`
Jargon: Lenses are a pattern for copying in deeply nested structures

## Scala for comprehension
```scala
for(variable <- generator) yield ...       // map
for(variable <- generator) { sideeffect }  // foreach
for(variable <- generator if variable ...) // withFilter
for(a <- g1, b<- g2)...                    // flatMap
```

## for comprehension together with Option
clarify



## Github

Store your password
```
$ git config credential.helper store
$ git push https://github.com/repo.git

Username for 'https://github.com': <USERNAME>
Password for 'https://USERNAME@github.com': <PASSWORD>`
```
Also see [this]([https://help.github.com/articles/changing-a-remote-s-url/#switching-remote-urls-from-https-to-ssh)


## Emacs
```
CxCf open file
CxCv open alternate file
Cxi  insert file
CxCs save file
CxCw write file (new name)
CxCc exit
Cf   forward
Cb   backward
Cp   lineup
Cn   linedown
Mf   next word
Mb   prev word
Ca   beginning of line
Ce   end of line
Me   forward sentence
Ma   backward sentence
Cv   scroll up
Mv   scroll down
M<   begin
M>   end
     Mx goto-line
     Mx goto-char
M<n> repeat next cmd n times
Cu<n>repeat next 4 times (without n) or n times
Cd   delete char
DEL  delete left
Md   delete word
MDEL delete left word
Cy   yank
Cw   cut region
CxCx exchange pint and mark
Mx   kill ring save (what others call copy)
Cxh  mark buffer
My   yank-pop
M!   shell command
Co   other window
Mp   in shell: repeat command
```


## Trash
- Programming
- Databases

**Bold** and _Italic_ and `Code` text

[Link](url) 
and ![Image](https://www.scala-lang.org/resources/img/frontpage/scala-spiral.png)


For more details see [GitHub Flavored Markdown](https://guides.github.com/features/mastering-markdown/).

### Jekyll Themes

Your Pages site will use the layout and styles from the Jekyll theme you have selected in your [repository settings](https://github.com/Bleiglanz/Bleiglanz.github.io/settings). The name of this theme is saved in the Jekyll `_config.yml` configuration file.

### Support or Contact

Having trouble with Pages? Check out our [documentation](https://help.github.com/categories/github-pages-basics/) or [contact support](https://github.com/contact) and we’ll help you sort it out.

# Rust

## General stuff

Tools: rustc, rustup, cargo, rustfmt,...

Rust uses snake_case_format

Rust uses 4-space indent

Create a new runable with `cargo new --bin name_of_prj`

Create a new library with `cargo new --lib name_of_lib`

If directory already exists, use `init` instead of `new`

`rustup update; cargo update`, important if nightly is used

`cargo run` builds an runs a binary app

shortcut `cargo b r t`...

Rust uses a simple directory layout (source files are in `src`)

Configuration is in `Cargo.toml`

Command line arguments in `std::env::args`

Results are `OK(value)` or `Err(e)`, just use `unwrap()` to panic if something is wrong

To bring names into scope, use `use`

## Variables

`let variable_name:Type = ...` is the standard way to bind a name to a value

`let mut variable_name:Type = ...` creates something mutable

## Expressions

`while` as usual

`for x in iter` as usual, for arrays create an iterator with `.iter()`

`if cond {} else {}` has no `(...)` for condition, it is an *expression* with a value

`loop` is infinite, has to have a `break`

blocks `{}` are values, the last expression should have no `;`

statements are terminated by `;`, they don't have a value

## Functions

```
fn tolstoi (arg:Type, arg2:Type) -> ResultType {

}
```
typically the last expression isn't followed by an `;`, in this case it is the result.
Think about the last semicolon in the function body!

## Macros

can be recognized by `!` at the end of the name `println!`, `assert!`

## Attributes=Annotations
```
#[test] 
fn test_this(){
    assert_eq!(1,1);
}
```
can be used, in this case a unit test (typically in the same source)
also: annotate the module ```#[cfg(test)]```
j

## Strings

```
    let mut s:String = "Hallo".to_string(); // String literals are refs, have to be converted?
    let p:&str   = "Foo";
```
Hm, String literals are ref by nature!

## Misc

`use` only brings things into scope, does not include anything

`let mut` und `let` assignment, also ownership implied, `const` for constants

`for x in coll` for loop

`std::env::args` is iterator for command line arguments

`unwrap` means just panic if not ok

`expect` also panics, but additional message

`Result` is an enum with `Ok(x)` and `Err(e)` as values

`&name` und `&mut name` just borrows, ownership untouched, deref with `*`

method calls `o.meth()` automatically derefs

raw string with `r#""#`

serialization -> serde

modules: careful `mod name` and `pub mod name`

arrays `[1,2,3,4]` fixed length (at compile time!), fixed types, on the stack

arrays index access `a[i]` is checked at runtime

array init `[0;1000]` semicolon to seperate default value

tuples `[1,"test"]` as usual, index starts with 0

one element tuple with `(1,)` because otherwise evaluation with brackets

every block has a value, if last expr doesn't have a semicolon

`for n in 0..8` has 8 elements, makes easy slicing...

`for x in xyz.iter()` often necessary

use underscore `_` for unused values

`format print write eprint` essentially the same (output varies)

casting is done via `expr as i64` -> From trait

a `?` inside a function body at a `Result<A,B>` return `Err(b)` at failure

closures syntax is `|x|{ body }`, use `move` if capture owership necessary

pattern matching in let statements `let (a,b) = fnreturnstuple();`, also for enums,..

rust allows shadowing, i.e. reassignment -> do this if type changes (unproblematic)

statement `let x=5;` has no value, contrast with expression -> a semicolon means something!

flow `loop{}` and `while cond {}` and `for x in coll {}`

slices have type `let x:&[T]=arr[0..n]`, always refs!

(index,value) pairs can be created with `...iter().enumerate()`

format for debugging with `{:?}`

use the `vec![init;len]` macro to initialize a vector

notice `&str` and `String` have no index acces (unicode), from `String` to `&str` automatically

a `&str` is a `&[u8]`, but contains only valid codepoints

collection `Vec<T>` allows slices, indexed access, etc.

also HashMap, BTreeMap, Set, ...

`coll.iter()` returns an iterator, is lazy (does nothing) - iterator has essentially one method: `next`

standard: `coll.iter().map().filter().collect()` everything is lazy, call collect at last

Rule of borrowing: `&` borrows a Ref, and `*` derefs it

Literal Strings `r##"?"##` is a raw String

rustup update to update toolchain

cargo search to search for packages

`pub mod myname {}` declares a public module

arrays have fixed length, can be initialized with `[27;10000]` (the size is a compile time constant)

tuples have mixed Types `(a,b,c)` has type `(A,B,C)`, access via `tuple.0,...,tuple.k`

if has no brackes around the condition, for loops with `for x in 3..7` or `for x in arr.iter()`

underscore for unused variable `_` or for a throwaway match while pattern matching

`format`, `print` and `write` use the same technology

type conversion allowed via `x as NewType` if possible

only inside a function can we use `stmt?` if the fn returns a Result. Then `Err(e)` is returned!

Lambdas (unnamed functions) via `|arglist|{body}`

the `let` is already pattern matching `let (a,b)=...`


