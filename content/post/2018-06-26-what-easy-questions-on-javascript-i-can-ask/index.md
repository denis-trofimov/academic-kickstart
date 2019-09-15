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

`b();<br />
console.log(a);<br />
var a = 'Hello World!';<br />
function b() {<br />
console.log('Called b!');<br />
}<br />
` 

### Answer:

`Called b!<br />
Hello World!`

## 

## <span style="font-weight: 400;">Functions, Context, and Variable Environments</span>

### Question: What this code give to the console?

`function b() {<br />
var myVar;<br />
console.log(myVar);<br />
}<br />
function a() {<br />
var myVar = 2;<br />
console.log(myVar);<br />
b();<br />
}<br />
var myVar = 1;<br />
console.log(myVar);<br />
a();<br />
console.log(myVar);`

### Answer:

`1<br />
2<br />
1<br />
1`

## 

## <span style="font-weight: 400;">The Scope Chain</span>

### Question: What this code give to the console?

`function a() {<br />
function b() {<br />
console.log(myVar);<br />
}<br />
b();<br />
}<br />
var myVar = 1;<br />
a();<br />
b();`

### Answer:

`1<br />
Uncaught ReferenceError: b is not defined<br />
` 

## <span style="font-weight: 400;">What About Asynchronous Callbacks</span>

### Question: What this code give to the console?

`// long running function<br />
function waitThreeSeconds() {<br />
var ms = 3000 + new Date().getTime();<br />
while (new Date() < ms){}<br />
console.log('finished function');<br />
}<br />
function clickHandler() {<br />
console.log('click event!');<br />
}<br />
// listen for the click event<br />
document.addEventListener('click', clickHandler);<br />
waitThreeSeconds();<br />
console.log('finished execution');`

### Answer:

`finished function<br />
finished execution<br />
click event!`

 [1]: https://simpleprogrammer.com/store/products/javascript-launchpad/?c=jslp70&utm_source=drip&utm_medium=email&utm_campaign=js-launchpad-sale&utm_content=js-launchpad-sale-email-2&__s=25hdpkywdqsodfst7mgj&utm_source=drip&utm_medium=email&utm_campaign=JavaScript+LaunchPad+Introduction&utm_content=Q%26A+about+JavaScript+LaunchPad
 [2]: https://simpleprogrammer.com/