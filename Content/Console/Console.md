_[General](../README.md) > [JavaScript](./main.md) > [Console](./Console.md)_

# **JavaScript**

## **Console**

> Console is a Browser's built-in Debugger

### **Below are a few things you can do using the** `console`

If you want to log something based on a condition, then you can use `console.assert()` which takes two parameters, a condition check, and the message to be logged, if the condition is false.

```javascript
let i = 1;
console.assert(i > 2, "The value of 2 is less than 2");
```
*Output:*

<img src="./images/Console_assert.png" alt="Console assert" style="width:60%;padding:0 20%;"/>

You can log an object in a pretty way you can wrap it in braces `{}` but if you use `console.table()` it will print it in an organized way.

```javascript
let obj = { foo: 2, bar: 3 };
console.log( obj );
console.table(obj);
```
*Output:*

<img src="./images/Console_table.png" alt="Console table" style="width:60%;padding:0 20%;"/>

You can group any repetitive logs along with a label using `console.group()` which takes a label for the group as a parameter.

```javascript
console.group("grouping logs");
for(let i=0;i<10000;i++){
    console.log("pls work this time");
}
```
*Output:*

<img src="./images/Console_group.png" alt="Console group" style="width:60%;padding:0 20%;"/>

You can log an object in a detailed manner using `console.dir()` which takes the object itself as a parameter.

```javascript
let obj = { foo: 2, bar: 3 };
console.dir(obj);
```
*Output:*

<img src="./images/Console_dir.png" alt="Console dir" style="width:60%;padding:0 20%;"/>

You can keep track of a counter variable then you can use `console.count()` which takes a label as a parameter.

```javascript
// normal way of counting the clicks.
let clicks = 0;

clicks++;
console.log(clicks);
//  do something here
clicks++;
console.log(clicks);

// tracking count in a better way.
console.count('clicks');
//  something here
console.count('clicks');
```
*Output:*

<img src="./images/Console_count.png" alt="Console count" style="width:60%;padding:0 20%;"/>

You can check how much time a block of code took to execute using `console.time()` and `console.timeLog()` which both take the same label as a parameter and surrounding them along the block of code for which you want to calculate the time.

```javascript
console.time("time to complete");

for (let i = 0; i < 100000; i++) {
  //  do something here
}

console.timeLog("time to complete");
```
*Output:*

<img src="./images/Console_timeLog.png" alt="Console time and timeLog" style="width:60%;padding:0 20%;"/>

You can trace from where the function has invoked from using the `console.trace()` which takes label as a parameter.

```javascript
function bottom() {
  function top() {
    console.trace("who called upon me?");
  }
  top();
}
bottom();
```
*Output:*

<img src="./images/Console_trace.png" alt="Console trace" style="width:60%;padding:0 20%;"/>

You can style the contents of a log message by adding `%c` at the beginning of the log message in `console.log()` which takes the log message as the first parameter and styles as the second parameter.

```javascript
console.log('%c Javascript is beautiful','color:yellow;font-weight:bold;font-size:20px;background-color:green;');
```
*Output:*

<img src="./images/Console_with_Styles.png" alt="Console with Styles" style="width:60%;padding:0 20%;"/>

If you want to explore more about what `console` can offer, you use `console.log(console)` to see all those methods, and you can dive deeper to know what each one of them can do.

```javascript
console.log(console);
```
*Output:*

<img src="./images/Console_console.png" alt="Console of console" style="width:60%;padding:0 20%;"/>