---
layout: post
title: CSS, Sass, SCSS, Compass, Less, BEM, SMACSS, OOCSS, ACSS, CCSS, WTFSS?
redirect_from: "/css"
---

I’ve been thinking a lot about my CSS authoring, its current state and how it has changed over the years.

Typically when I start a new project I’ll use my own framework [Motherplate](https://github.com/leemunroe/motherplate). It uses SCSS and Compass. Most of the class names were’t originally based on any other framework. Not deliberately anyway.

**Most developers I know now use [Bootstrap](http://getbootstrap.com/)**. If a friend or startup comes to me with an app  they want design help with, usually it has been marked up with Bootstrap classes. Makes sense, especially if it’s their prototype or version 0. Bootstrap is fast and efficient.

Most projects I work on I typically "own" the CSS. This is great, but I tend to have my own conventions, either **documented in my head, or made up on the spot, which is a terrible way to manage CSS**. It makes it harder for others to contribute in the future. Harder to maintain larger projects. Harder to write clean code.

With the rise of Bootstrap, BEM, SMACCs and other frameworks and methodologies, there are common best practice recommendations when it comes to naming your elements.

### CSS (Cascading Style Sheets)

> Cascading Style Sheets (CSS) is a style sheet language used for describing the look and formatting of a document written in a markup language.
> — <cite>[Wikipedia](http://en.wikipedia.org/wiki/Cascading_Style_Sheets)</cite>

Back to basics. What we all (should) know. **Simple styling** but hard to maintain. Results in lots of styles. Lots of overrides. Lots of specificity. Lots of "!important".

{% highlight css %}
div {
  font-size: 14px;
  margin: 0 0 20px;
  padding: 10px;
}
{% endhighlight %}

### Sass/SCSS (Syntactically Awesome Style Sheets)

> Sass is the most mature, stable, and powerful professional grade CSS extension language in the world.
> — <cite><a href="http://sass-lang.com/">Sass-Lang</a></cite>

In 2007 along came Sass. Particularly useful for importing and maintaining **multiple stylesheets**. Very useful for **variables, repeating patterns** and all sorts of other powerful things.

Sass (Syntactically Awesome Style Sheets) came first. SCSS (Sassy CSS) came shortly after, with more familiar CSS syntax. You probably want to go with SCSS. I can't imagine not using SCSS on a project, and having to write pure CSS.

{% highlight scss %}
$primary-color: purple;
ul {
  font-size: 14px;
  margin: 0 0 20px;

  li {
    margin-bottom: 20px;

    a {
      color: $primary-color;
    }
  }
}
{% endhighlight %}

[More on Sass and SCSS](http://sass-lang.com/).

### Compass

> Compass is a Sass extension and... it has a bunch of ready-to-use CSS3 Mixins, except it has also added several other stuff that make it a more powerful companion tool to Sass.
> — <cite><a href="http://www.hongkiat.com/blog/saas-compass/">Hongkiat</a></cite>

Compass mixins come in very handy. For me, the biggest problem Compass solves is **browser specific prefixes**. Not having to type these out or worry about what styles need them takes a load off.

{% highlight scss %}
@import "compass/css3"
div {
  @include border-radius(5px);
  @include box-shadow(0 0 10px rgba(0, 0, 0, .1));
}
{% endhighlight %}

[More on Compass](http://compass-style.org/).

### Less

> Less is a CSS pre-processor, meaning that it extends the CSS language, adding features that allow variables, mixins, functions and many other techniques that allow you to make CSS that is more maintainable, themable and extendable.
> — <cite><a href="http://lesscss.org/">Less</a></cite>

Less is very **similar to Sass**, except it uses Node (Javascript) to compile (as opposed to Ruby). I’ve never actually used it myself.

[More on Less](http://lesscss.org/).

### OOCSS (Object Oriented CSS)

> ...a CSS “object” is a repeating visual pattern, that can be abstracted into an independent snippet of HTML, CSS, and possibly JavaScript. That object can then be reused throughout a site.
> — <cite><a href="https://github.com/stubbornella/oocss/wiki">Nicole Sullivan</a></cite>

Higher level thinking on how to **reuse styles, patterns and abstract modules**. Think in terms of having a primary module with modifiers. Don’t be too specific or go too deep, `.box-heading` rather than `ul li .box-heading`.

{% highlight html %}
<div class="item">
  <ul class="item-list">
    <li class="item-list--item">
      <h3 class="item-heading">...
{% endhighlight %}
{% highlight css %}
.item {
  ...
}
.item-list {
  ...
}.item-list--item {
  ...
}
.item-heading {
  ...
}
{% endhighlight %}

<a href="http://appendto.com/2014/04/oocss/">More on OOCSS</a>.

### SMACCS (Scalable and Modular Architecture for CSS)

> ...an attempt to document a consistent approach to site development when using CSS.
> — <cite><a href="https://smacss.com/">SMACSS</a></cite>

Jonathan Snook wrote the book on this. Recommendations and best practices on **how to name your elements and class names**.

Think in terms of base (defaults), modules (reusable parts), states (hidden, active) and themes. Use `--` for modifiers and `__` for submodules.

{% highlight html %}
<div class=“container”>
  <div class=“container-header”>
    <div class=“container-header__title”>
      <h1 class=“container-header__title--home”>
{% endhighlight %}

<a href="https://smacss.com/">More on SMACCS</a>

### BEM (Block, Element, Modifier)

> The BEM approach ensures that everyone participating in the development of a website is working with the same codebase and using the same terminology
> — <cite><a href="https://bem.info/method/">BEM Methodology</a></cite>

Similar to SMACCS, **naming conventions for your projects**. An easy way to name and easy for others to work with. A block could be a navigation menu of tabs. An element could be one of the tabs within that block. A modifier could be the active tab.

{% highlight html %}
<ul class="menu">
  <li class="menu__item">...</li>
  <li class="menu__item_state_current">...</li>
  <li class="menu__item">...</li>
</ul>
{% endhighlight %}

### CCSS (Component CSS)

> ...an architecture which simplifies the CSS authoring experience for large web applications
> — <cite><a href="https://github.com/sathify/CCSS">Satheesh Kumar</a></cite>

CCSS is **combines the best of SMACSS and BEM for Sass projects**. It acts as a boilerplate and set of guidelines for teams to use on their next project.

<a href="https://github.com/sathify/CCSS">More on CCSS</a>.

### ACSS (Atomic CSS)

> A collection of single purpose styling units for maximum reuse
> — <cite><a href="http://acss.io/">Atomic CSS</a></cite>

With ACSS you are addressing one particular style with each class name, meaning you can reuse your class names over and over throughout your markup.

{% highlight css %}
.m-10 {
  margin: 10px
}

.w-50 {
  width: 50%;
}
{% endhighlight %}

<a href="http://www.smashingmagazine.com/2013/10/challenging-css-best-practices-atomic-approach/">More on Atomic CSS</a>

### Atomic Design

*Edit: Atomic Design is not the same as Atomic CSS - thanks <a href="https://twitter.com/thierrykoblentz">Thierry</a>*

> Atomic design is methodology for creating design systems. There are five distinct levels in atomic design: Atoms, Molecules, Organisms, Templates, Pages.
> — <cite><a href="http://bradfrost.com/blog/post/atomic-web-design/">Brad Frost</a></cite>

Thinking in terms of systems when designing interfaces. **Atoms** are building blocks of matter e.g. form button. **Molecules** are groups of atoms e.g. a search form has a label, input and button. Molecules combine to make **organisms** and are sections of an interface e.g. a site header has search, navigation etc. **Templates** consist of groups of organisms. Think of a layout of a web page for example. And finally **pages** are specific instances of templates.

<a href="http://patternlab.io/about.html">More on Atomic Design</a>.

### Conclusions and observations

Reading through these different frameworks and methodologies gives you a better understanding of how to best name your classes. It makes me realize I've been writing rather sloppy CSS over the years.

Going forward I plan to use a **combination of SMACCs, OOCSS and BEM, and staying closer aligned to Bootstrap** for naming common components like buttons, alerts, form elements.

I've also recently modified [my own boilerplate](https://github.com/leemunroe/motherplate) to better align to this way of thinking, which included restructuring the CSS file tree:

<p class="aligncenter"><img src="{{site.baseurl}}/img/css-files.gif" alt="CSS File Structure" width="500"></p>

Finally here are some closing observations and tips that I try to stick to:

* Try to keep styles **less than 3 levels deep**
* Try **not to use !important**, only if really needed or obvious classes e.g. a hidden class
* **Stay away from Sass @extends** as a general rule of thumb - they can get confusing
* Write lots of **comments** to document your styles
* Have a standard **agreed way** for you and your team to **write CSS** - Harry Roberts has some great [CSS Guidelines](http://cssguidelin.es/)
* In addition, it's good practice to have a **pattern library** showcasing all the styled elements that are currently available
* Use a **linter** like Causes [scss-lint](https://github.com/causes/scss-lint) to keep your SCSS/CSS inline with those guidelines
* Try not to use **&#42; global selector**
* Prefix classes with `js-` for class names used as **Javascript hooks**
* Make classes and **modules reusable** throughout your project
* Instead of making up names, inspect **frameworks like Bootstrap** for similar components
* **Avoid using IDs** for styling

