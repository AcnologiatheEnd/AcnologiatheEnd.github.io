---
layout: post
title:      "how to reset a given content on the dom"
date:       2020-11-14 03:59:09 +0000
permalink:  how_to_reset_a_given_content_on_the_dom
---


It's really simple depending on what you want to do. For my project I just needed a function to delete all the contents within a given div.

First thing you want to do is to grab the name of the parent div of the contents you want deleted. In my case, it was const main = document.querySelector("#body").

Next, we will have to create a function to get all the work done. Since I'll be using this function quite a bit, I make sure that it is defined in the outermost scope, so I can use it whenever need again. 

function deleteAllCard(){
      main.querySelectorAll('*').forEach(n => n.remove());
    }
		
the queryselector with it's current argument will select all the content within out main variable we created. Then it's going to loop through all the content of main and delete them from the dom.


