# JS Learnings

[Closures](#closures)
[Promises](#promises)



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





Inner-Function: It referred to as nested functions, are functions that are defined inside of another function.



        var add = function(v1, v2){
            function doAdd(){
                return v1 + v2;
            }
            return doAdd();
        }

        var foo = add(10, 10);     


    Note: One important characteristic of inner functions is that they have implicit access to the outer function’s scope.
    



Closures - A closure is created when an inner function is made accessible from outside of the function that created it. This typically occurs when an outer function returns an inner function. When this happens, the inner function maintains a reference to the environment in which it was created. 

    function add(value1) {
        return function doAdd(value2) {
            return value1 + value2;
        };
    }

    var increment = add(1);
    var foo = increment(2);

    
    
Note: “value1” is a local variable of add(), and a non-local variable of doAdd(). Non-local variables refer to variables that are neither in the local nor the global scope.  “value2” is a local variable of doAdd().



## Promises