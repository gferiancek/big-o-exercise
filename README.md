# Part 1: Simplifying Expressions
Simplify the following big O expressions as much as possible:

## O(n + 10)
O(n)

## O(100 * n)
O(n)

## O(25)
O(1)

## O(n<sup>2</sup> + n<sup>3</sup>)
O(n<sup>2</sup>)
( Correct answer: O(n^3) I assumed it would work like O(534) = O(1), but I can see how an extra exponet value has a far larger
impact than extra constants. )

## O(n + n + n + n)
O(n)

## O(1000 * log(n) + n)
O(n)

## O(1000 * n * log(n) + n)
O(n log(n))

## O(2<sup>n</sup> + n<sup>2</sup>)
O(2<sup>n</sup>)

## O(5 + 3 + 1)
O(1)

## O(n + n<sup>(1/2)</sup> + n<sup>2</sup> + n * log(n)<sup>10</sup>)
O(n<sup>2</sup>)

# Part 2: Calculating Time Complexity
Determine the time complexities for each of the following functions.

## logUpTo()
```
function logUpTo(n) {
  for (let i = 1; i <= n; i++;) {
    console.log(i)
  }
}
```
O(n) - Looping n times.

## logAtLeast10()
```
function logAtLeast10(n) {
  for (let i = 1; i <= Math.max(n, 10); i++) {
    console.log(i);
  }
}
```
O(n) - While n < 10 means we're at a constant of 10, anything above that scales with n.

## logAtMost10()
```
function logAtMost10(n) {
  for (let i = 1; i <= Math.min(n, 10); i++) {
    console.log(i)
  }
}
```
O(1) - While we scale with n with low values, anything over 10 is constant.

## onlyElementsAtEvenIndex()
```
function onlyElementsAtEvenIndex(array) {
  let newArray = [];
  for (let i = 0; i < array.length; i++) {
    if (i % 2 === 0) {
      newArray.push(array[i]);
    }
  }
  return newArray;
}
```
O(n) - Looping n times, % + push are constant.

## subtotals()
```
function subtotals(array) {
  let subtotalArray = [];
  for (let i = 0; i < array.length; i++) {
    let subtotal = 0;
    for (let j = 0; j <= i; j++) {
      subtotal += array[j];
    }
    subtotalArray.push(subtotal);
  }
  return subtotalArray;
}
```
O(n<sup>2</sup>) - While initial j loops are small, by the end of it we loop both i + j *n* times.

## vowelCount()
```
function vowelCount(str) {
  let vowelCount = {};
  const vowels = 'aeiouAEIOU';

  for (let char of str) {
    if (vowels.includes(char)) {
      if (char in vowelCount) {
        vowelCount[char] += 1;
      } else {
        vowelCount[char] = 1;
      }
    }
  }
  return vowelCount;
}
```
O(n) - Looping n times and while includes is O(n) it's on a fixed string, making it constant. Accessing object with keys is also constant.

# Part 3: Short Answer

## True or False: n<sup>2</sup> + n is O(n<sup>2</sup>)
True - + n is the smaller portion and can be omitted.

## True or False: n<sup>2</sup> * n is O(n<sup>3</sup>)
False - n<sup>2</sup> vs n<sup>3</sup> is irrelevant, so it can be reduced to n<sub>2</sup>.
( Correct Answer: True. As noted in Part 1, I assumed n^3 reduced to n^2. )

## True or False: n<sup>2</sup> + n is O(n)
False - n is the small portion an is omitted, leaving O(n<sup>2</sup>).

## What's the time complexity of the .indexOf array method?
O(n) - `indexOf()` needs to loop through each item in the array.

## What's the time complexity of the .includes array method?
O(n) - `includes()` also needs to loop through each item in the array.

## What's the time complexity of the forEAch array method?
O(n) - As the name implies, `forEach()` will loop through each item in the array! (Though, what you put inside of your `forEach()` block could potentially increase the time complexity.)

## What's the time complexity of the .sort array method?
O(n log n) - I'm not 100% certain on this one, as it can vary depending on the sort criteria. Colt did say that at best, sorting is O(n log n) though, so I'd think the main sort function would at least target that.

## What's the time complexity of the .unshift array method?
O(n) - You need to increase the indicies of each exisiting element, so you work on each item in array.

## What's the time complexity of the .push array method?
O(1) - Adding to the end of an array only deals with the item you're pushing, so its constant.

## What's the time complexity of the .splice array method?
O(n) - Similar to `unshift()`. `splice()` could be a simple index access, or you could rework the entire array, so at worst case it's O(n).

## What's the time complexity of the .pop array method?
O(1) - `pop()` only affects the last item, which you can access by index.

## What's the time complexity of the Object.keys() function?
O(n) - You need to grab each key, so it's propotional to the # of keys.

## Bonus - What's the space complexity of the Object.keys() function?
O(n) - Size of array depends on the # of keys in the object.
