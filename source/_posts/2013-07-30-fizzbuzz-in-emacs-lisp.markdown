---
layout: post
title: "Fizzbuzz in Emacs Lisp"
date: 2013-07-30 19:36
comments: true
categories: emacs
---

I decided to try writing fizzbuzz in Emacs Lisp. Fizzbuzz is a perennial coding interview question. It's an extremely simple problem that a surprising number of job applicants can't solve. The object is to count from 1 to 100 and print out "fizz" if the number is divisible by 3, "buzz" if the number is divisible by 5, otherwise the number is printed.

I haven't used emacs lisp in quite a while so I figured Fizzbuzz would be a fun warm up to get me back in the groove.

{% gist 6108908 %}

- ` defun ` is a special form for creating functions in emacs lisp. 
- the second line is a document string. It will be displayed when a user calls ` describe-function fizzbuzz `. This can also be called by typing the shortcut `C-hf` and typing the function name. 
- ` (interactive) ` allows the user can call the function interactively with ` M-x fizzbuzz ` while in emacs.
- ` mapcar ` applies a function (in this case an anonymous lambda function) to each element in a list.
- ` cond ` is the elisp King of Conditionals. 
It is like a case statement. The first argument is evaluated as a boolean and if it evaluates to ` t ` (true), then the remaining arguments are run. Otherwise the next statement is tested.