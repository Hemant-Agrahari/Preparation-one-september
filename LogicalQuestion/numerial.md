Q.Write a program to print 1 to 10 number.
function printNumber(num){
for(let i= 1 ;i <= num;i++){
console.log(i)
}
}

printNumber(12);

Q.Write a program to print even number.
function printNumber(num){
count=0;
for(let i= 1 ;i <= num;i++){
if(i%2 === 0){
console.log(i);
count++;
}
}
console.log('Total Event count :',count)
}
printNumber(12);
Q.Write a program to print odd number.

function printOddNumber(num){
count=0;
for(let i= 1 ;i <= num;i++){
if(i%2 != 0){
console.log(i);
count++;
}
}
console.log('Total odd count :',count)
}

printOddNumber(12);

Q.Write a program to find the largest number in a array without inbuild function.

const findLargestNumberInArray=(arr)=>{
let largestValue = arr[0]
for(let i = 1;i<=arr.length;i++){
if(arr[i] > largestValue){
largestValue =arr[i]
}
}
return largestValue
}

console.log(findLargestNumberInArray([2,3,4,78,4,3]))

Q.Write a program to find the second largest number in an array.

function printSecondLargestNumber(arr){
arr.sort((a,b)=>b-a)
for(let i = 1;i<=arr.length;i++){
if(arr[i] !== arr[0])
return arr[i]
}

}

console.log(printSecondLargestNumber([3,4,5,6,7,8]));

Q.Reverse a string without using built-in methods.

function reverseString(str) {
let reversed = "";
// loop from end to start
for (let i = str.length - 1; i >= 0; i--) {
reversed += str[i]; // add characters one by one
}

return reversed;
}

// Example
console.log(reverseString("hello")); // "olleh"
console.log(reverseString("frontend developer")); // "dnetnorf"

Q.Write a function that reverse the sentence word not sentence.
Input:"Hemant Kumar Agrahari"
Output:"tnameh ramuk irahargA"

function reverseWords(sentence) {
return sentence
.split(" ") // split into words ["Hemant","Kumar","Agrahari"]
.map(word => word.split("") // split each word into chars
.reverse() // reverse chars
.join("")) // join back to string
.join(" "); // join words with space
}

console.log(reverseWords("Hemant Kumar Agrahari"));
// Output: "tnameH ramuK iraharagA"

Q.Write a function for make capital only first letter of a sentence each word.
input:hemant kumar agrahari
output:Hemant Kumar Agrahari

function capitalizeWords(sentence) {
return sentence
.split(" ")
.map(word => word.charAt(0).toUpperCase() + word.slice(1))
.join(" ");
}

// Example
console.log(capitalizeWords("hemant kumar agrahari"));
// Output: Hemant Kumar Agrahari

Q.Find the maximum and minimum number in an array.

Check if a string is a palindrome.

Count the number of vowels in a string.

Remove duplicates from an array.

Write a function to flatten a nested array [1,[2,[3,4],5]] → [1,2,3,4,5].

Implement a custom map() function.

Check if two strings are anagrams.

Find the first non-repeating character in a string.

Write a debounce function.
