# JavaScript Guidelines

## General Notes

- ### Use external JavaScript files. 
    Do NOT include JavaScript in-line in the page unless there is a good reason.

- ### Place Scripts at the Bottom of Your Page
    It is a best practice to just place our scripts just before the closing </body> tag.
The primary goal is to make the page load as quickly as possible for the user. When loading a script, the browser can't continue on until the entire file has been loaded. Thus, the user will have to wait longer before noticing any progress.
For optimal page performance, concatenate your JavaScript into as few files as possible.

- ### Comment Your Code
    JavaScript comments can be used to explain JavaScript code, and to make it more readable.

- ### Self-Executing Functions
    Instead of creating a function and then call it, it's quite simple to make the function run automatically when a page loads or a parent function  is called. To achieve that, wrap your function in parenthesis, and then append an additional set, which essentially calls the function.
    ```sh
    (function doSomething() {
      return {
          name: 'John',
         lastName: 'Doe'
       };
    })();
    ```

- ### Raw JavaScript Can Always Be Quicker Than Using a Library
    While Javascript libraries such as jQuery are very helpful and can save an enormous time when coding, they can never be as fast as raw Javascript. For example jQuery's "each" method is great for looping, but using a native "for" statement will always be an ounve quicker.
- ### Avoid using eval()
    Because it allows arbitrary code to be run, it also represents a security problem.

## Variables
Always use meaningful variable names that can be read as words.
#### Conventions
- Variable names should be camelCase.
- Boolean values should be prefixed with 'is', 'has' e.t.c. if at all possible.
- Cached jQuery objects can be prefixed with $.

#### Best Practices

- ### Avoid global variables
    Minimize the use of global variables and functions. Global variables and functions can be overwritten by other scripts. Use local variables instead, and learn how to use closures.
    If referencing a window or global level variable that isn't obvious, please comment as such or explicitly state it. 

- ### Always declare variables
    All variables used in a function should be declared as local variables.
Local variables must be declared with the var(or let as for ECMA Script 6) keyword, otherwise they will become global variables.
- ### Declarations on Top
    Put all declarations at the top of each script or function. That way we:
    - Have cleaner code
    - Provide a single place to look for local variables
    - make it easier to avoid unwanted global variables
    - reduce the possibility of unwanted re-declarations
    >By default, JavaScript moves all declarations to the top (JavaScript Hoisting).

    Also, it is a good practice from performance perspective, to declare variables used inside a for-loop before the execution. For example:
    ```sh
        // Instead of writing:
        for (var i = 0; i < items.length; i ++){
            //do something
        }
        
        // It is better to declare i, and also store the items.length to a variable before the for-loop
        // as JavaScript will not have to init i inside the for, neither calculate items.length inside each loop iteration.
        var i = 0,
            len = items.length;
            
        for (; i < len; i ++) {
            //do something
        }
    ```
    
    
- ### Never Declare Number, String, or Boolean Objects
    Always treat numbers, strings, or booleans as primitive values, not as objects. Also, declaring these types as objects, slows down execution speed. 
    ```sh
    var x = "John";             
    var y = new String("John");
    (x === y) // is false because x is a string and y is an object. 
    
    //Or even worse
    var x = new String("John");             
    var y = new String("John");
    (x == y) // is false because you cannot compare objects. 
    ```
    
    - Use {} instead of new Object()
    - Use "" instead of new String()
    - Use 0 instead of new Number()
    - Use false instead of new Boolean()
    - Use [] instead of new Array()
    - Use /()/ instead of new RegExp()
    - Use function (){} instead of new Function()

- ### Use === Comparison
    The == comparison operator always converts (to matching types) before comparison.
    The === operator forces comparison of values and type: 
    ```sh
    0 == "";        // true
    1 == "1";       // true
    1 == true;      // true
    
    0 === "";       // false
    1 === "1";      // false
    1 === true;     // false 
    ```
- ### Use Parameter Defaults
    If a function is called with a missing argument, the value of the missing argument is set to undefined.
    Undefined values can break your code. It is a good habit to assign default values to arguments.

- ### Booleans should be easily identifiable. Use prefixes like "is", "can", "has".
    ```sh
    var isAdmin = true;
    ```
## Writing and Fromatting JavaScript
- **Open braces** are preceded by a single space.
- **Open braces** should appear on the same line as their preceding argument.
- **Close braces** should appear at the same indentation as the statement preceding the opening brace
-  There should be no space characters between **parentheses** and their contents.
-  Use **semicolons** and do not rely on automatic semicolon insertion.
-  Each **comma** and **colon** (and semi-colons that don't end a line) should be followed by a single space.
-  **Binary** and **ternary operators** should have a single space on each side.
-  **Quoted values** should be in 'single quotes' so that double quotes may easily exist inside them.
- Conditional statements go on a new line followed by the opening brace.
- 'else' go on the same line as the brace.

    #### Best Practices
    - Avoid user-agent sniffing. Use feature detection - [modernizr](https://modernizr.com/)
    - Do not repeat yourself (i.e. keep your code DRY)
    - Do not modify JavaScript core objects .prototype unless you really know what you're doing.
    - Use method names that make sense, such as init() or setup() for code that starts things off. Be consistent on your project.
    
    #### JavaScript Performance
    
    One of the most costly operations a browser can perform is updating the DOM in the page via inefficient JavaScript techniques. The most important thing to know is that the more you do on a Web page with JavaScript, the more work is being done, the more memory and the bigger the footprint it can generate. Additionally, updating a complex DOM structure over and over in JavaScript can cause re-flow, repainting, and jank.
    
    - [10 ways to minimize reflows and improve performance](https://www.sitepoint.com/10-ways-minimize-reflows-improve-performance/)
    - [Minimizing browser reflow](https://developers.google.com/speed/articles/reflow)
    - [Write better jQuery](https://medium.com/coding-design/how-can-you-write-better-in-jquery-69788663201e)



## Javasctipt Essentials
- [Scopes and Closures](https://css-tricks.com/javascript-scope-closures/)

## Javascript Design Patterns
- [Modular Design Patterns: Private, Privileged, and Protected Members in JavaScript](https://www.sitepoint.com/modular-design-patterns-in-javascript/)
- [4 design patterns you should know](https://scotch.io/bar-talk/4-javascript-design-patterns-you-should-know)
- [Learning JavaScript Design Patterns - Book](https://addyosmani.com/resources/essentialjsdesignpatterns/book/)








