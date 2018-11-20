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



