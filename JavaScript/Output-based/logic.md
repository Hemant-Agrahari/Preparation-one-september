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

Q.console.log({}=={})

Q.console.log({}==={})

Q.let obj = {a:1}
let copy = obj
copy.a=5;
console.log(copy.a)
Output: 5
Explanation: Objects are reference types. copy points to the same object as obj, so modifying copy.a also affects obj.a.

Q.print who age greater than 20
let people = [
  {
    name: "Rahul",
    age: 25,
    hobbies: ["cricket", "reading", "traveling"]
  },
  {
    name: "Sneha",
    age: 22,
    hobbies: ["painting", "dancing", "singing"]
  },
];

const res = people.map(res=>{
    if(res.age>20){
        console.log('name',res.name
        )
    }
})

Map always return array

Q.console.log(2+'2')
Ans:The + operator is used for both addition and string concatenation.
If either operand is a string, JavaScript converts the other into a string and concatenates.
2 + '2' → '2' + '2' → "22"

Q.console.log(2-'2')
The - operator is only for numeric subtraction, not concatenation.
JavaScript will try to convert '2' (string) into a number.
2 - '2' → 2 - 2 → 0

Q.console.log('2' + 2 - 2);
explain:
'2' + 2 → String concatenation happens first

'2' is a string, so 2 is converted to string.

Result: "22" (string).

Now "22" - 2 → subtraction

- only works with numbers.

JavaScript converts "22" into a number (22).

22 - 2 = 20.

✅ Output: 20 (number)

Q.console.log(true + true);   // 2   (true → 1)
Q.console.log(false + true);  // 1
Q.console.log(true - false);  // 1
Q.console.log(null + 1);       // 1    (null → 0)
Q.console.log(undefined + 1);  // NaN  (undefined → NaN)
Q.console.log([1,2] + [3,4]);   // "1,23,4" (arrays → strings → concat)
Q.console.log([] + []);         // ""   (empty string)
Q.console.log([] + {});         // "[object Object]"
Q.console.log({} + []);         // 0 or "[object Object]" (depends on JS engine)
Q.console.log('' == 0);        // true   (empty string → 0)
Qconsole.log('' === 0);       // false  (strict equality, no coercion)
Q.console.log(false == '0');   // true   (both → 0)
Q.console.log(false === '0');  // false
Q.console.log([0] == 0);       // true   ([0] → "0" → 0)
Q.console.log([1] == 1);       // true
Q.console.log([1,2] == '1,2'); // true   (array → string)

