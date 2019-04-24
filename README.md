#   JavaScript

##  Unary plus 
    +'2' is same as Number('2')

##  Operations run from left to right 
    alert(2 + 2 + '1' ); // "41" and not "221"

##  If one of the operands is a string, the other one is converted to a string too.
    alert( '1' + 2 ); // "12"

##  An operator always returns a value. Assignment is also an operator so always returns a value.         Chained assignments evaluate from right to left.
    a = b = c = 2 + 2; 
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
    alert( '01' == 1 ); // true, string '01' becomes a number 1
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

### Evaluates operands from left to right.
### For each operand, converts it to boolean. If the result is true, stops and returns the original value of that operand.
### If all operands have been evaluated (i.e. all were false), returns the last operand.

    alert( undefined || null || 0 ); // 0 (all falsy, returns the last value)
    alert( 1 || 0 ); // 1 (1 is truthy)

    let currentUser = null;
    let defaultUser = "John";

    let name = currentUser || defaultUser || "unnamed";

    alert( name ); // selects "John" – the first truthy value

### OR evaluates and tests them from left to right. The evaluation stops when a truthy value is reached, and the value is returned. This process is called “a short-circuit evaluation” because   it goes as short as possible from left to right

##  AND finds the first falsy value   

    result = value1 && value2 && value3;
##  The AND && operator does the following:

### Evaluates operands from left to right.
### For each operand, converts it to a boolean. If the result is false, stops and returns the original value of that operand.
### If all operands have been evaluated (i.e. all were truthy), returns the last operand

    alert( 1 && 2 && null && 3 ); // null

##  A double NOT !! is sometimes used for converting a value to boolean type:
##  Just like unary + is same as Number() !! is same as Boolean()

#   Functions
    
##  When JavaScript prepares to run the script or a code block, it first looks for Function Declarations in it and creates the functions. As a result, a function declared as a Function Declaration can be called earlier than it is defined. For example, this works:

    sayHi("John"); // Hello, John

    function sayHi(name) {
    alert( `Hello, ${name}` );
    }

##  When a Function Declaration is made within a code block, it is visible everywhere inside that block. But not outside of it.

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

### if we have only one argument, then parentheses can be omitted, making that even shorter:
    let double = n => n * 2;

### If there are no arguments, parentheses should be empty (but they should be present):
    let sayHi = () => alert("Hello!");

#   Object

##  Object Creation
    let user = new Object(); // "object constructor" syntax
    let user = {};  // "object literal" syntax
    
##  key is stored as a string. Object property keys may be either of string type, or of symbol type ONLY. Not numbers, not booleans, only strings or symbols, these two types.

##  Square brackets allow property name to be result of any expression like from a variable:

    let key = "likes birds";
    // same as user["likes birds"] = true;
    user[key] = true;
    
### Here, the variable key may be calculated at run-time or depend on the user input. And then we use it to access the property

##  Computed properties

### We can use square brackets in an object literal. That’s called computed properties.

    let fruit = prompt("Which fruit to buy?", "apple");

    let bag = {
      [fruit]: 5, // the name of the property is taken from the variable fruit
    };

    alert( bag.apple ); // 5 if fruit="apple"

### [fruit] means that the property name should be taken from fruit.

##  Property value shorthand

### In real code we often use existing variables as values for property names.

    function makeUser(name, age) {
      return {
        name: name,
        age: age
        // ...other properties
      };
    }

    let user = makeUser("John", 30);
    alert(user.name); // John
    
### Use property value shorthand to make it shorter. Instead of name:name we can just write name, like this:

    function makeUser(name, age) {
     return {
       name, // same as name: name
       age   // same as age: age
       // ...
      };
    }
##  Existence check

### Use 'in' to check if property exists on an object.

    let user = { name: "John", age: undefined };

    alert( "name" in user ); // true, user.name exists
    alert( "age" in user ); // true, user.age exists
    alert( user.age ); // undefined, user.age exists but value is undefined
    alert( user.address ); //undefined, user.address does not exist

### Do not use `name in user` in above code. JS engine will look for a variable name as key of the property

##  Walk over properties

    let user = {
      name: "John", 
      age: 30,
      isAdmin: true
    };

    for (let key in user) {
      // keys
      alert( key );  // name, age, isAdmin
      // values for the keys
      alert( user[key] ); // John, 30, true
    }
    
### Below code return undefined since prop is a variable and variable as key to property can only be used using obj[key] notation and not obj.key

    for(let prop in user){
        console.log(user.prop)
    }
    
##  Are objects ordered?

### integer properties are sorted, others appear in creation order

##  Copying by reference

### When an object variable is copied – the reference is copied, the object is not duplicated.

    let user = { name: "John", age: 10 };
    admin = user

    //user gets updated as well
    admin.city = 'long beach'

    console.log(user)

    // admin now holds reference to a new object and is no longer referencing user
    admin = {name: "admin"}
    console.log(admin)
    console.log(user)
 
##  Comparison by reference

### Two objects are equal only if they are the same object.
    let a = {};
    let b = a; // copy the reference

    alert( a == b ); // true, both variables reference the same object
    alert( a === b ); // true
    
    let c = {};
    let d = {}; // two independent objects

    alert( c == d ); // false
    
##  Const object

### A const object can be changed but can't be assigned a new object.

    const user = { name: "John", age: 10 };
    user.age = "26" //no issues
    user = {name: "admin"} //error
   
##  Cloning and merging, Object.assign

    Object.assign(dest, [src1, src2, src3...])//this statement returns the new object
    
### It copies the properties of all objects src1, ..., srcN into dest

    let user = { name: "John" };
    let permissions1 = { canView: true };
    let permissions2 = { canEdit: true };

    // copies all properties from permissions1 and permissions2 into user
    Object.assign(user, permissions1, permissions2);

    // now user = { name: "John", canView: true, canEdit: true }
### If the receiving object (user) already has the same named property, it will be overwritten. 

### Create a clone of object user

    let clone = Object.assign({}, user);
    
    //OR
    
    const user = { name: "John", age: 10 };
    let clone = {}
    Object.assign(clone, user);
    console.log(clone)
    
    //TypeError: Cannot convert undefined or null to object
    
    const user = { name: "John", age: 10 };
    let clone
    Object.assign(clone, user);
    console.log(clone)
  
### What if property is not a primitive?

    let user = {
      name: "John",
      sizes: {
        height: 182,
        width: 50
      }
    };

    let clone = Object.assign({}, user);

    alert( user.sizes === clone.sizes ); // true, same object

    // user and clone share sizes
    user.sizes.width++;       // change a property from one place
    alert(clone.sizes.width); // 51, see the result from the other one
    
### User `_.cloneDeep(obj)` method of lodash library for deep cloning in cases like above.

#   Symbol Type

##  Overview
### Symbol” value represents a unique identifier.A value of this type can be created using Symbol().
    
    // id is a new symbol
    let id = Symbol();

    // id is a symbol with the description "id"
    let id = Symbol("id");

###  Symbols are guaranteed to be unique. Even if we create many symbols with the same description, they are different values. Most values in JavaScript support implicit conversion to a string. Symbols don’t auto-convert to a string.

###  To get description of symbol.

    let id = Symbol("id");
    alert(id.toString()); // Symbol(id)

    //OR
    alert(id.description); // id

##  Hidden Properties

### Symbols allow us to create “hidden” properties of an object, that no other part of code can occasionally access or overwrite. Imagine that another script wants to have its own “id” property inside user, for its own purposes. That may be another JavaScript library, so the scripts are completely unaware of each other.

    let user = { name: "John" };

    //one script creates id
    let id = Symbol("id");
    user[id] = "ID Value";

    //Another script creates its own id
    let id = Symbol("id")
    user[id] = "Different ID Value"

### There will be no conflict, because symbols are always different, even if they have the same name. If we use "id" instead of a symbol, there will be conflict.

    let user = { name: "John" };

    // our script uses "id" property
    user.id = "ID Value";

    // ...if later another script the uses "id" for its purposes...

    user.id = "Their id value"
    // boom! overwritten! it did not mean to harm the colleague, but did it!

##  Symbols in a literal

### If we want to use a symbol in an object literal, we need square brackets because `id` is a variable/computed property. Even if `id` were a string i.e. `let id = "userid"`, we would use square bracket [id] = 12

    let id = Symbol("id");

    let user = {
    name: "John",
    [id]: 123 // not just "id: 123"
    };

##  Symbols are skipped by for…in while Object.assign copies both string and symbol properties.

##  Personal Recommendation: Always quote keys that are not Symbol.

    //String key

    let user = {
        "name" : "John" //instead of name : "John"
    }

    user["name"] //instead of user[name]

    //Symbol key
    let name = Symbol("Username")
    let user = {
        [name] : "John"
    }
    user[name]

##  Global symbols

### If you want same-named symbols to be same entities.

    // read from the global registry
    let id = Symbol.for("id"); // if the symbol did not exist, it is created

    // read it again
    let idAgain = Symbol.for("id");

    // the same symbol
    alert( id === idAgain ); // true

##  Method shorthand

### Shorter syntax is only for methods in an object literal, not for function.

    let user = {
    sayHi: function() {
        alert("Hello");
    }
    };

    // method shorthand looks better, right?
    let user = {
    sayHi() { // same as "sayHi: function()"
        alert("Hello");
    }
    };

    //Outside object literal, this form results in SyntaxError
    greet(){

    } 
  
##  Object methods, "this"

### "this" is not bound to any function. The value of this is evaluated during the run-time. It points to the object that called it.

    let user = {
        name : "Jon"
    }

    let admin = {
        name : "Snow"
    }

    function greet(){
        console.log(`Hi!, I am ${this.name}`)
    }

    user.sayHi =  greet
    admin.sayHi = greet
    user.sayHi() //Hi!, I am Jon
    admin['sayHi']() //Hi!, I am Snow
    greet() //undefined ...."this" is global object here which does not have variable "name". Global object is window in browser and module in Nodejs

### Example where "this" is easily lost

    let user = {
      name: "John",
      hi() { alert(this.name); },
      bye() { alert("Bye"); }
    };

    user.hi(); // John (the simple call works)

    // now let's call user.hi or user.bye depending on the name
    (user.name == "John" ? user.hi : user.bye)(); // Error!...
    
    //Above line of code is processed as below. 
    //  => (user.name == "John" ? alert(this.name) : alert("Bye"))() 
    //  => (alert(this.name))() // Now "this" is Global object

### Arrow functions have no “this”. Arrow functions are special: they don’t have their “own” this. If we reference this from such a function, it’s taken from the outer “normal” function.

##  Constructor, operator "new"
### Constructor functions technically are regular functions and used to create many similar objects. There are two conventions though:

### 1. They are named with capital letter first.
### 2. They should be executed only with "new" operator.

### When a function is executed as new User(...), it does the following steps:

### 1. A new empty object is created and assigned to this.
### 2. The function body executes. Usually it modifies this, adds new properties to it.
### 3. The value of this is returned.

    function User(name) {
      // this = {};  (implicitly)

      // add properties to this
      this.name = name;
      this.isAdmin = false;

      // return this;  (implicitly)
    }

    Example:

    function Movie(title){
      this.title = title;
      this.director =  null;
      this.playMovie = ()=>console.log(`Now Playing - ${this.title}`) //Arrow function binds this to outer function
    }
    m = new Movie("Batman")
    m.playMovie()
    console.log(m)

### Don't confuse function above with object literal syntax. Shorthand notations for properties won't work inside constructor function.

    function Movie(title){
      title, //Error because of comman and undefined variable - title
      director, //Error because of comman and undefined variable - director
      playMovie(){ //Error because function keyword is missing
        console.log(`Now Playing - ${this.title}`)
      }
    }

### Below object literal notation is perfectly fine provided title and director variables are defined already.

    let title = "Batman"
    let director = "Chris"
    let m = {
      title,
      director,
      playMovie(){
         console.log(`Now Playing - ${this.title} by ${this.director}`) //Now Playing - Batman by Chris
      }
      //playMovie : () => console.log(`Now Playing - ${this.title} by ${this.director}`) //returns undefined for "this" since arrow function does not bind it.
    }

### Rewrite constructor function Movie as below:

    function Movie(title){
      this.title = title;
      this.director =  null;
      this.playMovie = ()=>console.log(`Now Playing - ${this.title}`) //Here "this" refers to outer function and is completely unneccesary.
    }
    m = new Movie("Batman")
    m.playMovie()
    console.log(m)

### Below 2 forms are completely equivalent while second being better than first.

    //with "this" in arrow function. "this" is not needed here
    function Movie(title){
      this.title = title;
      this.director =  null;
      this.playMovie = ()=>console.log(`Now Playing - ${this.title}`)
    }
    m1 = new Movie("Batman")
    m1.playMovie()//Now Playing - Batman
    console.log(m1)//Movie { title: 'Batman', director: null, playMovie: [Function] }

    m2 = new Movie("Superman")
    m2.playMovie()//Now Playing - Superman
    console.log(m2)//Movie { title: 'Superman', director: null, playMovie: [Function] }

    //without "this" in arrow function. Better
    function Movie(title){
      this.title = title;
      this.director =  null;
      this.playMovie = ()=>console.log(`Now Playing - ${title}`)
    }
    m1 = new Movie("Batman")
    m1.playMovie()//Now Playing - Batman
    console.log(m1)//Movie { title: 'Batman', director: null, playMovie: [Function] }

    m2 = new Movie("Superman")
    m2.playMovie()//Now Playing - Superman
    console.log(m2)//Movie { title: 'Superman', director: null, playMovie: [Function] }

### Another way to achieve above is :

    let m1 = {
        "title" : "Batman",
        "director" : "Chris"
    }
    let m2 = {
        "title" : "Superman",
        "director" : "Chris"
    }

    //let playMovie = () =>console.log(`Now Playing - ${this.title} by ${this.director}`) //undefined, arrow function bind "this" to outer function which here is global object
    let playMovie = function(){
        console.log(`Now Playing - ${this.title} by ${this.director}`)
    } 
    m1.play = playMovie
    m2.play = playMovie

    m1.play()
    m2.play()


### Return from constructors. Usually, constructors do not have a return statement. Their task is to write all necessary stuff into this, and it automatically becomes the result. But if there is a return statement, then the rule is simple:

### If return is called with object, then it is returned instead of this.
### If return is called with a primitive, it’s ignored.

#   Advanced Functions

##  Rest parameters ...

### ... literally mean “gather the remaining parameters into an array”. The rest parameters must be at the end. 
### There is also a special "array-like object" named arguments that contains all arguments by their index. Hence you can use arguments.length, arguments[0] etc. Looks like [Arguments] { '0': 4, '1': 5, '2': 5, '3': 6 }
### Arrow functions do not have "arguments". If we access the arguments object from an arrow function, it takes them from the outer “normal” function.

    function sumAll(...numbers){
        console.log(numbers.reduce((m, n) => m + n))
        //Since arguments object is not an array, it does not support array functions. Below will generate an Error.
        //console.log(arguments.reduce((m, n) => m + n))
    }
    sumAll(4,5,5,6)

##  Spread operator ...

### Does opposite of rest parameter. Spreads an iterable when passed as argument. Note difference between parameter and argument.

    let numbers = [1,2,3]

    function add(one, two, three){
      console.log(one + two + three)
    }

    add(...numbers)

### Hence, when `...` is used in function call, it spreads the array but when used as parameter, it combines the arguments into  an array.

### Merging two arrays:

    let arr1 = [1,2,3]
    let arr2 = [4,5,6]
    let merged = [...arr1, ...arr2]

