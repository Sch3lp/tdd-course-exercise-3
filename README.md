
# TDD Lab Exercise 3

Exercises for http://sch3lp.github.io/tdd-course

## Technology

Preferably Java. Test Harnass with [JUnit5](https://junit.org/junit5/docs/current/user-guide/#writing-tests). Assertions with [AssertJ](http://joel-costigliola.github.io/assertj/).


## Assignment

We're going to be implementing a simplistic spreadsheet program.

Finish one story at a time and always apply Test First!

Make at least one commit per story!

### Unit tests

We did not supply **any tests** so you'll have to do your very best...

**Ok but what do I test exactly?**

![](test-all-the-things.jpg)

Happy path, edge cases, logic, ...

### Story 1: Simple spreadsheet

- A spreadsheet should be able to contain an unlimited amount of rows and columns
- A Row is identified with a number from 1 onwards...
- A Column is identified with a letter: A -> Z, AA -> ZZ, ...
- Cells are empty by default (`""`, not `null` or `undefined`)
- Cells should be able to store text
- You should be able to read a cell's contents

### Story 2: Numerical & literal values

- Cells with numerical content are evaluated automatically:
- Text `"  124  "` (with spaces) becomes the number `124` (without spaces)
- You should be able to read the literal contents of a cell
- Cell with text `"  124  "` has a literal value of `"  124  "` and value of `124`

### Story 3: Formulas

- `"=234"` is a formula, `" =234"` (space) is plain text
- The value of formula `"=234"` is the number `234`. Its literal value is the formula itself
- Kinds:
    - Constants `=124`
    - Wrapped with braces `=((124))`
    - Simple calculations `=3+5`, `=5-3`, `=4*2`
    - Complex calculations `=7*(2+3)*((((2+1))))`

Tip: don't try to evaluate the calculations above by yourself. You can use Java's _Nashorn JS_:

```java
ScriptEngineManager factory = new ScriptEngineManager();
ScriptEngine engine = factory.getEngineByName("nashorn");
engine.eval('4 + 5');
```

In Javascript it's simply a matter of using `eval()`.

### Story 4: Catching formula errors

When a formula contains an error, the value of the cell should be `**#ERROR**`.

### Story 5: References

When cell `A1` has a literal value of `=A2`:

- The value should be the value that is pointed to.
- When the value in A2 changes, the value in A1 changes as well.
- References to references should be possible! A1 -> A2 -> A3
- Circular references are impossible and should have `**#CIRCULAR**` as value.

### Story 6: Functions

For example: `=SUM(A1:A6)`.

- Provide a summing function that can be called with `SUM(RANGE)` as a literal value
- Provide an averaging function that can be called with `AVERAGE(RANGE)` as a literal value

