---
title: "Semantic UI Template for Paginate (Almost) Anything"
date: 2016-01-24 11:33
category: [Blog]
tags: [angularjs]
published: true
pinned: true
---

![dirPaginate with Semantic UI in plunker]({{ "/img/dirpaginate-semantic-ui-plunk.png" | prepend: site.baseurl }}){:class="pure-img"}

If you've tried using [Michael Bromley's](http://www.michaelbromley.co.uk/) AngularJS [Pagination Directive](http://www.michaelbromley.co.uk/blog/108/paginate-almost-anything-in-angularjs)
in a Semantic UI site, you'll probably notice that the pagination control renders like a regular unordered list.

<!--more-->

![dirPaginate broken in Semantic UI]({{ "/img/dirpaginate-broken-in-semantic-ui.png" | prepend: site.baseurl }}){:class="pure-img photo"}

## Pagination Directive

The directive is part of a [collection of utils available on GitHub](https://github.com/michaelbromley/angularUtils) and can be installed from
bower or npm, whichever suits your project best.

{% highlight bash %}
$ bower install angular-utils-pagination
{% endhighlight %}

{% highlight bash %}
$ npm install angular-utils-pagination
{% endhighlight %}

The directive replaces the use of `ng-repeat` for the page content, and includes a new directive to represent a set of page navigation buttons.
The control is designed for use in Bootstrap, which will be fine for the common case, but can be modified to use a custom template making it
very flexible - nice work Michael!

## New Template

I'm a big fan of [Semantic UI], and love how simple it is to style my [AngularJS] sites. Once I noticed the styles were broken, I started digging.
The solution is quick and simple, and involves creating a custom template for the page navigation directive to use Semantic UI.
I've based this off the pagination example in the [tables documentation](http://semantic-ui.com/collections/table.html).

Copy this template and save it in your project next to your other templates/views/partials as `dirPagination.tpl.html`.

{% highlight html %}
<div class="ui pagination menu" ng-if="1 < pages.length || !autoHide">
  <a class="icon item" ng-if="boundaryLinks" ng-class="{ disabled : pagination.current == 1 }" 
     href="" ng-click="setCurrent(1)">
    <i class="angle double left icon"></i>
  </a>
  <a class="icon item" ng-if="directionLinks" ng-class="{ disabled : pagination.current == 1 }" 
     href="" ng-click="setCurrent(pagination.current - 1)">
    <i class="left chevron icon"></i>
  </a>

  <a class="item" ng-repeat="pageNumber in pages track by tracker(pageNumber, $index)" 
     ng-class="{ active : pagination.current == pageNumber, disabled : pageNumber == '...' }" 
     href="" ng-click="setCurrent(pageNumber)">{{ pageNumber }}</a>

  <a class="icon item" ng-if="directionLinks" ng-class="{ disabled : pagination.current == pagination.last }" 
     href="" ng-click="setCurrent(pagination.current + 1)">
    <i class="right chevron icon"></i>
  </a>
  <a class="icon item" ng-if="boundaryLinks"  ng-class="{ disabled : pagination.current == pagination.last }" 
     href="" ng-click="setCurrent(pagination.last)">
    <i class=" angle double right icon"></i>
  </a>
</div>
{% endhighlight %}

## Reference the Template

To use the template, reference it in the pagination control directive as follows.

{% highlight html %}
<dir-pagination-controls template-url="path/to/dirPagination.tpl.html"></dir-pagination-controls>
{% endhighlight %}

Once you're done, your pagination controls should look like this, and function in exactly the same way as the vanilla Bootstrap version.
If there are updates to the directive, you may have to fix some things, but I'll try keep this up to date if anything does change.

![dirPaginate Semantic UI Pagination Controls]({{ "/img/dirpaginate-semantic-ui-pagination-controls.png" | prepend: site.baseurl }}){:class="pure-img photo"}

## Demo Site
 
The original repository includes a demo of the directive on Plunker which I've forked and updated with this template.
[Take a look at the demo](http://plnkr.co/edit/9A0A8OE6JPwtUBDyK9nr?p=preview) to see it in action!

Enjoy!

[Semantic UI]: http://semantic-ui.com/
[AngularJS]: https://angularjs.org/