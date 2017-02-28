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

## Exercises: Logic and Flow Control

### Odd Numbers

```javascript
var logOddNumbers = function(max) {
  for (var i = 1; i <= max; i += 2) {
    console.log(i);
  }
};
```

### Multiples of 3 and 5

```javascript
var multiplesOfThreeAndFive = function() {
  for (var i = 1; i <= 100; i++) {
    if (i % 3 === 0 && i % 5 === 0) {
      console.log(i + '!');
    } else if (i % 3 === 0 || i % 5 === 0) {
      console.log(i);
    }
  }
};
```

### Print Multiples

```javascript
var logMultiples = function(num) {
  var multiples = [];

  for (var i = 1; i * num <= 100; i += 2) {
    multiples.push(i * num);
  }

  multiples.reverse().forEach(function(x) {
    console.log(x);
  });
};
```

### FizzBuzz

```javascript
var fizzBuzz = function() {
  for (var i = 1; i <= 100; i++) {
    var output = '';

    if (i % 3 === 0) {
      output += 'Fizz';
    }

    if (i % 5 === 0) {
      output += 'Buzz';
    }

    console.log(output || i);
  }
};
```

### Prime Check

```javascript
var isPrime = function(num) {
  if (num == 1) return false;
  if (num == 2) return true;
  if (num % 2 === 0) return false;

  for (var i = 3; i < Math.sqrt(num); i += 2) {
    if (num % i === 0) return false;
  }

  return true;
};
```

### XOR

```javascript
var isXor = function(p, q) {
  return !!((p || q) && !(p && q))
};
```

### Guessing the Password

```javascript
var password = 'password';
var guesses = 0;
var maxGuesses = 3;

while (guesses < maxGuesses) {
  var userGuess = prompt "What is the password?"

  if (userGuess === password) {
    break;
  }

  guesses++;
}

if (guesses === maxGuesses) {
  console.log('You have been denied access');
} else {
  console.log('You have successfully logged in.');
}
```

### Student Grade

```javascript
var score1 = Number(prompt('First score?'));
var score2 = Number(prompt('Second score?'));
var score3 = Number(prompat('Third score?'));
var sum = score1 + score2 + score3;
var avg = sum / 3;
var letterGrade;

if (avg >= 90) {
  letterGrade = 'A';
} else if (avg >= 70) {
  letterGrade = 'B';
} else if (avg >= 50) {
  letterGrade = 'C';
} else {
  letterGrade = 'F';
}

console.log('Based on the average of your 3 scores your letter grade is "' + letterGrade + '".');
```

### Greatest Common Divisor

```javascript
var gcd = function(num1, num2) {
  var min = function(num1, num2) {
    return num1 < num2 ? num1 : num2;
  };

  var max = min(num1, num2);
  var currentGCD = 1;

  for (var i = currentGCD + 1; i <= max; i++) {
    if (num1 % i === 0 && num2 % i === 0) {
      currentGCD = i;
    }
  }

  return currentGCD;
};
```

```javascript
var gcd = function(num1, num2) {
  while (num2 !== 0) {
    var temp = num2;
    num2 = num1 % num2;
    num1 = temp;
  }

  return num1;
};
```

### Pattern Generation

```javascript
var generatePattern = function(rows) {
  for (var i = 1; i <= rows; i++) {
    line = '';

    for (var j = 1; j <= rows; j++) {
      if (j <= i) {
        line += j;
      } else {
        line += '*';
      }
    }

    console.log(line);
  }
};
```

### Index of Substring

```javascript
function checkAtIndex(firstString, secondString, idx) {
  for (var secondIndex = 0; secondIndex < secondString.length; secondIndex++) {
    var firstIndex = secondIndex + idx;
    if (firstString[firstIndex] !== secondString[secondIndex]) return false;
  }

  return true;
}

function indexOf(firstString, secondString) {
  for (var i = 0; i <= firstString.length - secondString.length; i++) {
    if (checkAtIndex(firstString, secondString, i)) return i;
  }

  return -1;
}

function lastIndexOf(firstString, secondString) {
  var result = -1;

  for (var i = 0; i <= firstString.length - secondString.length; i++) {
    if (checkAtIndex(firstString, secondString, i)) result = i;
  }

  return result;
}
```

### Trimming Spaces

```javascript
function stripFirstChar(str) {
  var newStr = '';
  for (var i = 1; i < str.length; i++) {
    newStr += str[i];
  }

  return newStr;
}

function stripLastChar(str) {
  var newStr = '';
  for (var i = 0; i < str.length - 1; i++) {
    newStr += str[i];
  }

  return newStr;
}

function trim(str) {
  while (str[0] === ' ') {
    str = stripFirstChar(str);
  }

  while (str[str.length - 1] === ' ') {
    str = stripLastChar(str);
  }

  return str;
}
```

That was a slow method. Here's a faster way:

```javascript
function trim(str) {
  var start = 0;
  var end = str.length - 1;
  var newStr = '';

  while (str[start] === ' ') {
    start++;
  }

  while (str[end] === ' ') {
    end--;
  }

  while (start <= end) {
    newStr += str[start];
    start++;
  }

  return newStr;
}
```

### Splitting a String

```javascript
function splitString(string, delimiter) {
  if (delimiter === undefined) throw Error('No delimiter');

  var output = '';

  for (var i = 0; i < string.length; i++) {
    if (string[i] === delimiter) {
      console.log(output);
      output = '';
    } else if (delimiter === '') {
      console.log(string[i]);
    } else {
      output += string[i];
    }
  }

  if (output) console.log(output);
}
```

### Repeating Strings

```javascript
function repeat(string, times) {
  if (isNaN(times) || times < 0) return undefined;

  var output = '';
  while (times > 0) {
    output += string;
    times--;
  }

  return output;
}
```

### String startsWith

```javascript
function startsWith(string, searchString) {
  for (var i = 0; i < searchString.length; i++) {
    if (string[i] !== searchString[i]) return false;
  }

  return true;
}
```

### Converting Strings to Lower Case

```javascript
function toLowerCase(string) {
  var newString = '';
  var asciiNumeric;

  for (var i = 0; i < string.length; i++) {
    asciiNumeric = string.charCodeAt(i);

    if (asciiNumeric >= 65 && asciiNumeric <= 90) {
      newString += String.fromCharCode(asciiNumeric + 32);
    } else {
      newString += string[i];
    }
  }

  return newString;
}
```

### Substring (1)

```javascript
function substr(string, start, length) {
  var output = '';

  if (start < 0) start = string.length + start;

  for (var i = start; i < string.length && i < start + length; i++) {
    output += string[i];
  }

  return output;
}
```

### Substring (2)

```javascript
function substring(string, start, end) {
  var output = '';
  var temp;

  if (end === undefined) end = string.length;
  if (isNaN(start) || start < 0) start = 0;
  if (isNaN(end) || end < 0) end = 0;
  if (end < start) {
    temp = end;
    end = start;
    start = temp;
  }
  if (start > string.length) start = string.length;
  if (end > string.length) end = string.length;

  for (var i = start; i < end; i++) {
    output += string[i];
  }

  return output;
}
```

### Rot13

```javascript
function rot13(str) {
  function translatedChar(char) {
    var LOWER_CASE_START = 97;
    var LOWER_CASE_END = 122;
    var UPPER_CASE_START = 65;
    var UPPER_CASE_END = 90;
    var ALPHABET_SIZE = 26;
    var TRANSLATION_SIZE = 13;
    var charCode;

    if (typeof char === 'string') {
      charCode = char.charCodeAt(0);
    } else if (isNaN(char)) {
      throw TypeError('Char must be a String or a Number.');
    } else {
      charCode = char;
    }

    if (charCode >= LOWER_CASE_START && charCode <= LOWER_CASE_END) {
      charCode -= LOWER_CASE_START;
      charCode += TRANSLATION_SIZE;
      charCode %= ALPHABET_SIZE;
      charCode += LOWER_CASE_START;
    } else if (charCode >= UPPER_CASE_START && charCode <= UPPER_CASE_END) {
      charCode -= UPPER_CASE_START;
      charCode += TRANSLATION_SIZE;
      charCode %= ALPHABET_SIZE;
      charCode += UPPER_CASE_START;
    }

    return String.fromChrCode(charCode);
  }

  var result = '';

  for (var i = 0; i < str.length; i++) {
    result += translatedChar(str[i]);
  }

  return result;
}
```

## Arrays

### Array Operations

#### push, pop, shift, unshift

```javascript
// 1.

function push(arr, val) {
  arr[arr.length] = val;
  return arr.length;
}

// 2.

function pop(arr) {
  var result = arr[arr.length - 1];
  arr.length = arr.length - 1;
  return result;
}

// 3.

function unshift(arr, val) {
  for (var i = arr.length - 1; i >= 0; i--) {
    arr[i + 1] = arr[i];
  }

  arr[0] = val;
  return arr.length;
}

// 4.

function shift(arr) {
  var result = arr[0];
  var oldLength = arr.length;
  for (var i = 0; i < oldLength; i++) {
    arr[i] = arr[i + 1];
  }

  arr.length--;
  return result;
}
```

#### indexOf and lastIndexOf

```javascript
// 1.

function indexOf(arr, val) {
  for (var i = 0; i < arr.length; i++) {
    if (arr[i] === val) return i;
  }

  return -1;
}

// 2.

function lastIndexOf(arr, val) {
  var result = -1;

  for (var i = 0; i < arr.length; i++) {
    if (arr[i] === val) result = i;
  }

  return result;
}
```

#### slice, splice, concat, and join

```javascript
// 1.

function slice(arr, start, end) {
  var newArr = [];

  for (var i = start; i < end; i++) {
    newArr[i - start] = arr[i];
  }

  return newArr;
}
```

## Objects

### Properties

```javascript
// 4.

function wordCount(str) {
  var words = str.split(' ');
  var counts = {};
  var word;

  for (var i = 0; i < words.length; i++) {
    word = words[i];
    if (counts[word]) {
      counts[word] += 1;
    } else {
      counts[word] = 1;
    }
  }

  return counts;
}
```
