# Debugging the Script that is Java
## The Stack
### The JavaScript interpreter processes one line of code at a time.  When a statement needs data from another function, it **stacks** (or piles) the new function on top of the current task.
* When a statement has to call some other code in order to do its job, the new task goes to the top of the pile of things to do.
* Once the new task has been performed, the interpreter can go back to the task in hand.
* Each time a new item is added to the stack, it creates a new execution context.
* Variables defined in a function (or execution context) are only available in that function.
## Execution Context & Hoisting pages 456 and 457
### 1. Prepare
* The new scope is created.
* Variables, functions, and arguments are created.
* The value of the **this** keyword is determined.
### 2. Execute
* Now it can assign values to variables
* Reference functions and run their code
* Execute statements
### Understanding that these two phases happen helps with understanding a concept called **hoisting**. You may have seen that you can:
* Call functions before they have been declared.
* Assign a value to a variable that has not yet been declared.
### The preperation phase is often described as taking all of the variables and functions and hoisting them to the top of the execution context.  Or you can think of them as having been *prepared*.
### Each execution context also creates its own **variables object**. This object contains details of all of the variables, functions, and parameters for that execution context.
## Understanding Scope
* In the interpreter, each execution context has its own variables object.  It holds the variables, functions, and parameters available within it.  each execution context can also access its parents **variables** object.
* Functions in JavaScript are said to have **lexical scope**.  They are linked to the object they were defined *within*. So for each execution context, the scope is the vurrent execution's **variables** object, plus the variables object for each parent execution context.
## Understanding Errors
* If a JavaScript statement generates an error, then it throws an **exception**. At that point, the interpreter stops and looks for exception-handling code.
* If you are anticipating that something in your code may cause an error you can use a set of statements to **handle** the error.  This is important because if the error is not handled, the script will just stop processing and the user will not know why.  So exception-handling code should inform users when there is a problem.
* Whenever the interpreter comes across an error, it will look for error-handling code.
## Error Objects (check out pages 460 and 461)
### When an **error** object is created, it will contain the following properties:
* **name**: Type of Execution
* **message**: Description
* **fileNumber**: Name of the JavaScript file
* **lineNumber**: Line number of error
### There are seven types of built-in error objects in JavaScript.
* **Error**: Generic error - the other errors are all based upon this error.
* **SyntaxError**: Syntax has not been followed.
* **ReferenceError**: Tried to reference a variable that is not declared/within scope.
* **TypeError**: An unexpected data type that cannot be coerced.
* **RangeError**: Numbers not in acceptable range.
* **URIError**: *encodeURI()*, *decodeURI()*, and similar methods used incorrectly.
* **EvalError**: eval() function used incorrectly.