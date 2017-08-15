# Promises and Fetch

## Introduction to promises

Every web developper needs to be able to develop asynchronous javascript with confidence and ease.

Callbacks are the default options to handle asynchronous code, but promises are the recommended option as it gives flexibility, intuitive syntax and easy error handling. 


## What is a Promise?

A **promise** is an object that may produce a single value some time in the future: either a resolved value, or a reason that it’s not resolved (e.g., a network error occurred). A promise may be in one of 3 possible states: fulfilled, rejected, or pending. Promise users can attach callbacks to handle the fulfilled value or the reason for rejection.

### How Promises Work

The promise object is used for deffered and asynchronous computations... which is not the most helpful definition. It is to help decide what will happen when an asynchronous code settles, and are not a pass for safely running long running exections. It is like a try catch wrapper around a piece of code tat will finish at an unpredictable time.  As a quick recap:

* Synchronous code: This is when one statement executes immediately after another in code, in a single timeline.
* Asynchronous code: This is when code is executed in an unknown or unpredicatbale time. Not expected to run in a single unbroken timeline. You should have no idea when these operations should complete. Network, event, thread and time based requests are usually asynchronous.

A promise is an object which can be returned synchronously from an asynchronous function. It will be in one of 3 possible states:
* **Fulfilled**: onFulfilled() will be called (e.g., resolve() was called)

* **Pending** - The initial state of a promise. The promise has not yet fulfilled or rejected.
* **Fulfilled** - The state of a promise representing a successful operation.
* **Rejected** - The state of a promise representing a failed operation.
* **Settled** - The promise is wither fulfilled or rejected.
Once settled, a promise can not be resettled. Calling resolve() or reject() again will have no effect. The **immutability** of a settled promise is an important feature.



A promise represents the result of an asynchronous operation. A promise is in one of four different states:


```
new Promise(function(resolve[, reject]) {
    var value =doSomething();
    if(thingWorked){
    }resolve(value);{
    else if(somethingWentWrong){
    //No Argument passed then rejected
    reject();
    }
}).then(function(value) {
  return nextThing(value);
}).catch(rejectFunction);

```

Promises lead to the next resolve in the chain and rejects lead to the next catch.


Callbacks are Javascript classic approach to collaborative asynchronous programming.
A callback is a function object that is passed to another function as a parameter and that  later on must be invoked under some circumstances: for example when an asynchronous function successfully completes a task, it invokes the callback function to give back control to the function that was previously executing, signaling that the task has completed.

### What advantages do promises provide over callbacks, what are the downsides of using promises?
There are many advatages to promises over callbacks:
* Firstly the code is more readable
* It helps dictate what the intended actions are for asynchronous code
* It is easier to error handle rather than manage hardcoding to find errors
* More flexible code avoiding the pyramid of doom 
* It is made to tell when an asyc code settles
* Gives a try catch wrapper for code

There are some disadvantages:
* This provides some lag to the usere which can be problematic
* It is to help decide what will happen when an asynchronous code settles, and are not a pass for safely running long running exections.  

### What is fetch and how do you use it?
``` fetch() ``` Fetch allows you to make network requests similar to XMLHttpRequest (XHR). The main difference is that the Fetch API uses Promises, which enables a simpler and cleaner API, avoiding callback hell and having to remember the complex API of XMLHttpRequest.

One of the great features of promises is the ability to chain them together. For fetch, this allows you to share logic across fetch requests.
If you are working with a JSON API, you'll need to check the status and parse the JSON for each response. You can simplify your code by defining the status and JSON parsing in separate functions which return promises, freeing you to only worry about handling the final data and the error case.
``` 
function status(response) {  
  if (response.status >= 200 && response.status < 300) {  
    return Promise.resolve(response)  
  } else {  
    return Promise.reject(new Error(response.statusText))  
  }  
}

function json(response) {  
  return response.json()  
}

fetch('users.json')  
  .then(status)  
  .then(json)  
  .then(function(data) {  
    console.log('Request succeeded with JSON response', data);  
  }).catch(function(error) {  
    console.log('Request failed', error);  
  });
  ```
 
### What is the downside of using Fetch()?

Some downsides of fetch() are :+1: 
* The Promise returned from fetch() won’t reject on HTTP error status even if the response is an HTTP 404 or 500. Instead, it will resolve normally (with ok status set to false), and it will only reject on network failure or if anything prevented the request from completing.
* By default, fetch won't send or receive any cookies from the server, resulting in unauthenticated requests if the site relies on maintaining a user session (to send cookies, the credentials init option must be set).

Fetch is a very explicit in it's use, you don’t get anything unless you ask for it. Generic use of fetch wont work if you don't specify all arguments because maybe:
1) The server uses cookie based authentication and fetch does not send cookies by default.
2) The server needs to know that the client will be able to handle a JSON encoded response.
3) The server is on a different sub-domain and CORS is disabled by default in fetch.
4) In order to block XSRF attacks, the server requires every API call to be accompanied by a custom X-XSRF-TOKEN header which proves that the API call is being made from my application page.

Example:
```
function addUser(details) {
  return fetch('https://api.example.com/user', {
    mode: 'cors',
    method: 'POST',
    credentials: 'include',
    body: JSON.stringify(details),
    headers: {
      'Content-Type': 'application/json',
      'Accept': 'application/json',
      'X-XSRF-TOKEN': getCookieValue('XSRF-TOKEN')
    }
  }).then(response => {
    return response.json().then(data => {
      if (response.ok) {
        return data;
      } else {
        return Promise.reject({status: response.status, data});
      }
    });
  });
}

//as opposed to the more simple example:
function handleErrors(response) {
    if (!response.ok) {
        throw Error(response.statusText);
    }
    return response;
}
fetch("http://httpstat.us/500")
    .then(handleErrors)
    .then(response => console.log("ok") )
    .catch(error => console.log(error) );
```

compared to axios:
```
function addUser(details) {
  return axios.post('https://api.example.com/user', details);
}
```
[more reading](https://medium.com/@shahata/why-i-wont-be-using-fetch-api-in-my-apps-6900e6c6fe78)
[more reading](https://www.tjvantoll.com/2015/09/13/fetch-and-errors/)
