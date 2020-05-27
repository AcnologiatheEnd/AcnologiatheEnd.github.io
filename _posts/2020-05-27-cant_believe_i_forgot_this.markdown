---
layout: post
title:      "Can't believe I forgot this..."
date:       2020-05-27 17:03:31 +0000
permalink:  cant_believe_i_forgot_this
---


I was trying to get querySelector function to print out one of my html element but I kept on getting null. I spent hours trying to figure out if maybe I did something wrong in the html file or something. Turns out, the issue was a little bit of simpler one.


**const body = document.querySelector("p");
console.log(body);**

This wasn't printing to my console because it's being executed before the html file it is connected to is even loaded. So if I tried selecting the "p" element, javascript doesn't know that it exist at that moment.

What is the solution? 


**document.addEventListener("DOMContentLoaded", function() { 

const body = document.querySelector("p");
console.log(body);

})**

So we're telling javascript to wait until our html has succesfully loaded to the DOM to execute that specific block of code. Now we get that element printed to our console. What a relief.

