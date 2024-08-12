# Node.js Workshop - A Deeper Dive into JavaScript Concepts

## Early JavaScript and Object Orientation

Brendan Eich invented JavaScript in 1995. It was designed with object-oriented principles in mind from the very beginning, though its approach to object-orientation is different from classical object-oriented programming (OOP) languages like Java or C++. It incorporated concepts of objects, properties, and methods, which are key components of OOP. However, it also introduced unique features that distinguished it from traditional OOP languages.

JavaScript was designed around objects and a prototype-based inheritance model rather than a class-based one. Objects were central to JavaScript, and prototypes allowed objects to inherit properties and methods from other objects. It used constructor functions to create objects, which could have methods and properties defined on their prototype and allowed for dynamic property addition and modification, even to the prototypes. Objects could encapsulate data and methods, allowing for the bundling of related functionality.

```js
function Person(name) {
  this.name = name;
}

Person.prototype.greet = function() {
  console.log("Hello, my name is " + this.name);
};

let alperen = new Person("Alperen");
alperen.greet(); // Output: Hello, my name is Alperen
```

JavaScript retains its features, although many new functionalities have been added throughout the years. Many features that we have discussed in the previous chapters, like array methods _forEach, map, filter, reduce,_ etc were not a part of JavaScript initially and were introduced in later versions.

## The ECMAScript Standardization

ECMAScript was created to standardize JavaScript, which was originally developed by Netscape. The first edition was released in 1997. Since its inception, ECMAScript has undergone several updates and revisions. Major versions include ES3 (1999), ES5 (2009), ES6 (2015, also known as ECMAScript 2015 or ES2015), and subsequent yearly updates like ES2016, ES2017, and so on. The development of ECMAScript is overseen by Technical Committee 39 (TC39), a group within ECMA International comprising experts from various companies and organizations.

### How ECMAScript Relates to JavaScript

JavaScript is an implementation of the ECMAScript standard, primarily used in web development. Other implementations include JScript (used in Microsoft's Internet Explorer) and ActionScript (used in Adobe Flash). Browsers and JavaScript engines strive to maintain compatibility with the ECMAScript standard to ensure that code behaves consistently across different environments.

## Evolution of JavaScript OOP Features

Over time, JavaScript has evolved to include more features commonly associated with classical OOP, making it more familiar to developers from those backgrounds:

- **ES5 and Object.create:** The introduction of Object.create in ECMAScript 5 (ES5) provided a way to create objects with a specified prototype.
  
- **ES6 Classes:** ECMAScript 6 (ES6), released in 2015, introduced the class syntax, which allowed developers to write object-oriented code in a more familiar and concise way, though it is essentially syntactic sugar over the existing prototype-based system.

```js
class Person {
  constructor(name) {
    this.name = name;
  }

  greet() {
    console.log("Hello, my name is " + this.name);
  }
}

let cengiz = new Person("Cengiz");
cengiz.greet(); // Output: Hello, my name is Cengiz
```

## Asynchronous Execution

Asynchronous execution a fundamental concept that allows code to perform tasks without blocking the main execution thread, enabling better performance and responsiveness in applications. This is crucial for creating non-blocking applications, where the UI or the main thread remains responsive and the application can handle multiple tasks simultaneously.

### The `Event Loop`

The JavaScript runtime uses an **event loop** to handle asynchronous operations. The event loop allows JavaScript to perform non-blocking operations, even though it is single-threaded. It slightly differs between browsers and Node.js, but the concept is largely the same - functions are executed in **Call Stack:**, asynchronous callbacks are queued in queues to be executed later, and the **Event Loop** monitors the call stack and task queues, pushing tasks from the queues to the call stack when it's empty. Diagrams explaining both implementations in more details are added below:

- [Event Loop in Browser](../images/browser-event-loop.jpg)
- [Event Loop in Node.js](../images/nodejs-event-loop.jpg)

### Asynchronous Patterns in JavaScript

`Callbacks` are functions passed as arguments to other functions and are executed after the completion of an asynchronous operation. Callbacks are simple and easy to understand but there is a caveat, using callbacks carelessly can lead to  "callback hell" or "pyramid of doom".

```js
function fetchData(callback) {
    setTimeout(() => {
        callback('Data loaded');
    }, 2000);
}

console.log('Start');
fetchData((data) => {
    console.log(data);
});
console.log('End');
```

`Promises` represent the eventual completion (or failure) of an asynchronous operation and its resulting value. A _promise_ can be in one of three states: pending, fulfilled, or rejected. Using promises, you can chain multiple asynchronous operations and have an overall more readable code, but again, an excessive amount of chaining could turn the things complex and ugly.

```js
let promise = new Promise((resolve, reject) => {
    setTimeout(() => {
        resolve('Data loaded');
    }, 2000);
});

console.log('Start');
promise
    .then((data) => {
        console.log(data);
    })
    .catch((error) => {
        console.error(error);
    });
console.log('End');
```

`async` and `await` are syntactic sugar over promises, providing a more readable and imperative style for handling asynchronous code. This syntax makes asynchronous code look synchronous, improving readability and error handling is more straightforward with `try...catch`. It is still based on promises, so all operations need to be promise-based.

```js
async function fetchData() {
    let data = await new Promise((resolve) => {
        setTimeout(() => resolve('Data loaded'), 2000);
    });
    console.log(data);
}

console.log('Start');
fetchData();
console.log('End');
```

## Promises

Promises represent the eventual completion (or failure) of an asynchronous operation and its resulting value. A promise is an object that represents a value that might not be available yet but will be resolved in the future. It has three possible states:

- **Pending**: The initial state, neither fulfilled nor rejected.
- **Fulfilled**: The operation completed successfully, and the promise has a value.
- **Rejected**: The operation failed, and the promise has a reason for failure (an error).

You can create a promise using the `Promise` constructor, which takes a function (known as the executor function) as an argument. This function receives two arguments: `resolve` and `reject`. A promise can be used by chaining methods like `then`, `catch`, and `finally`.

- resolve(value): Marks the promise as fulfilled and sets the value.
- reject(reason): Marks the promise as rejected and sets the reason.
- then(onFulfilled, onRejected): Attaches callbacks for when the promise is fulfilled or rejected.
- catch(onRejected): Attaches a callback for when the promise is rejected.
- finally(onFinally): Attaches a callback that will be called regardless of the promise's outcome.

```js
const myPromise = new Promise((resolve, reject) => {
    const success = true;

    if (success) {
        resolve('Operation was successful!');
    } else {
        reject('Operation failed!');
    }
});

myPromise
    .then((value) => {
        console.log(value); // 'Operation was successful!'
    })
    .catch((error) => {
        console.error(error); // If the promise was rejected
    })
    .finally(() => {
        console.log('Promise has been settled (fulfilled or rejected).');
    });

//or you can use the async/await syntax
async function example() {
    try {
        const result = await myPromise;
        console.log(result); // 'Operation was successful!'
    } catch (error) {
        console.error(error); // If the promise was rejected
    } finally {
        console.log('Promise has been settled (fulfilled or rejected).');
    }
}

example();
```

One of the most powerful features of promises is chaining. You can return a new promise from within a then callback, allowing for sequential asynchronous operations.

```js
const anotherPromise = new Promise((resolve) => {
    resolve(10);
});

anotherPromise
    .then((value) => {
        console.log(value); // 10
        return value * 2;
    })
    .then((newValue) => {
        console.log(newValue); // 20
        return newValue * 3;
    })
    .then((finalValue) => {
        console.log(finalValue); // 60
    });
```

### **Promise Methods**

`Promise.all()` waits for all promises in an array to be fulfilled. If any promise is rejected, `Promise.all()` immediately rejects with the reason of the first promise that was rejected.

```javascript
Promise.all([promise1, promise2, promise3])
    .then((results) => {
        console.log(results); // Array of results from all promises
    })
    .catch((error) => {
        console.error(error); // If any promise rejects
    });
```

`Promise.race()` waits for the first promise in the array to settle (either fulfilled or rejected) and returns that result.

```javascript
Promise.race([promise1, promise2, promise3])
    .then((result) => {
        console.log(result); // Result of the first settled promise
    })
    .catch((error) => {
        console.error(error); // If the first settled promise is rejected
    });
```

`Promise.allSettled()` waits for all promises in an array to settle (either fulfilled or rejected) and returns an array of the results.

```javascript
Promise.allSettled([promise1, promise2, promise3])
    .then((results) => {
        console.log(results); // Array of objects describing each promise's outcome
    });
```

`Promise.any()` waits for the first promise to be fulfilled, ignoring rejected promises. If all promises are rejected, it returns a rejected promise with an `AggregateError`.

```javascript
Promise.any([promise1, promise2, promise3])
    .then((result) => {
        console.log(result); // First fulfilled promise result
    })
    .catch((error) => {
        console.error(error); // If all promises are rejected
    });
```

## Event Listeners & Emitters

_Events_ are actions or occurrences that happen in the browser or some entity connected with your Node.js app.

_Event listeners_ are functions or procedures that wait for an event to occur on a specified element or object, such as a button click, a keypress, or a mouse movement. In Node.js context, it might be when a stream ends, a file is written, a request is completed etc. When the specified event happens, the event listener triggers a callback function, allowing you to respond to the event with custom logic.

_Event emitters_ are a design pattern used in programming to handle and manage events. This pattern is especially prevalent in environments like Node.js, where it plays a crucial role in managing asynchronous behavior. An event emitter is an object that emits events, allowing other objects (or functions) to listen for and respond to those events.

- An event emitter is an object that can trigger or emit events at certain points in the code.
- Other parts of the code can register functions (listeners) that should be executed when a specific event is emitted.
- An event can have multiple listeners, all of which will be triggered when the event is emitted.

```javascript
// Node.js Example

const EventEmitter = require('events');
const myEmitter = new EventEmitter();

// Define a listener function
const greetListener = (name) => {
    console.log(`Hello, ${name}!`);
};

// Add the 'greet' event listener
myEmitter.on('greet', greetListener);

// Emit the 'greet' event
myEmitter.emit('greet', 'Tomris'); // Output: Hello, Tomris!

// Remove the 'greet' event listener
myEmitter.removeListener('greet', greetListener);

// Emit the 'greet' event again
myEmitter.emit('greet', 'Yaman'); // No output, as the listener has been removed

// In newer versions of Node.js, you can also use the off method as an alias for removeListener.
myEmitter.off('greet', greetListener);

// remove all listeners for a specific event
myEmitter.removeAllListeners('greet');

// One-Time Listeners
myEmitter.once('onlyOnce', () => {
    console.log('This will only run once');
});

myEmitter.emit('onlyOnce'); // This triggers the listener
myEmitter.emit('onlyOnce'); // This will not trigger the listener again
```

Event emitters can pass multiple arguments to the listeners when an event is emitted.

```javascript
myEmitter.on('data', (a, b, c) => {
    console.log(a, b, c);
});

myEmitter.emit('data', 1, 2, 3); // Logs: 1 2 3
```

The `EventEmitter` class has a special event named `error`. If an error occurs, it is common practice to emit an `error` event. If no listeners are registered for this event, Node.js will throw the error, causing the process to crash.

```javascript
myEmitter.on('error', (err) => {
    console.error('An error occurred:', err);
});

myEmitter.emit('error', new Error('Something went wrong'));
```

In Node.js, many core modules, such as HTTP, streams, and file system modules, extend the `EventEmitter` class. This allows these modules to emit and listen to events.

```javascript
const http = require('http');

const server = http.createServer((req, res) => {
    res.end('Hello, World!');
});

// Listening for the 'request' event
server.on('request', (req, res) => {
    console.log(`Received request for: ${req.url}`);
});

server.listen(3000, () => {
    console.log('Server is listening on port 3000');
});
```

In this example, the `http.Server` object emits a `request` event whenever an HTTP request is received. The listener function logs the requested URL.

DOM objects in web browsers are not technically event emitters in the same sense as Node.js's EventEmitter class. However, they have a similar mechanism for handling events. While Node.js uses the EventEmitter class to manage events, the browser's DOM provides its own event-handling system built into the DOM API.

```javascript
// Browser Example

// Selecting an element
const button = document.getElementById('myButton');

// Adding a click event listener
button.addEventListener('click', function() {
  alert('Button was clicked!');
});

// Remove the event listener
button.removeEventListener('click', handleClick);
```

The default behavior of the browser can also be altered using event listeners. The following example shows how to stop navigating when a link is clicked.

```js
document.querySelector('a').addEventListener('click', function(event) {
    event.preventDefault(); // Preventing Default Actions
    alert('Default action prevented!');
});
```

## Error Handling Mechanisms

Most of the widely used languages have some sort of higher level error handling and _throw_ exceptions or errors; like Java uses `try...catch` and `finally` blocks; and supports checked exceptions, where certain errors must be either caught or declared in the method signature. A `try...catch` and on optional `finally` statements can be similarly used in JavaScript to handle exceptions that may occur during the execution of a block of code, and uou can throw your own errors using the `throw` statement.

```js
try {
    // Code that may throw an error
} catch (error) {
    // Code to handle the error
} finally {
    // Optional: Code that will always run, regardless of an error
}

if (!user) {
    throw new Error("User not found");
}
```

You can extend the built-in Error class to create custom error types.

```js
class CustomError extends Error {
    constructor(message) {
        super(message);
        this.name = "CustomError";
    }
}

throw new CustomError("This is a custom error");
```

### Error Handling in Asynchronous Code

Since we will be working with Node.js: traditionally, errors in asynchronous operations are handled by passing an error object as the first argument to the callback.

```js
fs.readFile('file.txt', (err, data) => {
  if (err) {
    console.error(err);
    return;
  }
  console.log(data);
});
```

With `async/await`, error handling is straightforward, `try...catch`:

```js
async function fetchData() {
  try {
    const response = await fetch("https://api.example.com/data");
    const data = await response.json();
    console.log(data);
  } catch (error) {
    console.error("Error:", error);
  }
}
fetchData();
```

Promises provide a more modern approach to handling asynchronous errors. Errors are caught using `.catch()` at the end of the promise chain.

```js
fetch('https://api.example.com/data')
  .then(response => response.json())
  .then(data => console.log(data))
  .catch(error => console.error('Error:', error));
```

### Handling Unhandled Rejections and Exceptions

The **`unhandledrejection` Event** catches unhandled promise rejections at the global level in the browser.

```js
window.addEventListener('unhandledrejection', (event) => {
   console.error('Unhandled promise rejection:', event.reason);
});
```

The **`uncaughtException` event** catches uncaught exceptions at the global level in Node.js.

```js
process.on('uncaughtException', (err) => {
   console.error('Uncaught Exception:', err);
   process.exit(1);
});
```
