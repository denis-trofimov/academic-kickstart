---
title: What easy questions on Javascript I can ask?
author: Denis Trofimov
type: post
date: 2018-06-25T23:29:33+00:00
url: /what-easy-questions-on-javascript-i-can-ask/
featured_image: WhatAboutAsynchronousCallbacks.png
accesspress_mag_post_template_layout:
  - global-template
accesspress_mag_sidebar_layout:
  - global-sidebar
categories:
  - learning
tags:
  - course
  - interview
  - javascript
  - learning
  - questions

---
In this post I speak about some basic Javascript quesions and answers, which I have made passing throught course [**JavaScript LaunchPad**][1] **by** **[Simple Programmer.com.][2]**

I have interviewed 3 persons in the year 2017 for developer position to the company I work for, Vzor Systems LLC.

It turned out that to prepare for interview from the interviewer side one should do some effort. If the company is not a big but a small startup, it is my job as interviewer to think of questions and written tests to check a candidate\`s skills and knowledge. One time I was looking for typical questions on interview for C++ developer position.

Having an interviewer field of view in mind, I created this questions list when I have finished first **[JavaScript LaunchPad][1] **chapter &#8220;**Execution Contexts and Lexical Environments&#8221;.**

<!--more-->

## <span style="font-weight: 400;">The Execution Context &#8211; Creation & Hoisting</span>

### Question: What this code give to the console?

```javascript
b();
console.log(a);
var a = 'Hello World!';
function b() {
  console.log('Called b!');
}
```

### Answer:

```javascript
Called b!
Hello World!
```

## 

## <span style="font-weight: 400;">Functions, Context, and Variable Environments</span>

### Question: What this code give to the console?

```javascript
function b() {
  var myVar;
  console.log(myVar);
}
function a() {
  var myVar = 2;
  console.log(myVar);
  b();
}
var myVar = 1;
console.log(myVar);
a();
console.log(myVar);
```

### Answer:

```javascript
1
2
1
1
```

## 

## <span style="font-weight: 400;">The Scope Chain</span>

### Question: What this code give to the console?

```javascript
function a() {
  function b() {
    console.log(myVar);
  }
  b();
}
var myVar = 1;
a();
b();
```

### Answer:

```javascript
1
Uncaught ReferenceError: b is not defined
``` 

## <span style="font-weight: 400;">What About Asynchronous Callbacks</span>

### Question: What this code give to the console?

```javascript
// long running function
function waitThreeSeconds() {
  var ms = 3000 + new Date().getTime();
  while (new Date() < ms){}
  console.log('finished function');
}
function clickHandler() {
  console.log('click event!');
}
// listen for the click event
document.addEventListener('click', clickHandler);
waitThreeSeconds();
console.log('finished execution');
```

### Answer:

```javascript
finished function
finished execution
click event!
```

 [1]: https://simpleprogrammer.com/store/products/javascript-launchpad/?c=jslp70&utm_source=drip&utm_medium=email&utm_campaign=js-launchpad-sale&utm_content=js-launchpad-sale-email-2&__s=25hdpkywdqsodfst7mgj&utm_source=drip&utm_medium=email&utm_campaign=JavaScript+LaunchPad+Introduction&utm_content=Q%26A+about+JavaScript+LaunchPad
 [2]: https://simpleprogrammer.com/