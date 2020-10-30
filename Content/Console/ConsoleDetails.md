# **1. log, info, debug, warn and error**

Console object's `log()` method prints a message to the default output, whether it be a browser's console or a terminal supporting `NodeJS` runtime
📄

Parameters

Multiple objects as parameters

```javascript
const messageOne = "Message number one";

const objectOne = {
  name: "Kyle",
  age: 24,
  city: "Los Angeles",
};

console.log(messageOne, objectOne); //  ✅  Message number one { name: 'Kyle', age: 24, city: 'Los Angeles' }
```

A String as a parameter

```javascript
const messageValue = "This is a message";

console.log(messageValue); //  ✅  This is a message
```

A String with substitute value(s)

The different `directives` that we can use for substitution are:

- `%d` or `%i` for an integer value

- `%f` for a float value

- `%s` for a String value

- `%O` or `%o` for an Object value

```javascript
const numberValue = 25;

const floatValue = 25.75;

const messageValue = "This is a message";

const objectValue = {
  name: "Kyle",
  age: 24,
  city: "Los Angeles",
};

const anotherObjectValue = {
  name: "Jeremy",
  age: 32,
  city: "New York",
};

console.log("Number value: %d", numberValue); //  ✅  Number value: 25

console.log("Float value: %f", floatValue); //  ✅  Float value: 25.75

console.log("Message value: %s", messageValue); //  ✅  Message value: This is a message

console.log("Object values: %O and %o", objectValue, anotherObjectValue);
//  ✅`Object values: { name: 'Kyle', age: 24, city: 'Los Angeles' } and { name: 'Jeremy', age: 32, city: 'New York' }
```

All the above parameters apply for the `info()`, `debug()`, `warn()`, and `error()` methods as well.

`info()` is the same as the `log()` just specifically assigned for printing out messages classified as information rather than just logging out messages. ℹ️

```javascript
const information = "This is some information";

console.info("Message value:", information);
```

<img src="./images/infoOutput.png" alt="" style="width:60%;padding:0 20%;"/>

`debug()` is the same as the `log()` which prints out message with log level `debug` 🐞

```javascript
const debugInfo = "This is some debug information";

console.debug("Message value:", debugInfo);
```

<img src="./images/debugOutput.png" alt="" style="width:60%;padding:0 20%;"/>

`warn()` prints out the message but as a warning ⚠️

```javascript
const warning = "This is a warning";

console.warn("Message value:", warning);
```

<img src="./images/warnOutput.png" alt="" style="width:60%;padding:0 20%;"/>

`error()` prints out the message but as an error ❌

```javascript
const error = "This is an error";

console.error("Message value: %s", error);
```

<img src="./images/errorOutput.png" alt="Console assert" style="width:60%;padding:0 20%;"/>

# **2. Styling the console output**

You can use the `%c` directive inside any of the logging methods to style the console output.

The text before the `%c` will not be affected, and everything after the directive will be styled as per the `CSS declaration`.

If you want to use multiple `%c` directives then you can provide the same number of `CSS declarations` as parameters.

```javascript
console.log(
  "This %cstory is about the %cConsole in JavaScript",
  "color: green; font-style: bold;font-size:18px;padding: 2px",
  "color: red; font-style: bold;font-size:28px; background-color: cyan;padding: 2px"
);
```

<img src="./images/styleOutput.png" alt="Console assert" style="width:60%;padding:0 20%;"/>

The properties usable along with the `%c` syntax are as follows (at least, in Firefox but they may differ in other browsers):

- background and its longhand equivalents.
- border and its longhand equivalents
- border-radius
- box-decoration-break
- box-shadow
- clear and float
- color
- cursor
- display
- font and its longhand equivalents
- line-height
- margin
- outline and its longhand equivalents
- padding
- text-\* properties such as text-transform
- white-space
- word-spacing and word-break
- writing-mode

# **3. Displaying objects and HTML/XML in a pretty way using dir() and dirxml()**

The `dir()` outputs an interactive list of properties in the form of a Javascript Object for the given object, and you can expand to see all the available child properties and methods.

```javascript
console.dir(document.location);
```

<img src="./images/dirOutput.png" alt="Console assert" style="width:60%;padding:0 20%;"/>

The `dirxml()` outputs an interactive tree for the given `HTML/XML` element.If it is not possible to display the given element like a tree, then it will be displayed as Javascript Object, and you can expand the tree to see the contents of child nodes for the given element.

```javascript
console.dirxml(document);
```

<img src="./images/dirxmlOutput.png" alt="Console assert" style="width:60%;padding:0 20%;"/>

# **4.Display data in tabular form using table**

The `table()` takes a single parameter of `data`(mandatory), which can either be an array or an object and an optional parameter of `columns`. Each element in the given array (or a property in an object) will be a row in the displayed table.

The first column of the table will be labeled `index` if the given parameter is an array with the `indices` as values, and in case of an object, the values will be `property names` of that object.

Displaying an array

```javascript
const developers = ["Kyle", "John", "Sally"];

console.table(developers);
```

<img src="./images/tableArrayOutput.png" alt="Console assert" style="width:60%;padding:0 20%;"/>

Displaying of compound types:

Displaying array of arrays

```javascript
const developers = [
  ["Kyle", "Renner"],
  ["John", "Parker"],
  ["Sally", "McKenzy"],
];

console.table(developers);
```

<img src="./images/table2x2Output.png" alt="Console assert" style="width:60%;padding:0 20%;"/>

Displaying array of objects

```javascript
function Developer(firstName, lastName) {
  this.firstName = firstName;
  this.lastName = lastName;
}
const kyle = new Developer("Kyle", "Renner");
const john = new Developer("John", "Parker");
const sally = new Developer("Sally", "McKenzy");

console.table([kyle, john, sally]);
```

<img src="./images/tableArrayObjectOutput.png" alt="Console assert" style="width:60%;padding:0 20%;"/>
Displaying object whose properties are objects.

```javascript
function Employee(firstName, lastName) {
  this.firstName = firstName;
  this.lastName = lastName;
}

const company = {};

company.CEO = new Employee("Kyle", "Renner");
company.CTO = new Employee("John", "Parker");
company.CFO = new Employee("Sally", "McKenzy");

console.table(company);
```

<img src="./images/tableObjectOutput.png" alt="Console assert" style="width:60%;padding:0 20%;"/>
Restricting the columns of the table using an optional second parameter

```javascript
function Developer(firstName, lastName) {
  this.firstName = firstName;
  this.lastName = lastName;
}
const kyle = new Developer("Kyle", "Renner");
const john = new Developer("John", "Parker");
const sally = new Developer("Sally", "McKenzy");

console.table([kyle, john, sally], ["firstName"]);
```

<img src="./images/table2ndParamOutput.png" alt="Console assert" style="width:60%;padding:0 20%;"/>

You can sort the table based on a particular column by clicking on that column's label

<img src="./images/tableSortedOutput.png" alt="Console assert" style="width:60%;padding:0 20%;"/>

# **5. Count the number of times a message is getting printed out using count and countReset**

`count()` prints out the number of times the call has been made to `count()` using the same label, and `countReset()` resets the counter value to `0` for the given label.

```javascript
function counter() {
  console.count("Call to counter");
}

counter(); //  ✅  Call to counter: 1

counter(); //  ✅  Call to counter: 2

console.countReset("Call to counter");

counter(); //  ✅  Call to counter: 1

console.count("Simple Counter"); //  ✅  Simple Counter: 1
```

If calls are made to these functions without any label, then counting/resetting label would be `default`.

```javascript
function counter() {
  console.count();
}

counter(); //  ✅  default: 1

counter(); //  ✅  default: 2

console.countReset();

counter(); //  ✅  default: 1

console.count(); //  ✅  default: 2
```

# **6. Grouping similar or unrelated logs using group, groupCollapsed and groupEnd**

`group()` creates a new group and indents grouped logs in the console until groupEnd() is called.

groupCollapsed() is the same as group() but creates the group in collapsed mode by default in the console, the user will need to use the `disclosure button` to expand it to reveal the grouped logs within the collapsed group.

Grouping without labels

```javascript
console.group();
for (let i = 0; i < 50; i++) {
  console.log("outer logs");
}
console.log("hello");
console.group();
for (let i = 0; i < 100; i++) {
  console.log("inner logs");
}
console.groupCollapsed();
console.log("child log here");
console.groupEnd();
console.groupEnd();
console.groupEnd();
console.group();
console.log("other log here");
console.groupEnd();
```

<img src="./images/groupOutput.png" alt="Console assert" style="width:60%;padding:0 20%;"/>

Grouping with labels

```javascript
console.group("Outer group");
for (let i = 0; i < 50; i++) {
  console.log("outer logs");
}
console.log("hello");
console.group("Inner group");
for (let i = 0; i < 100; i++) {
  console.log("inner logs");
}
console.groupCollapsed("child group");
console.log("child log here");
console.groupEnd("child group");
console.groupEnd("Inner group");
console.groupEnd("Outer group");
console.group("Other group");
console.log("other log here");
console.groupEnd("Other group");
```

<img src="./images/groupLabeledOutput.png" alt="Console assert" style="width:60%;padding:0 20%;"/>

# **7. Displaying a message to the console based on a condition using assert**

`assert()` prints out a message to the console if the given condition is `false` and prints nothing to the console if the condition is satisfied.

Single object(string here) as a parameter

```javascript
const i = 1;
console.assert(i > 2, "The value of i is less than 2");
//  ❌ Assertion failed: The value of i is less than 2

console.assert(i < 2, "The value of i is greater than 2");
```

Multiple objects as parameters

```javascript
const i = 1;
const messageOne = "Hello";
const personTwo = { name: "John", age: 32 };
console.assert(i > 2, messageOne, personTwo);
//  ❌ Assertion failed: Hello { name: 'John', age: 32 }

console.assert(i < 2, messageOne, personTwo);
```

String with substitutions as parameters

All the substitutions that are supported by `log()` are also available for `assert()`

```javascript
const i = 1;
console.assert(i > 2, "The value %d is less than 2", i);
//  ❌ Assertion failed: The value of 1 is less than 2

console.assert(i < 2, "The value %d is greater than 2", i);
```

# **8. Calculate time taken for operations to complete using time, timeLog and timeEnd**

`time()` starts the timer to track the time taken for an operation to complete.

`timeLog()` logs out the current time that was started by the `time()`.

`timeEnd()` ends the timer that was started by `time()`

These functions can be called using a `label` as a parameter or without any parameter.

With a label as a parameter

```javascript
console.time("time taken");

for (let i = 0; i < 10000; i++) {
  //  do something here
}

console.timeLog("time taken"); //  ✅  time taken: 0.370ms

for (let i = 0; i < 10000; i++) {
  //  do something else here
}

console.timeEnd("time taken"); //  ✅  time taken: 13.962ms
```

Without any parameter (logs default as a label)

```javascript
console.time();

for (let i = 0; i < 10000; i++) {
  //  do something here
}

console.timeLog(); //  ✅  default: 0.466ms

for (let i = 0; i < 10000; i++) {
  //  do something else here
}

console.timeEnd(); //  ✅  default: 12.502ms
```

# **9. Displaying the stack trace for the origin of function invocation using trace**

`trace()` prints out the stack trace to the console and can be called with `zero or more objects` as a parameter

Without any parameter

```javascript
function outer() {
  function inner() {
    console.trace();
  }
  inner();
}

outer();
```

<img src="./images/traceOutput.png" alt="Console assert" style="width:60%;padding:0 20%;"/>

With parameters

```javascript
function outer() {
  function inner() {
    console.trace("hello", { name: "Kyle", age: 24 });
  }
  inner();
}

outer();
```

<img src="./images/traceParamOutput.png" alt="Console assert" style="width:60%;padding:0 20%;"/>

# **10. Clearing the console**

`clear()` clears out the whole console if the environment supports it

```javascript
const numberValue = 25;

const floatValue = 25.75;

const messageValue = "This is a message";

const objectValue = {
  name: "Kyle",
  age: 24,
  city: "Los Angeles",
};

console.log(numberValue, floatValue, messageValue, objectValue);

console.clear();
```

<img src="./images/clearOutput.png" alt="Console assert" style="width:60%;padding:0 20%;"/>
