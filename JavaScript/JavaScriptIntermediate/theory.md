Q.What is Promises?
A Promise is an object used to handle asynchronous tasks in JavaScript. It has three states — pending, fulfilled, and rejected — and helps us write cleaner async code without callback hell.

let myPromise = new Promise((resolve, reject) => {
  let success = true;
  if (success) {
    resolve("✅ Operation successful!");
  } else {
    reject("❌ Operation failed!");
  }
});

myPromise
  .then(result => console.log(result))   // runs if resolved
  .catch(error => console.log(error))   // runs if rejected
  .finally(() => console.log("Done"));  // runs always


Q.What is Promise chaining and how does it work?
Ans:
Promise chaining is a technique where multiple asynchronous operations are executed in sequence, by returning a new Promise from one .then() and handling it in the next .then()

Promise chaining allows us to run asynchronous tasks step by step. Each .then() passes its result to the next one, and if an error happens anywhere, it can be caught in .catch() at the end.

Q.What happens if you don’t return a value in a .then() block?
Ans:
If you don’t explicitly return a value in a .then(), the next .then() in the chain will receive undefined as its input.

Q.What is the difference between returning a value vs returning a Promise in .then()?What is the difference between returning a value vs returning a Promise in .then()?
Ans:
Returning a value passes it immediately to the next .then(), while returning a Promise makes the next .then() wait until that Promise resolves.

Q. What is the difference between Promise.all, Promise.allSettled, Promise.any, and Promise.race?
Ans:
Promise.all waits for all promises to resolve, but fails if one rejects.
Promise.allSettled waits for all promises and gives results of both fulfilled and rejected.
Promise.any returns the first fulfilled promise and ignores rejections.
Promise.race returns the result of the first promise that settles, whether resolved or rejected.

Q. How does Promise.all behave when one Promise rejects?
Ans:
If one promise rejects, Promise.all immediately rejects with that error, and other results are ignored.

Q. When should you use Promise.allSettled() instead of Promise.all()?
Ans:
Use Promise.allSettled when you want results of all promises, even if some fail — like loading multiple resources where failure of one doesn’t stop others.

Q. What happens if you resolve or reject a Promise multiple times?
Ans:
A promise can only settle once. After it is resolved or rejected, further resolve or reject calls are ignored.

Q. What is the difference between microtask queue (Promises) and macrotask queue (setTimeout)?
Ans:
Promises use the microtask queue, so their callbacks run before macrotasks like setTimeout. Microtasks have higher priority than macrotasks.

Q. How does error propagation work in Promise chains?
Ans:
If an error happens in a promise chain, it propagates to the nearest .catch. If no .catch is present, it causes an unhandled promise rejection.

Q.what is async await?
Ans:
Async/await is a way to handle asynchronous operations in JavaScript.
When I put async before a function, it always returns a Promise. Inside that function, I can use the await keyword to pause execution until the Promise resolves or rejects.

It makes asynchronous code look like synchronous code, so it’s easier to read and maintain compared to chaining .then() methods.

Q.What is closure?
Ans:
A closure is a feature in JavaScript where an inner function can continue to use variables from its parent function’s scope, even after the parent function is gone.

Q.What is currying function?
Ans:
Currying is a technique in JavaScript where a function is transformed into a sequence of functions, each taking a single argument. Instead of passing all arguments at once, you can pass them one by one.

Q.What is higher order function?
Ans:
A higher-order function is a function that either takes another function as an argument, or returns a function as its result, or both. It’s a concept that helps in making code more reusable and functional.

Q.What is the difference between memo and useMemo?
Ans:
memo is a higher-order component that we use to prevent unnecessary re-rendering of a component. It wraps a component and compares its props — if the props haven’t changed, React skips rendering the component again. This helps improve performance when the component is receiving the same props repeatedly.

On the other hand, useMemo is a hook that we use inside a component to memoize the result of an expensive calculation. It caches the value and only recalculates it when its dependencies change. This helps avoid running complex logic on every render unnecessarily.

Q.What is deep copy and what is shadow copy?
Ans:
 A shallow copy creates a new object, but it only copies the top-level properties. If any property is an object or an array, it still refers to the same reference in memory. That means changes in nested objects will affect both the original and the copied object.

 const original = { name: 'Hemant', address: { city: 'Delhi' } };
const shallowCopy = { ...original };

shallowCopy.address.city = 'Mumbai';
console.log(original.address.city); // Output: 'Mumbai'
Here, changing address.city in the copy also changes it in the original because only the reference is copied

Deep Copy:
A deep copy creates a completely new object with all nested objects and arrays duplicated as well. Changes in the copied object don’t affect the original.

const original = { name: 'Hemant', address: { city: 'Delhi' } };
const deepCopy = JSON.parse(JSON.stringify(original));

deepCopy.address.city = 'Mumbai';
console.log(original.address.city); // Output: 'Delhi'
In this case, even though we change address.city in the copied object, the original remains unchanged because all nested objects are also copied.”