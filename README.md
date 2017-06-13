# JS Learnings

[Closures](#closures)



## Closures
Before we should understand the concept of closure, there are two other features of javascript that must be understood - _first-class-functions_ and _inner-functions_

    First-Class-Function: It can be constructed at runtime and assigned to variables. 
    They can also be passed to, and returned by other functions.

    
        var foo = function(){
            console.log('Hello');
        }

        var bar = function(args){
            return args;
        }

        bar(foo)();
    