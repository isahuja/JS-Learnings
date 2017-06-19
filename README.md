# JS Learnings

[Closures](#closures)<br>
[Promises](#promises)


## Closures<br>
Before we should understand the concept of closure, there are two other features of javascript that must be understood - _first-class-functions_ and _inner-functions_

<u>First-Class-Function</u>: It can be constructed at runtime and assigned to variables. 
    They can also be passed to, and returned by other functions.

    

    
        var foo = function(){
            console.log('Hello');
        }

        var bar = function(args){
            return args;
        }

        bar(foo)();





<u>Inner-Function</u>: It referred to as nested functions, are functions that are defined inside of another function.



        var add = function(v1, v2){
            function doAdd(){
                return v1 + v2;
            }
            return doAdd();
        }

        var foo = add(10, 10);     


    Note: One important characteristic of inner functions is that they have implicit access to the outer function’s scope.
    



<u>Closures</u> - A closure is created when an inner function is made accessible from outside of the function that created it. This typically occurs when an outer function returns an inner function. When this happens, the inner function maintains a reference to the environment in which it was created. 

        function add(value1) {
            return function doAdd(value2) {
                return value1 + value2;
            };
        }

        var increment = add(1);
        var foo = increment(2);

    
    
Note: “value1” is a local variable of add(), and a non-local variable of doAdd(). Non-local variables refer to variables that are neither in the local nor the global scope.  “value2” is a local variable of doAdd().


<br><br>
## Promises

Promises provide a simpler alternative for executing, composing, and managing asynchronous operations when compared to traditional callback-based approaches. They also allow you to handle asynchronous errors using approaches that are similar to synchronous <span style="color:blue">_try/catch_</span>.

<u>States of Promises</u><br> 
**Pending** - The underlying operation has not yet completed, and the promise is pending fulfillment. <br>
**Fulfilled** - The operation has finished, and the promise is fulfilled with a value. This is analogous(clear/forsure) to returning a value from a synchronous function.<br>
**Rejected** -  An error has occurred during the operation, and the promise is rejected with a reason. This is analogous to throwing an error in a synchronous function.


A promise is said to be settled (or resolved) when it is either fulfilled or rejected. Once a promise is settled, it becomes immutable, and its state cannot change. The ``` then ``` and ``` catch ``` methods of a promise can be used to attach callbacks that execute when it is settled. These callbacks are invoked with the fulfillment value and rejection reason, respectively.<br><br>


![alt text](img/idOX8.png "Promises")


Example:-<br>


        const promise =  new Promise((resolve, reject) => {
            // Perform some work (possibly asynchronous)
            // ...

            if(/* Work has successfully finished and produced "value" */){
                resolve(value);
            } else{
                // Something went wrong because of "reason"
                // The reason is traditionally an Error object, although
                // this is not required or enforced.
                let reason = new Error(message);
                reject(reason);

                // Throwing an error also rejects the promise.
                throw reason;
            }
        });


The then and catch methods can be used to attach fulfillment and rejection callbacks:

        promise.then(value =>{
            // Work has completed successfully,
            // promise has been fulfilled with "value"
        }).catch(reason => {
            // Something went wrong,
            // promise has been rejected with "reason"
        });
