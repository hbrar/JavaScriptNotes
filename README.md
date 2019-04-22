#   JavaScript

#   Variables

##  Unary plus i.e. +'2' is same as Number('2')

##  Operations run from left to right 
    eg alert(2 + 2 + '1' ); // "41" and not "221"

##  If one of the operands is a string, the other one is converted to a string too.
    eg alert( '1' + 2 ); // "12"

##  An operator always returns a value. Assignment is also an operator so always returns a value.         Chained assignments evaluate from right to left.
    eg a = b = c = 2 + 2; 
    First c = 2 + 2 is evaluated and it returns a value of 4
    Then b = 4 is evaulated and it returns a value of 4 and so on.

##  The prefix form returns the new value while the postfix form returns the old value (prior to          increment/decrement). If the result of increment/decrement is not used, there is no difference in     which form to use:

    let counter = 0;
    counter++;
    ++counter;
    alert( counter ); // 2, the lines above did the same

    let counter = 1;
    let a = counter++; // (*) changed ++counter to counter++

    alert(a); // 1

#   Comparisons

##  When comparing values of different types, JavaScript converts the values to numbers
    eg alert( '01' == 1 ); // true, string '01' becomes a number 1
    but in case of "23" > "20", values won't be converted to numbers since they are of same type.
    Hence dictionary order will be used for comparison of strings "23" and "20"
    
##  A regular equality check ==, converts operands of different types to numbers(except null and          undefined). Hence 0 == false is true but not 0 === false

    equality check == and comparisons > < >= <= work differently. Comparisons convert null to a number, treating it as 0. That’s why  null >= 0 is true and  null > 0 is false.

    On the other hand, the equality check == for undefined and null is defined such that, without any conversions, they equal each other and don’t equal anything else. That’s why null == 0 is false.

    alert( null > 0 );  // (1) false
    alert( null == 0 ); // (2) false
    alert( null >= 0 ); // (3) true
    
    alert( null == undefined ); // true

    The value undefined shouldn’t be compared to other values:
    alert( undefined > 0 ); // false (1)
    alert( undefined < 0 ); // false (2)
    alert( undefined == 0 ); // false (3)

    Comparisons (1) and (2) return false because undefined gets converted to NaN and NaN is a special numeric value which returns false for all comparisons.
    The equality check (3) returns false because undefined only equals null and no other value.

    If one operand in comparison operator is number other is converted to number as well.
    eg. "20" > 10 //true
    but ""

#   If Else

##  The if (…) statement evaluates the expression in its parentheses and converts the result to a         boolean. A number 0, an empty string "", null, undefined, and NaN all become false. Because of
    that they are called “falsy” values.

#   Logical operators
##  If an operand is not a boolean, it’s converted to a boolean for the evaluation.
    eg 
    if (1 || 0) { // works just like if( true || false )
    alert( 'truthy!' );
    }
##  OR finds the first truthy value
    
    result = value1 || value2 || value3;
    The OR || operator does the following:

    Evaluates operands from left to right.
    For each operand, converts it to boolean. If the result is true, stops and returns the original value of that operand.
    If all operands have been evaluated (i.e. all were false), returns the last operand.

    alert( undefined || null || 0 ); // 0 (all falsy, returns the last value)
    alert( 1 || 0 ); // 1 (1 is truthy)

    let currentUser = null;
    let defaultUser = "John";

    let name = currentUser || defaultUser || "unnamed";

    alert( name ); // selects "John" – the first truthy value

    OR evaluates and tests them from left to right. The evaluation stops when a truthy value is reached, and the value is returned. This process is called “a short-circuit evaluation” because   it goes as short as possible from left to right

##  AND finds the first falsy value   

    result = value1 && value2 && value3;
    The AND && operator does the following:

    Evaluates operands from left to right.
    For each operand, converts it to a boolean. If the result is false, stops and returns the original value of that operand.
    If all operands have been evaluated (i.e. all were truthy), returns the last operand

    alert( 1 && 2 && null && 3 ); // null

##  A double NOT !! is sometimes used for converting a value to boolean type:
    Just like unary + is same as Number() !! is same as Boolean()

#   Functions
    
    When JavaScript prepares to run the script or a code block, it first looks for Function Declarations in it and creates the functions. As a result, a function declared as a Function Declaration can be called earlier than it is defined.

    For example, this works:

    sayHi("John"); // Hello, John

    function sayHi(name) {
    alert( `Hello, ${name}` );
    }

    When a Function Declaration is made within a code block, it is visible everywhere inside that block. But not outside of it.

    let age = prompt("What is your age?", 18);

    // conditionally declare a function
    if (age < 18) {

    function welcome() {
        alert("Hello!");
    }

    } else {

    function welcome() {
        alert("Greetings!");
    }

    }

    // ...use it later
    welcome(); // Error: welcome is not defined

##  Arrow Functions

    let sum = (a, b) => a + b;

    /* The arrow function is a shorter form of:

    let sum = function(a, b) {
    return a + b;
    };
    */

    if we have only one argument, then parentheses can be omitted, making that even shorter:
    let double = n => n * 2;

    If there are no arguments, parentheses should be empty (but they should be present):
    let sayHi = () => alert("Hello!");

#   Object
