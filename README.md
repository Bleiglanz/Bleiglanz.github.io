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





## SQL

- Programming
- Databases

**Bold** and _Italic_ and `Code` text

[Link](url) and ![Image](src)
```

For more details see [GitHub Flavored Markdown](https://guides.github.com/features/mastering-markdown/).

### Jekyll Themes

Your Pages site will use the layout and styles from the Jekyll theme you have selected in your [repository settings](https://github.com/Bleiglanz/Bleiglanz.github.io/settings). The name of this theme is saved in the Jekyll `_config.yml` configuration file.

### Support or Contact

Having trouble with Pages? Check out our [documentation](https://help.github.com/categories/github-pages-basics/) or [contact support](https://github.com/contact) and we’ll help you sort it out.
