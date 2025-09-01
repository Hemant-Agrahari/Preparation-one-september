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
Promise chaining is a technique where multiple asynchronous operations are executed in sequence, by returning a new Promise from one .then() and handling it in the next .then()

Promise chaining allows us to run asynchronous tasks step by step. Each .then() passes its result to the next one, and if an error happens anywhere, it can be caught in .catch() at the end.

Q.What happens if you don’t return a value in a .then() block?
If you don’t explicitly return a value in a .then(), the next .then() in the chain will receive undefined as its input.

Q.What is the difference between returning a value vs returning a Promise in .then()?What is the difference between returning a value vs returning a Promise in .then()?
Returning a value passes it immediately to the next .then(), while returning a Promise makes the next .then() wait until that Promise resolves.

Q.What is the difference between Promise.all, Promise.allSettled, Promise.any, and Promise.race?

Q.How does Promise.all behave when one Promise rejects?

Q.When should you use Promise.allSettled() instead of Promise.all()?

Q.What happens if you resolve or reject a Promise multiple times?

Q.What is the difference between microtask queue (Promises) and macrotask queue (setTimeout)?

Q.How does error propagation work in Promise chains?


