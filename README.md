# Debug Guide

- [Debug Guide](#debug-guide)
    - [Open a Ticket](#open-a-ticket)
    - [Shortcut](#shortcut)
        - [Think about these things anytime you see an error](#think-about-these-things-anytime-you-see-an-error)
    - [Thoughts on Learning](#thoughts-on-learning)
        - [Ask for help, we do not get tired of questions, even if we end up telling you to search most of your question online](#ask-for-help-we-do-not-get-tired-of-questions-even-if-we-end-up-telling-you-to-search-most-of-your-question-online)
    - [Big Note for Beginners](#big-note-for-beginners)
    - [Process](#process)
        - [This section will be continually updated](#this-section-will-be-continually-updated)
    - [Examples](#examples)
        - [Example 1: `undefined` variable](#example-1-undefined-variable)
        - [Example 2: Not passing in correct amount of parameters](#example-2-not-passing-in-correct-amount-of-parameters)
        - [Example 3: Treating my variables as the wrong data type](#example-3-treating-my-variables-as-the-wrong-data-type)

## Open a Ticket

Ask yourself these questions, and prepare an answer for each of them before asking for help.

* What is your code doing? 
* What should it do?
* How do you know it doesn’t work? (Does it show an error message, or is it not working the way you want it to?)
* What have you tried to fix it, and why?



## Shortcut 

### Think about these things anytime you see an error

* Use `console.log` to triangulate where your code breaks
* Are you dealing with a ***syntax error***? Does the code say `TypeError` or `undefined does not have a property length`?
    * Check for spelling of your variables
    * Are all your variables declared somewhere?
    * Are you treating your variables as the ***correct data type***?
* Is it a ***logic error***? Is your code actually doing what you think it is doing?
    * Write out an ***environment diagram*** (where you list out all your variables and what they are at each step)
* Refactor code into smaller helper functions so you can test smaller parts of your large code block
* Comment out code and bring your code back to a working status, then slowly add back your code you commented till it breaks (triangulating errors)



## Thoughts on Learning

### Ask for help, we do not get tired of questions, even if we end up telling you to search most of your question online
* We will show you the answer often, especially in the beginning and especially with syntax questions
* However, expect that if we point you to a tool (i.e. a built-in function you should check out), you will have to do some ***research yourself*** on Google
* If you still do not understand how to solve the problem, we will help further

No one is any less a student or a person for being frustrated and stuck with documentation, 
especially in the beginning. 

We ask for everyone to research their questions first not because we do not want to help, but because it will make you good at solving the basic problems of programming:

* ***Syntax***. Spelling and using the right format for your code.
* ***Configuration problems***. Example: setting up a React project (usually people have solutions out there for you already).

What we will most want to help on, and what you will most want our help on, are ***logic problems***. These do not
always give an error, and that is why these are the most challenging for all programmers.



## Big Note for Beginners

Have a belief about all of your variables. You should know (write it down if you're unsure) what your variables are most of the time.
Data type is essential, you should never guess what data type your variables are and continue coding a long time without confirming what they are. 

You can confirm the data type by using `console.log` or using a function with the variable without erroring.



## Process 

| More Thorough Debugging Tips                                 |
| :----------------------------------------------------------- |
| Write out your beliefs about your code (what you think your variables look like) |
| Triangulate your bug, test each belief and assumption you have about your code |
| If you coded a lot without testing your code, and now you are lost at where to even start looking for your bug, start by removing code one line/block at a time until you get back to a working code block, then start adding in code one line/group at a time. When you reach your error again, you will have found the suspect. |
| You may also want to clean up your code by refactoring it into smaller functions and then testing the smaller functions. |
| Reproduce your error after you fixed it, did it come back again? This teaches you a lot about the nature of your bug, and general programming ideas you might have had that were wrong. |
| Build small, test often. Use helper functions where you can. |
| If you feel you are too far gone, you can always start over, this time with more modular code. |
| Understand the question prompt, read it aloud and stop where it doesn't make sense. |
| Read your error codes, does it point you to a place in your file? After looking through all of them is there any part of it that makes sense? (recognizable files) |



---
### This section will be continually updated


## Examples


### Example 1: `undefined` variable

```javascript
// Why does this give an error?
function hello() {
    return 'Hello, ' + person;
}

hello();    // error code shows 'person' is not defined
```

Given this example, I would ask a student:
* First: What can you gather from the error message you see?
* Secondly: Take note of the `person` variable, is it defined somewhere?

If the student still does not understand the error, I will ask:
* Did you mean to add `person` as an parameter for your function?
* Perhaps you meant to reference a `person` variable somewhere else?

---


### Example 2: Not passing in correct amount of parameters

```javascript
function removeItemFromArray(arr, index) {
    var copy = [...arr];    // making a copy of 'arr'
    copy.splice(index, 1);
    return copy;
}

removeItemFromArray([1, 2, 3, 4]);      // no error message; returns [2, 3, 4]
// How many inputs should this function take in?
```

What's wrong with this code?
* It doesn't give me an error message, and it seems to do something
* However, does it work for all cases?
* Should it even be working or is it just coding on side-effects (i.e. I don't know the logic of why it is working, but it is, so I don't care)
* The author of this code has forgot to put in a value in the index parameter, thus passing in `undefined`. The code will work if the goal was to remove index 0, but it will fail for any other case.
* This would still be a ***syntax*** error, because the author forgot to type in something. 

---


### Example 3: Treating my variables as the wrong data type

```javascript
var obj = [{ 
    name: 'patrick',
    age: 24
}];

console.log(obj.name);      // gives me back 'undefined'
```

What's wrong with this code?
* What type is variable `obj`? 
* It is an array, but the author of this treated it as if it was an object.
* `obj` is actually an array of length 1, with an object inside that has the attribute `name`. 

Solution
* Either remove the array notation and make `obj` just the object with `{ name, age }