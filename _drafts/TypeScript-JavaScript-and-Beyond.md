---
title: "TypeScript, JavaScript, and Beyond"
date: 2015-09-04 11:22
categories: [Blog]
tags: [typescript, javascript]
published: true
---

# TypeScript, JavaScript, and Beyond

Many JavaScript developers have been getting very excited over new the features in ECMAScript 6, which gives us a huge new set of features to help bring the language up to date with other modern languages. These are great features which will improve the experience of writing JavaScript, especially in large-scale applications with many developers, and hopefully improve the quality of the code we write in general.

*Take a look at the features listed at [es6-features.org](http://es6-features.org/) for an in depth view of what you can do in ES6.*

The problem with ES6 is that we can't quite yet use all of it due to the constraints of where the code will be executed. Not all features are [implemented in all browsers](https://kangax.github.io/compat-table/es6/), and different versions of Node.js (and hosting providers) require some work to get them enabled, such as the `--harmony` flag (see [the latest Node.js ES6 docs](https://nodejs.org/en/docs/es6/)). However, if you are happy with introducing a transpilation (compilation) step into your workflow, you *can* make use of most of these features today.

## Targeting JavaScript Versions

One of the most popular tools by far for transpiling JavaScript down through versions is [Babel](https://babeljs.io/).

> **ES2015 and beyond**
> By default, Babel ships with a set of ES2015 syntax transformers. These allow you to use new syntax, **right now** without waiting for browser support.

By *building* your ES6 JavaScript code and specifying ES5 as the target version, Babel will generate downgraded but fully functional JavaScript (although some features will need a [polyfill](http://babeljs.io/docs/usage/polyfill/) to work). This creates *compiled JavaScript code* which can run within any environment it was targeted for, and simplifies maintenance for [future ECMAScript versions](http://www.ecma-international.org/publications/standards/Ecma-262.htm) too.

## Reducing Mistakes

Being a dynamic language without requiring any compilation step, JavaScript will often frustrate developers. There are [many things wrong with the language](https://github.com/stevekwan/best-practices/blob/master/javascript/gotchas.md) that anyone who has been writing JavaScript for a while may have become acquainted with, and subsequently learn to avoid them or work around them.

Using a language which has many dynamic and flexible features can sometimes become confusing, especially due to the lack of an early warning system like a build step. Babel will give you a large portion of this, but overall it won't tell you when you're doing something by mistake, such as expecting a string but passing a number:

```js
function hello(text) {
  return text.split(' ')
}

hello('my friend')
> ["my", "friend"]

hello(10)
```
> Uncaught TypeError: text.split is not a function

Some would argue that this is a powerful part of the language, and I have seem some clever use of this for all sorts of strange behaviour. However, there are libraries which make an attempt to protect the developer from this particular mistake by *throwing their own error* back at the developer:

```js
function hello(text) {
  if (typeof text !== 'string')
    throw Error('text must be a string')
  return text.split(' ')
}

hello(10)
```
> Uncaught Error: text must be a string

There are many ways a developer can reduce the chance of these mistakes.

### An IDE (Integrated Development Environment)
Code inspection can help by warning the developer at development time, but to know that this is unintentional requires making assumptions which can get messy or give false positives.

### Linting
Using tools such as [JSHint](https://github.com/jshint/jshint) can detect errors and potential problems with JavaScript, and is widely accepted in the community to be required in any large-scale project. This also helps to align standards which helps new or returning developers to understand the code and make changes effectively.

### Building with Babel
If Babel fails to understand the intent of your code, it can warn of the problem before it builds. This makes a great sanity check, but will not be able to detect the scenario in the example above.

### Types
The simplest solution would be to have a step which can make use of *declared intent* and use this to warn of the problem. This is where TypeScript comes in, and boasts this as a core feature:

```js
function hello(text: string) {
  return text.split(' ')
}

hello(10)
```
> Argument of type 'number' is not assignable to parameter of type 'string'.

## TypeScript



TypeScript is a typed *superset* of JavaScript
This means it supports all the features of JavaScript, but also adds many new features which are not available in all editions of JavaScript.
Some of the main features are:
* Types - variables, parameters and function returns can be typed such that the compiler can warn the developer of any type mismatches
* Classes - create objects with private properties, public accessors, extend existing classes, and implement interfaces
* Modules - bundle classes, functions and interfaces into 

I've started to use TypeScript in my recent projects, and I'm having a blast using it. As you may already know, 
I write [nearly all my out-of-work personal projects](https://github.com/Codesleuth?tab=repositories) in JavaScript, and usually as Node.js modules.
There are many reasons why I use it over vanilla JavaScript, even though I consider myself adept with the language and its features (pains).