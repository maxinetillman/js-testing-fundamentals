### Intro


## Errors 

Simplest form of a test:
Saving result in a variable. 
Saving an expected value in a variable. 
We run our script 'node index.js' 
If result does not equal to expected value, then we throw an error. 

```
let result = sum(3,7);
let expected = 10; 
if (result !== expected){
    throw new Error(`${result} is not equal to ${expected}`)
}
```

If result does equal to expected value, our script passed. 

## Abstract Test Assertions into a Javascript Assertion Library

Adding abstraction in our simple tests can make writing tests easier. 
Abstraction = reduce complexity by removing unnecessery info 
Assertions we can add to make writing tests easier:
- create expect function that takes actual in
- return toBe(takes in expected value)
- if actual is not expect, throw error 

```
function expect(actual){
    return {
        toBe (expected){
            if(actual !== expected)
        throw new Error(`${actual} is not equal to ${expected}`)
        }
    }
}
```

We could also use:
toEqual(expected){},
toBeGreaterThan(){}

## Encapsulate and Isolate Tests by building a Javascript Testing Framework 

When an assertion hits an error, the rest of the tests don't run. Developers can identify problem is much better if all tests are run. 

If we continued to write tests like we wrote expect() function above, when an error occurs all tests will stop running, when we look in our terminal, it will tell us the line in which the error occured but to get more meaningful and important information about why it error'd, we really have to read through a lot of cryptic information. 

# Current way of testing:
- using our expect() function
```
result = subtract(7,3)
expected = 4
expect(result).toBe(expected)

```

# To overcome this: 
- create function called test
- takes in title, callback
- wrap in 'try catch' 
- use console logs in try what passed or console errors in catch to advise what failed, use title to make v clear


``` 
function test(title, callback){
    try {
        callback()
        console.log(`✔️ ${title}`)
    } catch (error) {
        console.error(`❌ ${title}`)
    }
}

function subtractTest(){
    result = subtract(7,3)
    expected = 4
    expect(result).toBe(expected)
}

test('subract subtracts numbers', subtractTest)

// when we look at the console or terminal, 
we will see a really specific error message! 

```
