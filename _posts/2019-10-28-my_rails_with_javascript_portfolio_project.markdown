---
layout: post
title:      "My Rails with JavaScript Portfolio Project."
date:       2019-10-28 21:13:52 +0000
permalink:  my_rails_with_javascript_portfolio_project
---



'Rails and JavaScript' project has a requirement to have a Ruby base, so I decided to rebuild my previous 'Ruby on Rails Project'. Basically what I had to do is to add a layer of JavaScript to my previous project in order to make my application more dynamic. At this point, the task to combine two languages together was quite interesting and challenging at the same time. Along with this project, I came across a lot of new and difficult challenges. However, challenges are exactly what I need, I believe that challenges help to expedite the learning process! That's how we learn a lot of new things in coding. With a lot of debugging and research, I feel more comfortable and able to look at my JavaScript coding from different perspectives.
I was not aware of how difficult this project was for everybody, but I have to admit it was pretty tough for me, but I handled it.
 I had a particular requirement for this project and I found quite an interesting one that I would like to describe in detail below. I want to talk about the difference between 'var', 'let' and 'const' variable declarations.
 I think a lot of people hesitate and at some point do not have a clear understanding of the difference between var, let, const - variable declaration. Lately, a lot of developers advise not to use 'var', and for newcomers in the field, like us, we need to know why not to use and what are the reasons.  Before ES6 come out in 2015 and presented us a lot of new interesting features in JS, we were using 'var' like one and only variable declaration, with ES6 we've got several more - 'let' and 'const', and after that, we start slowly to forgot about a 'var'. So what is the difference between these two and why some of us stop using 'var', let's figure out?
 
‘var’ - this declaration has a lot of tricky moments for us as coders, everything that we assign with 'var', as long as it is not located in the function scope, will be in global scope access.
```
function create() {
var age = 30;
}
// undefined
 
console.log(age);
//VM12921:1 Uncaught ReferenceError: age is not defined
```
If we take 'var' out of function scope it automatically becomes globally available, but the danger consists not only in that, the value of variable assigned with 'var' declaration also easy to change to a different one, which in the case when on one of the projects working more than one person can be followed by many bugs. The reason is because, without understanding people can assign the same variable to a different value several times, without knowing it. Or if you'll run some loop with the 'setTimeout' method,  with 'var' it's can work not in the way as you expected it. For example, like here instead of counting from 0 to 2 with a one-second delay it just gives us three-times 3: 
```       
for (var i = 0; i < 3; i++) {
setTimeout(function() {
console.log(i);
}, 1000);
}
// 3 3
```
And here is exactly that difference between 'var' and 'let' declarations. Let's see what happens if we use 'let' in this case:
```
for (let i = 0; i < 3; i++) {
setTimeout(function() {
console.log(i);
}, 1000);
}
// 0
    1
    2
```
So why does it's happening? Because 'let' uses block scope, not a lexical scope, that means that 'let' does not care about global or local, it does not care whether you are inside of a function or not. Instead, it cares about the block in which you are, and a block is basically anything with curly braces that is a 'function', 'for' loop or 'if' check. But if it's one variable created for that 'for' loop, one variable which we then change with every iteration, and this is a special behavior we get with 'let' with block scope variables in ‘for’ loops like this one here.
Also like 'var', a variable declared with 'let' can be updated within its scope. Unlike 'var', a 'let' variable cannot be re-declared within its scope. So while this will work:
```
    let greeting = "say Hi";
    greeting = "say Hello instead";
```
This will return an error:
```
    let greeting = "say Hi";
    let greeting = "say Hello instead";//error: Identifier 'greeting' has already been declare
 ```
However, if the same variable is defined in different scopes, there will be no error:
```
    let greeting = "say Hi";
    if (true) {
        let greeting = "say Hello instead";
        console.log(greeting);//"say Hello instead"
    }
    console.log(greeting);//"say Hi"
```
There is no error because both instances are treated as different variables since they have different scopes.
This fact makes ‘let’ a better choice than ‘var’. When using ‘let’, you don't have to bother if you have used a name for a variable before as a variable exists only within its scope.
Variables declared with the 'const' maintain constant values. 'const' declarations share some similarities with ‘let’ declarations:
'const' declarations are block-scoped
Like ‘let’ declarations, ‘const’ declarations can only be accessed within the block it was declared. For example:
```
function foo(){
const show = “hello” ;
}
console.log(show);  // Uncaught ReferenceError: show is not defined
```
'const' cannot be updated or re-declared
This means that the value of a variable declared with ‘const’ remains the same within its scope. It cannot be updated or re-declared. For example:
```
const number = 1
const number = 2
//Uncaught SyntaxError: Identifier 'number' has already been declared
```
But if we will assign variable with const to an object or array, we can change their value. If we will try like this it's not gonna work:
```
const  world = {forest: "trees"};
world= {forest: "grass"}; //Uncaught TypeError: Assignment to constant variable.
```
But if we will do in a little different way it will work fine.
```
const  world = {forest: "trees"};
world.forest =  "leaves";
world
//{forest: "leaves"}
```
So basically whenever you use an equal sign after a 'const' variable you'll get an error. But instead of assigning a new value to a "world", we assign it to property inside of the "world". 
So you possibly have a question, what kind of variable declaration should I use and where?!?
Use 'let' for variables, use 'const' for variables that shouldn't change and don't use 'var', var is an old JavaScript and there isn't a reason to use it anymore, you can do the same thing better with 'let'. But if you see the logic in using 'var' for you, in some particular situation, go ahead and do it, but better to avoid it.

