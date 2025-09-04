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

Reverse a string without using built-in methods.

Find the maximum and minimum number in an array.

Check if a string is a palindrome.

Count the number of vowels in a string.

Remove duplicates from an array.

Write a function to flatten a nested array [1,[2,[3,4],5]] → [1,2,3,4,5].

Implement a custom map() function.

Check if two strings are anagrams.

Find the first non-repeating character in a string.

Write a debounce function.
