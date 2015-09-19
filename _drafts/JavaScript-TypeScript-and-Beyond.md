---
title: "TypeScript, JavaScript, and Beyond"
date: 2015-09-04 11:22
categories: [Blog]
tags: [typescript, javascript]
published: true
pinned: true
---

Many JavaScript developers have been getting very excited over new the features in ECMAScript 6, which gives us a huge new set of features to help bring the language up to date with other modern languages. These are great features which will improve the experience of writing JavaScript, especially in large-scale applications with many developers, and hopefully improve the quality of the code we write in general.

<!--more-->

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

{% highlight javascript linenos %}
function hello(text) {
  return text.split(' ')
}

hello('my friend')
// ["my", "friend"]

hello(10)
// Uncaught TypeError: text.split is not a function
{% endhighlight %}

Some would argue that this is a powerful part of the language, and I have seem some clever use of this for all sorts of strange behaviour. However, there are libraries which make an attempt to protect the developer from this particular mistake by *throwing their own error* back at the developer:

{% highlight javascript linenos %}
function hello(text) {
  if (typeof text !== 'string')
    throw Error('text must be a string')
  return text.split(' ')
}

hello(10)
// Uncaught Error: text must be a string
{% endhighlight %}

There are many ways a developer can reduce the chance of these mistakes:

### An IDE (Integrated Development Environment)
Code inspection can help by warning the developer at development time, but to know that this is unintentional requires making assumptions which can get messy or give false positives.

### Linting
Using tools such as [JSHint](https://github.com/jshint/jshint) can detect errors and potential problems with JavaScript, and is widely accepted in the community to be used in large-scale projects. Standardised linting can help new or returning developers to understand code and make changes quickly and effectively.

### Building with Babel
If Babel fails to understand the intent of your code, it can warn of the problem before it builds. This makes a great sanity check, but will not be able to detect the scenario in the example above.

### Declarative intent
The simplest solution would be to have a step which can make use of *declared intent* and use this to warn of the problem. This is where TypeScript comes in, and boasts *types* as a core feature:

{% highlight javascript linenos %}
function hello(text: string) {
  return text.split(' ')
}

hello(10)
// Argument of type 'number' is not assignable to parameter of type 'string'.
{% endhighlight %}

This extra step will reduce many runtime mistakes, allowing the developer to concentrate on writing code, not fixing errors.

## TypeScript

The goal of TypeScript is to improve the experience and quality of application scale JavaScript. [Anders Hejlsberg](https://en.wikipedia.org/wiki/Anders_Hejlsberg), chief architect of Delphi and lead architect of C#,  worked on the development of TypeScript at Microsoft, and [introduced the language](https://channel9.msdn.com/posts/Anders-Hejlsberg-Introducing-TypeScript) as a solution to the state of tooling available at the time.

### Superset

> Typescript is a superset of JavaScript that that compiles to plain JavaScript.

![TypeScript Stack](http://imgur.com/Ak4b7OZ.png)

All JavaScript code *is TypeScript* code. This is because TypeScript is an extension of JavaScript with full support for existing JavaScript syntax. Anders also comments that the language passes all of the ECMAScript 262 tests, to prove that it is really in full support of the language.

### Existing Projects

Being 100% JavaScript compatible means developers wishing to introduce TypeScript into existing code bases can do so with little effort. This widens the surface area for TypeScript, and has helped it grow from version 0.8 to 1.5.4 already, and continues to improve thanks to the community's contributions and feedback.

### Transcompilation

The first step to using TypeScript is to pass all code through the [compiler, `tsc`](https://www.npmjs.com/package/typescript), which generates JavaScript code. This step is called *transcompilation* (or *transpilation* for short) and works sort of like a pre-processor or macro injector. TypeScript goes in, JavaScript comes out.

![TypeScript to JavaScript](http://i.imgur.com/bKoYDLE.png)

The power of the compiler lies within its ability to recognise types and be able to warn the user of type violations, including suggestions of what may be wrong. If everything is fine, the compiler will create code that looks exactly like JavaScript. Take the following example of a class:

{% highlight javascript linenos %}
class Customer {
  private _customerId: number
  
  constructor(customerId: number) {
    this._customerId = customerId
  }
  
  get customerId(): number {
    return this._customerId
  }
  
  sayHello(): void {
    console.log('Hello from customer ' + this._customerId + '!')
  }
}

var customer = new Customer(10)
customer.sayHello()
// Hello from customer 10!
{% endhighlight %}

When targeting ESCMAScript 5 for the output of this script, the compiler generates the following:

{% highlight javascript linenos %}
var Customer = (function () {
    function Customer(customerId) {
        this._customerId = customerId;
    }
    Object.defineProperty(Customer.prototype, "customerId", {
        get: function () {
            return this._customerId;
        },
        enumerable: true,
        configurable: true
    });
    Customer.prototype.sayHello = function () {
        console.log('Hello from customer ' + this._customerId + '!');
    };
    return Customer;
})();
var customer = new Customer(10);
customer.sayHello();
// Hello from customer 10!
{% endhighlight %}

The compiler has created a class with a prototype function and one object property for the customer ID.


### Types

In the example above, the `Customer` object expects a number for the ID when it is created. If a non-number type were used in the example, the compiler would show an error:

{% highlight javascript linenos %}
var customer = new Customer("10")
// error TS2345: Argument of type 'string' is not assignable to parameter of type 'number'.
{% endhighlight %}

This can be very helpful when developing or refactoring large code bases. In the absence of safe-refactoring tools like [ReSharper](https://www.jetbrains.com/resharper/), TypeScript shines. It's especially useful when automating builds, such that it can be used as a gated check-in mechanism to reduce bugs that reach production.

### Accessibility

In the previous example, the keyword `private` marks a property as inaccessible outside of the object's scope. It's important to understand that *this means nothing to JavaScript*, and only serves to help the TypeScript developers by scoping variables arbitrarily. There's nothing stopping a developer using the class above as follows:

{% highlight javascript linenos %}
var customer = new Customer(10)
customer._customerId = "potato"
customer.sayHello()
// Hello from customer potato!
{% endhighlight %}

This is valid when consuming the JavaScript code, but in TypeScript the compiler will display the following:
{% highlight javascript linenos %}
error TS2322: Type 'string' is not assignable to type 'number'.
error TS2341: Property '_customerId' is private and only accessible within class 'Customer'.
{% endhighlight %}

Even so, errors can be ignored, and the class can be used in this way *since this is just JavaScript*.

### Inheritance

Classes can be inherited with the `extends` keyword, which creates the class as an extension of the original properties of the base class. For example:

{% highlight javascript linenos %}
class DomainObject {
  protected _id: number
  
  constructor(id: number) {
    this._id = id
  }
  
  get getId(): number {
    return this._id
  }
}

class Customer extends DomainObject {
  constructor(customerId: number) {
    super(customerId)
  }

  sayHello(): void {
    console.log('Hello from customer ' + this._id + '!')
  }
}
{% endhighlight %}

The `super` keyword calls the base constructor, allowing the constructor chain to flow to the base class. 

### Future Proof

New features of JavaScript are fully supported by TypeScript. Anything which isn't specifically a TypeScript syntax will be passed through the compiler and written "as-is" in the output. If you wish to use a new API or syntax, go ahead and use it.

### Test