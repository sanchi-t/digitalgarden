---
{"dg-publish":true,"permalink":"/interview/backend/node-js/"}
---


# Nodejs


## Architecture

Node.js uses the <mark style="background: #FFB86CA6;">Single Threaded Event Loop</mark> architecture to handle multiple concurrent clients.

![Pasted image 20241209004809.png](/img/user/Images/Pasted%20image%2020241209004809.png)

### Parts of Node js Architecture:

- **Requests** : Incoming requests can be blocking (complex/<mark style="background: #FFB86CA6;">synchronous</mark>) or non-blocking (simple/<mark style="background: #FFB86CA6;">asynchronous</mark>), depending upon the tasks that a user wants to perform in a web application
- **Node.js server**: Node.js server is a server-side platform that takes requests from users, processes those requests, and returns responses to the corresponding users
- **Event Queue**: Event Queue in a Node.js server stores incoming client requests and passes those requests one-by-one into the Event Loop
- **Thread pool**: Thread pool consists of all the threads available for carrying out some tasks that might be required to fulfill client requests
- **Event loop**: Event Loop indefinitely receives requests and processes them, and then returns the responses to corresponding clients.
- **External Resources**: External resources are required to deal with blocking client requests. These resources can be for computation, data storage, etc.

![Pasted image 20241209005207.png](/img/user/Images/Pasted%20image%2020241209005207.png)

### The workflow of Node js Architecture:

- Clients send requests to the webserver to interact with the web application. Requests can be non-blocking or blocking e.g Querying the data , updating the data or deleting the data .
- Node.js retrieves the incoming requests and adds those requests to the Event Queue.
- The requests are then passed one-by-one through the Event Loop. It checks if the requests are simple enough to not require any external resources.
- Event Loop processes simple requests (non-blocking operations), such as I/O Polling, and returns the responses to the corresponding clients.

A single thread from the Thread Pool is assigned to a single complex request. This thread is responsible for completing a particular blocking request by accessing the external resources, such as compute, database, file system, etc.

Once, the task is carried out completely, the response is sent to the Event Loop that in turn sends that response back to the Client.



## Theoretical Questions:

### 1.  What are advantages and disadvantages of nodejs?

The advantages are:
- **Handling multiple concurrent client requests is fast and easy:** Because of event queue and thread pool. 
- **No need for creating multiple threads:** Single thread is enough to handle a blocking incoming request. 
- **Requires fewer resources and memory.**
- **Active Community and Support**.

The disadvantages are:
- **Scalability Challenges:** Due to the fact that it’s a single-threaded process. You might need to divide building many complex applications into smaller microservices that handle different operations.
- **Immature Modules:** While the npm ecosystem is extensive, not all libraries and modules are mature or well-maintained.
- **Vulnerabilities in Packages:** The reliance on third-party packages increases the risk of security vulnerabilities.
- [[Interview/Backend/NodeJs#2. What is callback hell? \| Callback Hell]]: It can be resolved by using [[Interview/Backend/NodeJs#3. What is a promise in js? \|promises]] or [[Interview/Backend/NodeJs#4. What is async/await in js? \| async/await]] .

### 2. What is callback hell?

Callback hell is a situation where multiple nested callbacks are used to handle asynchronous operations in JavaScript. This typically happens when you have several asynchronous tasks that depend on each other’s results. Here’s a classic example:

```js
asyncOperation1(function(result1) {  
    asyncOperation2(result1, function(result2) {  
        asyncOperation3(result2, function(result3) {  
            asyncOperation4(result3, function(result4) {  
                // Do something with result4  
            });  
        });  
    });  
});
```

Problems with Callback Hell
1. **Readability:** The code becomes hard to read and understand, especially as the nesting grows deeper.
2. **Maintainability:** Modifying or extending functionality becomes challenging and error-prone.
3. **Error Handling:** Handling errors across nested callbacks can become complex and repetitive.

Solutions to Callback Hell
 1. Named Functions: Refactor your code to use named functions instead of anonymous callbacks. This approach improves readability by separating concerns and reducing nesting.
	 ```js
	function handleResult1(result1) {  
	    asyncOperation2(result1, handleResult2);  
	}  
	function handleResult2(result2) {  
	    asyncOperation3(result2, handleResult3);  
	}  
	function handleResult3(result3) {  
	    asyncOperation4(result3, function(result4) {  
	        // Do something with result4  
	    });  
	}  
	asyncOperation1(handleResult1);
	```

4. [[Interview/Backend/NodeJs#3. What is a promise in js? \| Promises.]]
5. [[Interview/Backend/NodeJs#4. What is async/await in js? \| Async/Await.]]

### 3. What is a promise in js?
The **`Promise`** object represents the eventual completion (or failure) of an asynchronous operation and its resulting value. This lets asynchronous methods return values like synchronous methods: instead of immediately returning the final value, the asynchronous method returns a _promise_ to supply the value at some point in the future.

A `Promise` is in one of these states:

- _pending_: initial state, neither fulfilled nor rejected.
- _fulfilled_: meaning that the operation was completed successfully.
- _rejected_: meaning that the operation failed.

>[!info]
>A promise is said to be _settled_ if it is either fulfilled or rejected, but not pending.
> - If the promise is fulfilled, `.then()` is used to retrieve the value and perform actions after its resolution.
> - If the promise is rejected `.catch()` is used for error handling.
> - Just like there’s a `finally` clause in a regular `try {...} catch {...}`, there’s `finally` in promises. The call `.finally(f)` is similar to `.then(f, f)` in the sense that `f` runs always, when the promise is settled: be it resolve or reject.

![Pasted image 20241209140635.png](/img/user/Images/Pasted%20image%2020241209140635.png)

Usage:
```js
const myPromise = new Promise((resolve, reject) => {
  setTimeout(() => {
    resolve("foo");
  }, 300);
});

myPromise
  .then(handleFulfilledA, handleRejectedA)
  .then(handleFulfilledB, handleRejectedB)
  .then(handleFulfilledC, handleRejectedC);

//OR

myPromis
  .then((response) => console.log(respons))
  .catch((error) => console.log(error));

```


### 4. What is async/await in js?

The async/await syntax is a special syntax created to help you work with promise objects.
The `await` keyword basically makes JavaScript wait until the `Promise` object is resolved or rejected. Instead of having to use the callback pattern inside the `then()` method, you can assign the fulfilled promise into a variable like this:
```js
const response = await fetch('https://jsonplaceholder.typicode.com/todos/1');
const json = await response.json();
console.log(json)
```

An `async function` declaration creates an [`AsyncFunction`](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/AsyncFunction) object. Each time when an async function is called, it returns a new [`Promise`](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Promise) which will be resolved with the value returned by the async function, or rejected with an exception uncaught within the async function.

For example, consider the following code:

``` js
async function foo() {
  return 1;
}
```

It is similar to:

``` js
function foo() {
  return Promise.resolve(1);
}
```

To handle an error that might occur from the async/await syntax, you can use the try/catch block to catch any rejection from your promise.

```js
async function runProcess() {
  try {
    const response = await fetch('https://jsonplaceholder.typicode.com/todos/1');
    const json = await response.json();
    console.log(json);
  } catch (error) {
    console.log(error);
  }
}

runProcess();
```


### 5. What is var, let and const in js?

The `var` keyword declares variables with function scope or global scope, depending on where it's defined. Variables declared with `var` are **hoisted**, meaning they can be used before their declaration, but their value will be `undefined` until the actual assignment. `var` allows re-declaration of the same variable within the same scope, which can lead to unintended bugs in larger codebases. It's generally considered less safe and is avoided in modern JavaScript development.

The `let` keyword was introduced in ES6 (ECMAScript 2015) to provide **block-level scope**, meaning the variable is only accessible within the curly braces `{}` where it is defined. Unlike `var`, `let` prevents re-declaration in the same scope, making it more predictable and safer for managing state. `let` is also hoisted, but it is placed in a <mark style="background: #FFB86CA6;">Temporal Dead Zone (TDZ)</mark>, which means you cannot use it before its declaration, reducing potential bugs caused by unintentional usage.

The `const` keyword is used to declare variables that are **constant**, meaning their value cannot be reassigned after initialization. Like `let`, `const` is block-scoped and is subject to the Temporal Dead Zone. However, `const` does not make the variable immutable if it's an object or array; only the reference to the object cannot be changed, but the contents can still be modified. `const` is generally used for values that should remain constant throughout the code, providing clarity and reducing accidental reassignment errors.


### 6. What is NPM and NPX?

#### NPM
NPM – or "Node Package Manager" – is the default package manager for JavaScript's runtime Node.js.
NPM consists of two main parts:

- a CLI (command-line interface) tool for publishing and downloading packages, and
- an [online repository](https://www.npmjs.com/) that hosts JavaScript packages

`npm` installs, updates and manages downloads of dependencies of your project. Dependencies are pre-built pieces of code, such as libraries and packages, that your Node.js application needs to work.

>[!info]
>[**Yarn**](https://yarnpkg.com/en/) and [**pnpm**](https://pnpm.io) are alternatives to npm cli. You can check them out as well.

#### NPX
The `npx` stands for **Node Package Execute** and it comes with the `npm`, when you installed `npm` above `5.2.0` version then automatically `npx` will installed. It is an `npm` package runner that can execute any package that you want from the `npm` registry without even installing that package.
It can also run locally installed packages which are a bit difficult to do with `npm`.


### 7. What is the use of package.json and package-lock.json?

The use cases for `package.json` file:
- **Dependency Management**: The `package.json` file lists all the dependencies required for the NodeJS project. These dependencies include both runtime dependencies needed for the application to function and development dependencies required for building, testing, and maintaining the project.
- **Version Control Integration** The `package.json` file typically includes metadata such as the project's name, version, description, author, and license. This information helps developers and users understand the project's purpose, track its version history, and comply with licensing requirements.
- **Script Execution**: NodeJS projects often define custom scripts in the `package.json` file to automate various tasks, such as running tests, starting the development server, building the project, or deploying the application. These scripts simplify common development workflows and promote consistency across different environments.

In the `package.json`, the `“dependencies”` object maps **package-name to the version range.**

![Pasted image 20241210144434.png](/img/user/Images/Pasted%20image%2020241210144434.png)

This makes `npm install` non-deterministic. So, when you run `npm install` today, and then you run it again after 3 months, you may not end up with the same `node_modules` tree.
When multiple developers are working on the same repository (which is most likely the case in every organization), this might pose a big problem and lead to inconsistencies in the dependencies installed, or worse, breaking changes.

- `^2.3.0` — [Caret Symbol] This tells npm to upgrade to minor and patch versions, but not major versions. So, basically `2.3.4, 2.3.9, 2.4.5, 2.8` but not `3.0.0` onwards. (Upgrade to minor and patch, but not major)
- `~2.3.0` — [Tilde Symbol] This tells npm to upgrade to patch versions, but not minor and major versions. So `2.3.4, 2.3.9` but not `2.4.0` onwards. (Upgrade to patch, but not minor and major)

Therefore for locking the version we use `package-lock.json`.


### 8. What is lexical scope in js?

The process of determining the scopes of the variables/functions during runtime is called lexical scoping. The word _lexical_ comes from the _lexical/tokenization phase_ of the JS compiler steps.

Lexical scope defines the accessibility of variables and functions depending on their location in the source code. Variables and functions have different levels of scope:

- **Global Scope:** Variables defined outside any function or block, accessible anywhere in the program.
- **Local Scope:** Variables defined inside a function or block, accessible only within that specific function or block.
- **Nested Scope:** Inner functions have access to variables in their parent functions.
- **Block Scope:** Variables defined with let and const are limited to the block they are declared in, like loops or conditionals.

### 9. What is closure in js?

Consider the following code example:
```js
function makeFunc() {
  const name = "Mozilla";
  function displayName() {
    console.log(name);
  }
  return displayName;
}

const myFunc = makeFunc();
myFunc();

```

At first glance, it might seem unintuitive that this code still works. In some programming languages, the local variables within a function exist for just the duration of that function's execution. Once `makeFunc()` finishes executing, you might expect that the `name` variable would no longer be accessible. However, because the code still works as expected, this is obviously not the case in JavaScript.

The reason is that functions in JavaScript form closures. A _closure_ is the combination of a function and the lexical environment within which that function was declared. This environment consists of any variables that were in-scope at the time the closure was created. In this case, `myFunc` is a reference to the instance of the function `displayName` that is created when `makeFunc` is run. The instance of `displayName` maintains a reference to its lexical environment, within which the variable `name` exists. For this reason, when `myFunc` is invoked, the variable `name` remains available for use, and "Mozilla" is passed to `console.log`.

>[!info]
> Due to closure the whole lexical scope is returned instead on only executional context.


###  10. What are higher order functions in js?

A higher order function is a function that takes one or more functions as arguments, or returns a function as its result.

There are several different types of higher order functions like map and reduce.

```js
// Callback function, passed as a parameter in the higher order function
function callbackFunction(){
    console.log('I am  a callback function');
}

// higher order function
function higherOrderFunction(func){
    console.log('I am higher order function')
    func()
}

higherOrderFunction(callbackFunction);
```

```js
const arr = [1, 2, 3, 4, 5];
const output = arr.map((num) => num += 10)
console.log(arr); // [1, 2, 3, 4, 5]
console.log(output); // [11, 12, 13, 14, 15]
```

The callback function that is being passed to `map` uses the arrow function syntax, and it takes a single argument `num`. This function adds 10 to `num` (every element in the array) and returns the result.


### 11. What is the difference between request parameters and query parameters?

Request parameters and query parameters are both ways to send data to a server, but they differ in purpose and placement. <mark style="background: #FFB86CA6;">Request parameters</mark> are part of the URL path itself and are typically used to identify specific resources. For example, in the URL `/users/123`, `123` is a request parameter that represents the user ID. These parameters are often defined in the API route and are required to access specific data. Request parameters are parsed from the URL and are not part of the query string.

<mark style="background: #FFB86CA6;">Query parameters</mark>, on the other hand, are appended to the URL after a `?` and are used to pass optional or additional information to the server. They follow the key-value format, separated by `&` for multiple parameters. For example, in `/users?sort=name&active=true`, `sort` and `active` are query parameters used to modify the response or filter data. Unlike request parameters, query parameters are optional and often provide metadata or control information without directly identifying resources.


### 12. What are different types of module system in nodejs?

There are two different module systems in Node.js: CommonJS and ECMAScript modules (ES modules).

#### **CommonJS (CJS)**:
In CommonJS, you use `require` to import modules and `module.exports` or `exports` to define what a module exposes.

**Exporting in CommonJS**:
If a module defines a single export, you use `module.exports`:
```js
// singleExport.js
module.exports = function () {
    console.log("Hello from CommonJS!");
};

```

You can also export multiple items using an object:
```js
// multipleExports.js
function greet() {
    console.log("Hello!");
}

function add(a, b) {
    return a + b;
}

module.exports = {
    greet,
    add,
};

```

**Importing in CommonJS**

To import modules, use `require`:
```js
// Importing single export
const singleExport = require('./singleExport');
singleExport(); // Hello from CommonJS!

// Importing multiple exports
const { greet, add } = require('./multipleExports');
greet(); // Hello!
console.log(add(5, 10)); // 15

```


#### **ECMAScript Modules (ESM)**

ESM uses `import` and `export` for module management. You can have **default exports** or **named exports**.

**Exporting in ESM**

For a default export:
```js
// defaultExport.js
export default function () {
    console.log("Hello from ESM!");
}

```

For multiple named exports:
```js
// namedExports.js
export function greet() {
    console.log("Hello!");
}

export function add(a, b) {
    return a + b;
}

```

You can also combine default and named exports:
```js
// combinedExports.js
export default function multiply(a, b) {
    return a * b;
}

export function subtract(a, b) {
    return a - b;
}

```

**Importing in ESM**

To import a default export:
```js
import defaultExport from './defaultExport.js';
defaultExport(); // Hello from ESM!

```

>[!info]
> We don't need to use `{}` for default exports when importing.
> `export default` is used to export a single class, function or primitive from a script file.

To import named exports:
```js
import { greet, add } from './namedExports.js';
greet(); // Hello!
console.log(add(5, 10)); // 15

```

To import both default and named exports together:
```js
import multiply, { subtract } from './combinedExports.js'; console.log(multiply(5, 3)); // 15 console.log(subtract(10, 4)); // 6
```

**Configuring ESM in Node.js**

To enable ESM in Node.js, add the following to `package.json`:
```js
{
  "type": "module"
}

```


### 13. What is circular dependency in nodejs and how to fix it?

A **cyclic dependency** occurs when two or more modules depend on each other either directly or indirectly, forming a circular chain. This can create issues such as infinite loops, unexpected behavior, or errors in your application. For example, if **Module A** depends on **Module B**, and **Module B** also depends on **Module A**, this results in a cyclic dependency.

```js
// moduleA.js
const moduleB = require('./moduleB');
module.exports = {
    greet: () => moduleB.sayHello(),
};

// moduleB.js
const moduleA = require('./moduleA');
module.exports = {
    sayHello: () => moduleA.greet(),
};

```
When Node.js tries to resolve these dependencies, it encounters an incomplete module export, leading to runtime issues or undefined behavior.

**How to Avoid and Fix Cyclic Dependencies**

**1. Refactor Code to Remove Dependency Loops**
Break the cyclic dependency by restructuring your modules. Identify the shared logic and extract it into a new module.  
**Refactored Example**:
```js
// shared.js
function greet() {
    console.log("Hello!");
}
module.exports = { greet };

// moduleA.js
const { greet } = require('./shared');
module.exports = { greet };

// moduleB.js
const { greet } = require('./shared');
module.exports = { greet };

```

**2. Use Dependency Injection**
Pass dependencies as arguments to functions or constructors instead of requiring them directly inside modules. **Example**:
```js
// moduleA.js
function greet(dependency) {
    dependency.sayHello();
}
module.exports = { greet };

// moduleB.js
function sayHello() {
    console.log("Hello from Module B!");
}
module.exports = { sayHello };

// main.js
const moduleA = require('./moduleA');
const moduleB = require('./moduleB');
moduleA.greet(moduleB);

```


### 14. Can values of js const object be changed? Why? How to prevent that?

**Yes, properties and methods be changed for a const object**.

A const declaration does not mean that the value of the variable cannot be changed. It just means that the **variable identifier cannot be reassigned**.
```js
const SomeOb = {
	id: 233,
	name: null,
};

// allowed
SomeOb.name = "John Doe";

// not allowed as variable cannot be reassigned
SomeOb = 10;
```

>[!info]
>Primitive data types (Number, Boolean, String etc) are passed by value. The variable identifier holds the value, and since identifier cannot be changed for a const, it essentially means that the value cannot be changed here.
>
>However complex data types such as objects and arrays are passed by reference. The variable identifier holds the reference, not the actual "value". So even if the object's properties and methods are altered, it does not change the actual reference.


Prevent changing properties in an object:
The `Object.freeze()` method can make an object or array immutable. No changes can be made to that object once it gets immutable.
```js
var sample = {
    id: 1003,
    name: "John",
    age: 35
};

// allowed
sample.age = 34;

// object is now frozen
Object.freeze(sample);

// this will not change value
sample.age = 30;

// "34"
console.log(sample.age);
```

Knowing whether an Object is Frozen or Not
The `Object.isFrozen()` method can check whether a specific object is frozen or not. If frozen, it returns a boolean true, and false otherwise.
```javascript
var sample = {
    a: 23
};

// false
console.log(Object.isFrozen(sample));

Object.freeze(sample);

// true
console.log(Object.isFrozen(sample));
```

>[!info]
>`Object.freeze()` does a shallow freeze — only the immediate properties of the object cannot be changed. **If the object contains another object as a property, then properties of that inner object can be changed even if the main object is frozen**.
> ```js
> var sample = {
>    a: 23,
>    test: {
>        b: 45
>    }
>};
>
> Object.freeze(sample);
> 
> //this will happen as "b" is the property of inner object.
> sample.test.b = 100;



## Coding Problems


### 1. Building a Simple RESTful API with Express

```js
const express = require('express');  
const app = express();  
const port = 3000;  
  
app.use(express.json());  
  
let items = []; // In-memory storage for simplicity  
  
// Create a new item  
app.post('/items', (req, res) => {  
    const item = req.body;  
    items.push(item);  
    res.status(201).json(item);  
});  
  
// Get all items  
app.get('/items', (req, res) => {  
    res.json(items);  
});  
  
// Get a single item by ID  
app.get('/items/:id', (req, res) => {  
    const id = parseInt(req.params.id, 10);  
    const item = items.find(i => i.id === id);  
    if (item) {  
        res.json(item);  
    } else {  
        res.status(404).json({ message: 'Item not found' });  
    }  
});  
  
// Update an item by ID  
app.put('/items/:id', (req, res) => {  
    const id = parseInt(req.params.id, 10);  
    const index = items.findIndex(i => i.id === id);  
    if (index !== -1) {  
        items[index] = req.body;  
        res.json(items[index]);  
    } else {  
        res.status(404).json({ message: 'Item not found' });  
    }  
});  
  
// Delete an item by ID  
app.delete('/items/:id', (req, res) => {  
    const id = parseInt(req.params.id, 10);  
    items = items.filter(i => i.id !== id);  
    res.status(204).end();  
});  
  
app.listen(port, () => {  
    console.log(`Server running at http://localhost:${port}`);  
});
```

### 2. Reading and Writing JSON Files

```js
const fs = require('fs').promises;  
const path = './data.json';  
  
async function updateJsonFile(key, value) {  
    try {  
        const data = await fs.readFile(path, 'utf-8');  
        const jsonData = JSON.parse(data);  
        jsonData[key] = value;  
        await fs.writeFile(path, JSON.stringify(jsonData, null, 2));  
        console.log('File updated successfully');  
    } catch (error) {  
        console.error('Error updating file:', error);  
    }  
}  
  
updateJsonFile('exampleKey', 'exampleValue');
```

### 3. Logging Requests with Middleware

```js
const express = require('express');
const app = express();
const port = 3000;

function requestLogger(req, res, next) {
    const { method, url } = req;
    const timestamp = new Date().toISOString();
    console.log(`[${timestamp}] ${method} ${url}`);
    next();
}

app.use(requestLogger);

app.get('/', (req, res) => {
    res.send('Hello, world!');
});

app.listen(port, () => {
    console.log(`Server running at http://localhost:${port}`);
});
```

#### To use multiple middle (middleware chaining):

```js
const middleware1 = (req, res, next) => {  
// Tasks  
next();  
};  
const middleware2 = (req, res, next) => {  
// Tasks  
next();  
};  
app.get('/example', middleware1, middleware2, (req, res) => {  
  // Route handler  
});
```

### 4. Creating a Simple HTTP Server

```js
const http = require('http');

const server = http.createServer((req, res) => {
    res.statusCode = 200;
    res.setHeader('Content-Type', 'text/plain');
    res.end('Hello, World!\n');
});

server.listen(3000, '127.0.0.1', () => {
    console.log('Server running at http://127.0.0.1:3000/');
});
```

### 5. Implementing a Rate Limiter Middleware

```js
const express = require('express');
const rateLimit = require('express-rate-limit');

const app = express();
const port = 3000;

const limiter = rateLimit({
    windowMs: 60 * 1000, // 1 minute
    max: 5, // limit each IP to 5 requests per windowMs
    message: 'Too many requests from this IP, please try again later.'
});

app.use(limiter);

app.get('/', (req, res) => {
    res.send('Hello, world!');
});

app.listen(port, () => {
    console.log(`Server running at http://localhost:${port}`);
});
```

### 6. Connecting to MongoDB

```js
const { MongoClient } = require('mongodb');

const url = 'mongodb://localhost:27017';
const dbName = 'mydatabase';

async function fetchDocuments() {
    const client = new MongoClient(url, { useUnifiedTopology: true });

    try {
        await client.connect();
        console.log('Connected to MongoDB');
        const db = client.db(dbName);
        const collection = db.collection('mycollection');
        const documents = await collection.find({}).toArray();
        console.log('Documents:', documents);
    } catch (error) {
        console.error('Error fetching documents:', error);
    } finally {
        await client.close();
    }
}

fetchDocuments();
```

### 7. JWT Authentication in Express

```js
const express = require('express');
const jwt = require('jsonwebtoken');
const app = express();
const port = 3000;

app.use(express.json());

const secretKey = 'your_secret_key';

function authenticateToken(req, res, next) {
    const token = req.header('Authorization')?.split(' ')[1];
    if (!token) return res.sendStatus(401);

    jwt.verify(token, secretKey, (err, user) => {
        if (err) return res.sendStatus(403);
        req.user = user;
        next();
    });
}

app.post('/login', (req, res) => {
    const { username } = req.body;
    const user = { name: username }; // Normally, you'd validate the user here
    const token = jwt.sign(user, secretKey);
    res.json({ token });
});

app.get('/protected', authenticateToken, (req, res) => {
    res.send('This is a protected route');
});

app.listen(port, () => {
    console.log(`Server running at http://localhost:${port}`);
});
```

### 8. Debouncing API Requests

```js
function debounce(func, wait) {
    let timeout;
    return function (...args) {
        clearTimeout(timeout);
        timeout = setTimeout(() => func.apply(this, args), wait);
    };
}

const fetchData = async () => {
    console.log('Fetching data...');
    // Simulate API request
};

const debouncedFetchData = debounce(fetchData, 2000);

debouncedFetchData();
debouncedFetchData();
debouncedFetchData();
```

### 9. Custom Error Handler Middleware

```js
const express = require('express');
const app = express();
const port = 3000;

app.use(express.json());

app.get('/', (req, res) => {
    throw new Error('Something went wrong!');
});

app.use((err, req, res, next) => {
    console.error(err.stack);
    res.status(500).send('Something went wrong!');
});

app.listen(port, () => {
    console.log(`Server running at http://localhost:${port}`);
});
```

### 10. Monitoring Performance Metrics

```js
const express = require('express');
const app = express();
const port = 3000;

app.use(express.json());

app.use((req, res, next) => {
    const start = Date.now();
    res.on('finish', () => {
        const duration = Date.now() - start;
        console.log(`${req.method} ${req.originalUrl} took ${duration}ms`);
    });
    next();
});

app.get('/', (req, res) => {
    setTimeout(() => {
        res.send('Hello, world!');
    }, 1000); // Simulate delay
});

app.listen(port, () => {
    console.log(`Server running at http://localhost:${port}`);
});
```


### 11. How to make Post request in Node.js?

```js
// Import the axios library
const axios = require('axios');

// Create a data object
const data = {
  title: 'Hello, world!',
  body: 'This is a test post',
  userId: 1
};

// Make the POST request using the then method
axios.post('http://jsonplaceholder.typicode.com/posts', data, {
  headers: {
    'Content-Type': 'application/json',
    'User-Agent': 'Node.js'
  }
}).then((response) => {
  // Log the post information
  console.log(`Post Data: ${response.data}`);
}).catch((error) => {
  // Log the error message and code
  console.log(`Error message: ${error.message}`);
```

Or

```js
// Import the http module
const http = require('http');

// Create an options object
const options = {
  hostname: 'jsonplaceholder.typicode.com',
  port: 80,
  path: '/posts',
  method: 'POST',
  headers: {
    'Content-Type': 'application/json',
    'User-Agent': 'Node.js'
  }
};

// Create a data object
const data = {
  title: 'Hello, world!',
  body: 'This is a test post',
  userId: 1
};

// Stringify the data object
const dataString = JSON.stringify(data);

// Update the options object with the data length
options.headers['Content-Length'] = dataString.length;

// Create a request object
const request = http.request(options, (response) => {
  let data = '';

  // Listen to the data event
  response.on('data', (chunk) => {
    // Append the chunk to the data variable
    data += chunk.toString();
  });

  // Listen to the end event
  response.on('end', () => {
    const post = JSON.parse(data);

    // Log the post information
    console.log(`Post data: ${post}`);
  });

  // Listen to the error event
  response.on('error', (error) => {
    throw error;
  });
});

// Write the data to the request object
request.write(dataString);

request.end();
```

