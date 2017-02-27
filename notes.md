# Launch School Course 210

## JavaScript Basics

### Data Types

In ES5, there are five primitive data types:

- number
- boolean
- string
- null
- undefined

and one compound data type:

- object

We can use the `typeof` operator to get the data type of any value:

```javascript
typeof 1.2      // "number"
typeof 'hello'  // "string"
typeof false    // "boolean"
```

#### Number

JS uses 64 bits to store numbers, which means the largest number we can use in a JS program is 9,223,372,036,854,775,807. Since JS uses double precision floats, a number that can be precisely stored is 9,007,199,254,740,991 (see: `Number.MAX_SAFE_INTEGER`). The maximum numeric value that can be represented is 1.7976931348623157e+308 (`Number.MAX_VALUE`). Any number greater is represented as `Infinity`.

Numbers support basic arithmetic operations, including `+`, `-`, `*`, and `/`. JS uses a floating point system to represent all numbers. This is unlike other programming languages that use different types to represent int, float, double, real, or decimal values.

Floating point values cannot precisely represent values because of how the computer represents them. This is true for all programming languages that store numbers this way. This results in the occasional rounding error. For example, in JS, `0.1 + 0.2` returns `0.30000000000000004`, rather than `0.3`. The best practice is to avoid fractional numbers as much as you can, instead using an integer number for the smallest relevant units. For example, when working with money, we always want to represent the amount in cents.

There are a few special number values:

- `Infinity`: when you need a number that's greater than any other number.
- `-Infinity`: when you need a number that's less than any other number.
- `NaN`: means "not a number." You will see `NaN` when a math function encounters an error.

#### Boolean

True and false. Comparison operations return boolean values.

#### String

A `String` is a sequence of characters and is used to represent text in JS. In JS, strings can contain any amount of text. We can double quote and single quote strings--unlike in Ruby, there is no distinction between either representation.

A common string operation is concatenation, which joins one string to another. We use the `+` operator for this:

```javascript
'Hello' + ' World'; // "Hello World"
```

### More on Strings

#### Special Characters

Strings can hold any character in UTF-16. We need escape sequences for formatting characters:

```javascript
var multiline = 'This string\nspans multiple lines.';
```

Here are some escape characters:

Code | Character
--- | ---
`\n` | New line
`\t` | Tab
`\r` | Carriage return
`\v` | Vertical tab
`\b` | Backspace

We may need to sometimes escape standard characters. For instance, if we need to use single quotes in a single-quote-delimited string, then we need to escape those single quote characters.

```javascript
'It\'s easy to use contractions in JS!'
```

#### String Concatenation

If you want to append content to an existing string, you can use __concatenation__. We use the `+` symbol for that.

```javascript
var firstName = 'John';
var lastName = 'Doe';
firstName + ' ' + lastName; // 'John Doe'
```

#### Character Access

We can call methods on strings and string literals. For example, we can use the `charAt()` method to get the character at a given index:

```javascript
'hello'.charAt(1); // 'e'
```

We can use brackets for that too:

```javascript
'hello'[1] // 'e'
```

JS uses 0-based indexing.

#### String Length

Strings also have a `length` property:

```javascript
'hello'.length; // 5
```

#### Working with long strings

We can use concatenation for long strings to make them easier to read in code. JS also lets us use `\` at the end of each line, which tells JS to ignore the following newline and concatenate the next line to the current string. The trouble is that if there are any spaces or tabs after the `\`, JS will treat them as literal spaces or tabs, and include them in the string.

### Primitive Values are Immutable

All JS primitives are immutable, which means we cannot change them once we create them. When we perform an operation that appears to change them, we are simply creating a new instance of that type and re-assigning variables to them as we use them. JS will not re-assign them on its own, though. We have to do that ourselves.

```javascript
a = 'hello';
a.toUpperCase();  // returns 'HELLO', but a isn't changed
a;                // still 'hello'
```

### Variables

JS uses variables to store values. It's good to give these descriptive names.

#### Naming Variables

"Variable naming is known as one of the most difficult tasks in computer programming. When you are naming variables, think hard about the names. Try your best to make sure that the name you assign your variable is accurately descriptive and understandable to another programmer. Sometimes that other programmer is yourself months or years later!"

Guidlines:

- JS is case-sensitive: `myVariable` is not the same as `myvariable`.
- Variable names can be of any length.
- It must start with a Unicode letter, the underscore `_` or dollar sign `$`.
- Succeeding letters must be Unicode letters, numbers, or underscores.
- It must not be a reserved word.

The following are valid variable names:

```
_count
$price
value
my_var
otherVar
```

Here are invalid var names:

```
1count
my#var
```

#### Declaring Vars

Variables are declared before they are used. there is a subtle but important difference between declared and undeclared names which we'll discuss later. In JS, they are declared using `var`.

```javascript
var myVariable;
```

#### Variable Assignment

We use `=` to assign a value to a var.

```javascript
var number;

number = 3;
```

You can also combine the variable declaration with an assignment:

```javascript
var myVar = 'Hello world';
```

A variable that is declared but not assigned is initialized to `undefined`.

```javascript
var foo;
foo; // undefined
```

#### Dynamic Typing

JS is dynamically typed, which means a variable can hold a reference to any data type and can be reassigned to a different type without error. A var in JS is just the name for a particular value at a particular time.

```javascript
var myVar = 'hello world';
myVar = 23;
myVar // 23
```

### Operators

An operator is a symbol that tells the computer to perform operations on values (operands). JS has lots of operators.

#### Arithmetic Operators

The usual suspects are here: `+`, `-`, `*`, and `/`. `%` is an operator in JS, but it isn't the same as it is in other languages (modulo). Instead, it returns the remainder of int division. With positive integers, there is no distinction between it and `mod`. When one number is negative, however, we get something different. In JS, e.g., `10 % -3` returns `1`. In mod division, the same operation returns `-2`.

#### Assignment Operators

Just like other languages, JS gives us compound assignment operators.

Name | Operator | Long Form Meaning
--- | --- | ---
Assignment | `a = b` | `a = b`
Addition Assignment | `a += b` | `a = a + b`
Subtraction Assignment | `a -= b` | `a = a - b`
Mult. Assignment | `a *= b` | `a = a * b`
Division Assignment | `a /= b` | `a = a / b`
Remainder Assignment | `a &= b` | `a = a % b`

#### Comparison Operators

Comparison operators return boolean values. When the operands are of different types, JS tries to coerce them into suitable types. This is a source of a lot of confusion and bugs, so it's recommended that we use the comparison operators that don't use type coercion. `==` and `!=` perform this coercion, while `===` and `!==` are their "strict" equivalents, which do not perform type coercion.

Operator | Description
--- | ---
`==` | True if the operands are equal
`!=` | True if the operands are not equal
`===` | True if the operands are equal and of the same type
`!==` | True if the operands are not equal and of the same type
`>` | True if the left is greater than the right
`<` | True if the left is less than the right

#### String operators

We can compare strings like numbers. A string is less than another string if its characters appear before the other's in Unicode lexicographical ordering. This is roughly simlar to alphabetical ordering, but all of the uppercase letters appear before all of the lowercase letters. `'a' > 'A'` will return true.

Strings also support the compound `+=` operator.

```javascript
var a = 'Hello';
a += ' world';

a; // 'Hello world'
```

#### Logical Operators

Boolean values can be combined using logical operators `&&`, `||`, and `!`. Non-boolean values can be used in these operations, and we'll discuss this use case later on. The operators work as you'd expect.

### Expressions and Statements

#### Expressions

An expression is any valid code that resolves to a value.

```javascript
'hello';
10 + 13;
sum = 10; // Assignments are expressions too!
```

Expressions can be put anywhere that JavaScript expects or allows a value.

##### Operator Precedence

JS's precidence rules are similar to those in other langs. That is, multiplication and division before addition and subtraction. Parens override this.

##### Increment and Decrement Oprators in Expressions

`++` and `--` operators increment or decrement their operands by 1. These can appear either before or after the operand. This doesn't matter when used as a standalone expression.

```javascript
var a = 1;
a++; // same as "a = a + 1"; a is now 2
++a;        // same as "a = a + 1"; a is now 3
a--;        // same as "a = a - 1"; a is now 2
--a;        // same as "a = a - 1"; a is now 1
```

However, they behave differently if they are part of a more complex expression.

- If the operator appears after the operand, JS evaluates the expression, then modifies the operand.
- If the operator appears before the operand, JS modifies the operand and then evaluates the expression.

```javascript
var a;
var b;
var c;

a = 1;
b = a++; // equal to "b = a; a++;". So now b is 1 and a is 2.
c = ++a; // equal to "++a; c = a;". So now c is 3 and a is 3.
```

##### Logical Short Circuit Evaluation in Expressions

When an expression contains `&&` or `||`, JS evaluates them using "short circuit" rules similar to other langs.

- For an expression like a || b, if a is true, the result is always true. Since it does not need to evaluate b to make this determination, JavaScript short circuits the evaluation and returns true without evaluating b.
- As with a && b, JavaScript short circuits the evaluation if a is false, and returns false without evaluating b.

```javascript
var a = true;
var b = false;

a || (b = true);      // b is still false after this, because (b = true) is never evaluated
b && (a = 1);         // a is still true after this, because (a = 1) is never evaluated
```

#### Statements

Unlike expressions, statements in JS don't necessarily resolve into a value. Statements generally control the execution of a program. For example, var assignments are expressions, but var declarations are statments.

Other types of statements include `if/else`, `switch`, `while`, and `for`. Statements help to "do something" rather than giving a value to use.

### Input and Output

Use `prompt()` to prompt the user for some text. Use `alert()` to display some text to the user. You can also output text to the console using `console.log()`. Each of these takes a string as an argument. `prompt()` returns a value, which is whatever the user entered.

### Explicit Primitive Type Coercions

Sometimes we want to convert some values to different types. For example, `"2"` to `2`. This is called "coercion" or "conversion." Since primitives are immutable, JS doesn't actually convert values. Instead, these actions return a new value of the proper type.

#### Converting Strings to Numbers

We can use `Number()` to turn strings that contain a Numeric value to a Number.

```javascript
Number('1'); // 1
```

If a string can't be converted, it'll return `NaN`.

```javascript
Number('abc123'); // NaN
```

The `parseInt()` and `parseFloat()` global functions turn Strings into Number. They work similarly to `#to_i` and `#to_f` in Ruby--the former will only handle the Integer part of the string.

```javascript
parseInt('123');       // 123
parseInt('123.12');    // 123, will only return whole numbers
parseFloat('123.12');  // 123.12, can handle floating point values
```

#### Converting Numbers to Strings

Use `String()`.

```javascript
String(123);  // '123'
String(1.23); // '1.23'
```

Numbers also have a `toString()` method:

```javascript
(123).toString(); // '123'
```

We can convert a number to a string by using the `+` operator to add it to a string, but we should avoid this.

```javascript
123 + ''; // '123'
```

#### Booleans to Strings

To turn boolean values to strings, use `String()`.

```javascript
String(true); // 'true'
```

Booleans have a `toString` method attached, as well.

```javascript
false.toString();
```

#### Primitives to Booleans

If you have a string representation of a boolean, then just compare it with `'true'` to determine whether that string is `'true'` or `'false'`.

There is no direct coercion of Strings to Booleans, so you have to compare it to the string values.

You can use the `Boolean()` global function to convert to a boolean value based on the truthy and falsy rules in JS. In JS, all values are truthy with the exception of `null`, `NaN`, `0`, `''` (an empty string), `undefined`, and `false`. Note that the string `'false'` is a truthy value!

The double bang works the same as it does in Ruby

```javascript
!!(0); // false
```

### Implicit Primitive Type Coercions

Here are some examples of implicit primitive type coercions.

```javascript
1 + true       // true is coerced to the number 1, so the result is 2
'4' + 3        // 3 is coerced to the string "3", so the result is "43"
false == 0     // false is coerced to the number 0, so the result is true
```

This is one of the shitty things about JS--it makes the code bug-prone and not very expressive. They should be avoided. Here are some examples of this.

#### The Plus Operator

The unary `+` operator will try to convert values into numbers:

```javascript
+('123');   // 123
+('');      // 0
+(null);    // 0
+('a');     // NaN
```

The binary `+` operator, as we have seen, is used for both addition for numbers and concatenation for strings. When we give it mixed operands that include a string, JavaScript tries to convert the other operand to a string as well.

```javascript
1 + true // 2
'123' + 123 // '123123'
123 + '123' // '123123'
'a' + null  // 'anull' - null is coerced to a string
```

#### Other Arithmetic Operators

The other operators are only defined for numbers, so JS will try to coerce both operands to numbers.

```javascript
1 - true      // 0
'123' * 3     // 369 - the string is coerced to a number
'8' - '1'     // 7
```

#### Relational Operators

`>`, `<`, `>=`, and `<=` are defined for numbers and strings. JS will try to coerce the opration into a number coparison unless both operands are strings.

```javascript
11 > '9' // true - '9' is coerced into 9.
123 > 'a' // false - 'a' is coerced to NaN; any number comparison with NaN is false
123 <= 'a' // also false
```

#### Equality Operators

JS provides non-strict and strict equality operators. Strict operators don't perform type coercions; non-strict operators have a set of complex rules to coerce types before performing the comparison.

##### Non-strict equality operstors

```javascript
0 == false // true - false is coerced into number 0
'' == undefined // false - undefined is coerced to 'undefined'
'' == 0 // true - '' is coerced to 0
true == 1 // true - comprisons between a bool and a non-bool will coerce bools into numbers
'true' == true // false, and the source of many bugs
```

##### Strict equality operators

```javascript
0 === false // false
'' === undefined // false
'' ==== 0 // false
true === 1 // false
'true' === true // false
```

#### Best Practices

Understanding type coercions is important when you debug problems. When you write your programs, though, it's best to:

- Always use explicit type coercions
- Always use strict equality operators

Clearly show your intentions and be explicit.

### Conditionals

#### if...else

The if/else syntax looks like this:

```javascript
var score = 80;

if (score > 70) {
  console.log('Congratulations, you passed!');
}
```

Here's what's happening:

1. `score > 70` is evaluated to a boolean. Here, it's `true`.
2. `if (score > 70)` is a conditional statement. When it returns true, the block of code following the condition runs.
3. `{ console.log('Congratulations, you passed!'); }` is a block. A block groups statements and is delimited by curly braces. Blocks may have zero or more statements in them.

An `if` can have an optional `else` clause. If the statement passed to `if` is false, the `else` block runs.

```javascript
if (score > 70) {
  console.log('Congrats you passed');
}
else {
  console.log('Sorry but you should study.');
}
```

Another `if` statement may follow an `else` statement; this lets you test multiple conditions. In these cases, only the first statement that evaluates as true executes.

```javascript
if (condition1) {
  // statements
}
else if (condition2) {
  // statements
}
else if (condition3) {
  // statements
}
else {
  // statements
}
```

Conditions may be nested, but you should curb this as much as you can because it's ugly and hard to follow:

```javascript
if(condition1) {
  if (nestedCondition) {
    // statements
  }
  else {
    // statements
  }
}
else {
  // statements
}
```

#### Truthy and Falsy Values

When an expression in an `if` statement doesn't evaluate to `true` or `false`, JS does a conversion to a boolean based on a simple set of rules. The following are falsy values. All other values are truthy.

```javascript
false
null
undefined
0
NaN
''
```

When using logical operators, then, it isn't necessary to use `true` or `false` values.

```javascript
1 || 1; // 1 (`||` short circuits when the first value is true.)
1 && 2; // 2 (`&&` short circuits when the first value is false.)
```

#### Switch

A `switch` statement compares an expression with multiple `case` labels. When it finds a match, the statements following the matched case label are executed:

```javascript
var reaction = 'negative';

switch (reaction) {
  case 'positive':
    console.log('Positive!');
  case 'negative':
    console.log('Negative!');
  case 'undecided':
    console.log('Undecided!');
  default:
    console.log('Unknown!');
}
```

This will log the following output:

```
Negative!
Undecided!
Unknown!
```

The `switch` statement ran the code starting from the first match. Notice, though, that all following code was also executed. This is a tricky part of JS--fall-through happens when we don't add a `break` statement after each case. This is seen as a problem, since we typically only want to execute one of the case branches. Here's how we prevent it:

```javascript
var reaction = 'negative';

switch (reaction) {
  case 'positive':
    console.log('Positive!');
    break;
  case 'negative':
    console.log('Negative!');
    break;
  case 'undecided':
    console.log('Undecided!');
    break;
  default:
    console.log('Unknown!');
}
```

This will now only log the `'negative'` branch.

### Looping and Iteration

JS has loops.

#### The 'while' Loop

```javascript
while (condition) {
  // do something repeatedly
}
```

The condition is first evaluated, then executes the statements in the block if the condition evaluates to a truthy value. The condition is then re-evaluated, and the block is executed again if the condition is still truthy. This process repeats until the condition yields a falsy value.

```javascript
var counter = 0;
var limit = 10;

while (counter < limit) {
  console.log(counter);
  counter += 2;
}
```

#### Infinite loops

It's easy enough to see how we can make a `while` loop that never ends.

```javascript
var counter = 0;
var limit = 10;

while (counter < limit) {
  console.log(counter);
}
```

`counter` never changes, and so it will always be less than `limit`.

#### Break and Continue

```javascript
var counter = 0;
var limit = 10;

while (true) {
  counter += 2;
  if (counter > limit) {
    break;
  }

  console.log(counter);
}
```

`while (true)` will produce an infinite loop. However, we have a conditional inside the loop that calls a `break` statement when a condition is met. When `break` is called, then the currenly-running loop will stop executing.

The `continue` statement skips the current iteration of the loop and returns to the top of the loop:

```javascript
var counter = 0;
var limit = 10;

while (true) {
  counter += 2;
  if (counter === 4) {
    continue;
  }

  if (counter > limit) {
    break;
  }

  console.log(counter);
}
```

Here the program will log every even number from 2 to 10, skipping 4.

#### The 'do...while' Loop

The `do...while` loop is similar, but will guarantee at least one execution of the block, even if the condition passed to `while` is never met. That statement is evaluated at the END of the block, rather than at the beginning.

```javascript
var counter = 0;
var limit = 0;

do {
  console.log(counter);
  counter++;
} while (counter < limit);
```

#### `for` Loops

`for` loops combine the key elements of setting up a loop: the initial state, the condition, and whatever change needs to be made before re-evaluating the condition.

```javascript
for (initialExpression; condition; incrementExpression) {
  // do some stuff repeatedly
}
```

Many `for` loops use an "iterator" value, commonly `i` or `j`.

```javascript
for (var i = 0; i < 10; i++) {
  console.log(i);
}
```

Here's the flow of execution.

1. Execute the initialization statement. This statement may include variable declarations.
2. Evaluate the condition. The loop terminates if it yields a falsy value.
3. Execute the body of the loop.
4. Execute the increment expression.
5. Return to step 2 for the next iteration.

You can skip any of the three components of the `for` statement.

```javascript
var i = 0;
for (; i < 10; i++) {
  console.log(i);
}
```

```javascript
for (var i = 0; ; i++) {
  if (i < 10) {
    break;
  }

  console.log(i);
}
```

```javascript
for (var i = 0; i < 10; ) {
  console.log(i);
  i++;
}
```
