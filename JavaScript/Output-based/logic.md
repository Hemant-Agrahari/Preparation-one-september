Q.console.log('2'==2)
Output: true
Explanation: The == operator checks value equality with type coercion, so the string '2' is converted to number 2 before comparison.

Q.console.log('2'===2)
Output: false
Explanation: The === operator checks strict equality, so no type coercion occurs. '2' is a string and 2 is a number, so they are not equal.

Q.console.log([]==[])
Output: false
Explanation: Arrays are reference types, and == compares references. Two different empty arrays do not reference the same object, so it returns false.

Q.console.log([]===[])
Output: false
Explanation: Same as above — === compares references, and two separate empty arrays are different objects in memory.

Q.console.log([1,2,3]+[5,6,7])
Output: '1,2,35,6,7' (a string)
Explanation: The + operator concatenates arrays as strings. Each array is converted to a string '1,2,3' and '5,6,7', then concatenated.

Q.console.log(0.1+0.2 === 0.3)
Output: false
Explanation: Floating-point numbers in JavaScript are not always exact due to binary representation. 0.1 + 0.2 evaluates to 0.30000000000000004.

Q.let obj = {a:1}
let copy = obj
copy.a=5;
console.log(copy.a)
Output: 5
Explanation: Objects are reference types. copy points to the same object as obj, so modifying copy.a also affects obj.a.