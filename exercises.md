# Launch School Course 210 - Exercises

## Javascript Basics

### Variables and Numbers

#### 1.

```javascript
var numerator = 10;
```

#### 2.

```javascript
var denominator = 2;
```

#### 3.

```javascript
var answer = numerator / denominator;
console.log(answer);
```

### Primitive Types and Type Coercion

```javascript
// 1.

var x = '13';
var y = 9;

console.log(x + y); // 139
console.log(Number(x) + y); // 22

// 2.

console.log(x * y); // 117

// 3.

var npa = 212;
var nxx = 555;
var num = 1212;

console.log('' + npa + nxx + num);

// 4.

console.log(String(npa) + String(nxx) + String(num));

// 5.

console.log(npa.toString() + nxx.toString() + num.toString());

var bool = true;
var arr = [1, 2, 3];

console.log(bool.toString()); //=> 'true'
console.log(arr.toString());  //=> '1,2,3'
```

### Operators and Conditionals

```javascript
// 1.

var apples = 3;
var bananas = 5;

if (apples == bananas) {
  console.log('Match!'); // Does not execute.
}

// 2.

bananas = '3';

if (apples == bananas) {
  console.log('Match!'); // Executes
}

// 3.

if (apples === bananas) {
  console.log('Match!'); // Does not execute
}

// 4.

if (apples === bananas) {
  console.log('Match!');
}
else {
  console.log('No match!'); // this one executes
}

// 5.

if (apples === bananas) {
  console.log('Match!');
}
else if (apples == bananas) {
  console.log('Kinda match!'); // This one executes.
}
else {
  console.log('No match!');
}

// 6.

if (apples === bananas) {
  console.log('Match!');
}
else {
  if (apples == bananas) {
    console.log('Kinda match!'); // This one executes.
  }
  else {
    console.log('No match!');
  }
}

// 7.

apples = 3;
bananas = 3;
var areEqual = apples === bananas;

console.log(areEqual);

// 8.

apples = 3;
bananas = undefined;
var eitherOr = apples || bananas;

console.log(eitherOr); // 3

// 9.

bananas = 1;

var eitherOr = apples || bananas;
console.log(eitherOr); // 3

var eitherOr = bananas || apples;
console.log(eitherOr); // 1


// 10.

var lastName = 'Guillen'
var familyMessage = lastName === 'Guillen' ? 'You\'re part of the family!' : 'You\'re not family!'
```
