# join

## join.isExist

### description

# enter
# learn (Edit)
# play
# exit

# node

## node.status



Flatdoc
=======

Flatdoc is a small JavaScript file that fetches Markdown files and renders them
as full pages. Essentially, it's the easiest
way to make open source documentation from *Readme* files.

 * No server-side components
 * No build process needed
 * Deployable via GitHub Pages
 * Can fetch GitHub Readme files
 * Gorgeous default theme (and it's responsive)
 * Just create an HTML file and deploy!

*Current version: [v0.9.0][dist]*

[![Build Status](https://travis-ci.org/rstacruz/flatdoc.svg?branch=gh-pages)](https://travis-ci.org/rstacruz/flatdoc)

Getting started
---------------

Create a file based on the template, which has a bare DOM, link to the
scripts, and a link to a theme. It will look something like this (not exact).
For GitHub projects, simply place this file in your [GitHub pages] branch and
you're all good to go.

*In short: just download this file and upload it somewhere.*

The main JS and CSS files are also available in [npm] and [bower].

[Default theme template >][template]

[Blank template >][blank]

[bower]: http://bower.io/search/?q=flatdoc
[npm]: https://www.npmjs.org/package/flatdoc

### Via GitHub

To fetch a Github Repository's readme file, use the `Flatdoc.github` fetcher.
This will fetch the Readme file of the repository's default branch.

``` javascript
Flatdoc.run({
  fetcher: Flatdoc.github('USER/REPO')
});
```

You may also fetch another file other than the Readme file, just specify it as
the 2nd parameter.

``` javascript
Flatdoc.run({
  fetcher: Flatdoc.github('USER/REPO', 'Changelog.md')
});
```

After you've done this, you probably want to deploy it via [GitHub Pages].

[GitHub Pages guide >][GitHub Pages]

### Via a file

You may also fetch a file. In this example, this fetches the file `Readme.md` in
the same folder as the HTML file.

``` javascript
Flatdoc.run({
  fetcher: Flatdoc.file('Readme.md')
});
```

You may actually supply any URL here. It will be fetched via AJAX. This is
useful for local testing.

``` javascript
Flatdoc.run({
  fetcher: Flatdoc.file('http://yoursite.com/Readme.md')
});
```

How it works
------------

Flatdoc is a hosted `.js` file (along with a theme and its assets) that you can
add into any page hosted anywhere.

#### All client-side

There are no build scripts or 3rd-party services involved. Everything is done in
the browser. Worried about performance? Oh, It's pretty fast.

Flatdoc utilizes the [GitHub API] to fetch your project's Readme files. You may
also configure it to fetch any arbitrary URL via AJAX.

#### Lightning-fast parsing

Next, it uses [marked], an extremely fast Markdown parser that has support for
GitHub flavored Markdown.

Flatdoc then simply renders *menu* and *content* DOM elements to your HTML
document. Flatdoc also comes with a default theme to style your page for you, or
you may opt to create your own styles.

Markdown extras
---------------

Flatdoc offers a few harmless, unobtrusive extras that come in handy in building
documentation sites.

#### Code highlighting

You can use Markdown code fences to make syntax-highlighted text. Simply
surround your text with three backticks. This works in GitHub as well.
See [GitHub Syntax Highlighting][fences] for more info.

    ``` html
    <strong>Hola, mundo</strong>
    ```

#### Blockquotes

Blockquotes show up as side figures. This is useful for providing side
information or non-code examples.

> Blockquotes are blocks that begin with `>`.

#### Smart quotes

Single quotes, double quotes, and double-hyphens are automatically replaced to
their typographically-accurate equivalent. This, of course, does not apply to
`<code>` and `<pre>` blocks to leave code alone.

> "From a certain point onward there is no longer any turning back. That is the
> point that must be reached."  
> --Franz Kafka

#### Buttons

If your link text has a `>` at the end (for instance: `Continue >`), they show
up as buttons.

> [View in GitHub >][project]

Customizing
===========

Basic
-----

### Theme options

For the default theme (*theme-white*), You can set theme options by adding
classes to the `<body>` element. The available options are:

#### big-h3
Makes 3rd-level headings bigger.

``` html
<body class='big-h3'>
```

#### no-literate
Disables "literate" mode, where code appears on the right and content text
appear on the left.

``` html
<body class='no-literate'>
```

#### large-brief
Makes the opening paragraph large.

``` html
<body class='large-brief'>
```

### Adding more markup

You have full control over the HTML file, just add markup wherever you see fit.
As long as you leave `role='flatdoc-content'` and `role='flatdoc-menu'` empty as
they are, you'll be fine.

Here are some ideas to get you started.

 * Add a CSS file to make your own CSS adjustments.
 * Add a 'Tweet' button on top.
 * Add Google Analytics.
 * Use CSS to style the IDs in menus (`#acknowledgements + p`).

### JavaScript hooks

Flatdoc emits the events `flatdoc:loading` and `flatdoc:ready` to help you make
custom behavior when the document loads.

``` js
$(document).on('flatdoc:ready', function() {
  // I don't like this section to appear
  $("#acknowledgements").remove();
});
```

Full customization
------------------

You don't have to be restricted to the given theme. Flatdoc is just really one
`.js` file that expects 2 HTML elements (for *menu* and *content*). Start with
the blank template and customize as you see fit.

[Get blank template >][template]

Misc
====

Inspirations
------------

The following projects have inspired Flatdoc.

 * [Backbone.js] - Jeremy's projects have always adopted this "one page
 documentation" approach which I really love.

 * [Docco] - Jeremy's Docco introduced me to the world of literate programming,
 and side-by-side documentation in general.

 * [Stripe] - Flatdoc took inspiration on the look of their API documentation.

 * [DocumentUp] - This service has the same idea but does a hosted readme 
 parsing approach.

Attributions
------------

[Photo](http://www.flickr.com/photos/doug88888/2953428679/) taken from Flickr,
licensed under Creative Commons.

Acknowledgements
----------------

© 2013, 2014, Rico Sta. Cruz. Released under the [MIT 
License](http://www.opensource.org/licenses/mit-license.php).

**Flatdoc** is authored and maintained by [Rico Sta. Cruz][rsc] with help from its 
[contributors][c].

 * [My website](http://ricostacruz.com) (ricostacruz.com)
 * [Github](http://github.com/rstacruz) (@rstacruz)
 * [Twitter](http://twitter.com/rstacruz) (@rstacruz)

[rsc]: http://ricostacruz.com
[c]:   http://github.com/rstacruz/flatdoc/contributors

[GitHub API]: http://github.com/api
[marked]: https://github.com/chjj/marked
[Backbone.js]: http://backbonejs.org
[dox]: https://github.com/visionmedia/dox
[Stripe]: https://stripe.com/docs/api
[Docco]: http://jashkenas.github.com/docco
[GitHub pages]: https://pages.github.com
[fences]:https://help.github.com/articles/github-flavored-markdown#syntax-highlighting
[DocumentUp]: http://documentup.com

[project]: https://github.com/rstacruz/flatdoc
[template]: https://github.com/rstacruz/flatdoc/raw/gh-pages/templates/template.html
[blank]: https://github.com/rstacruz/flatdoc/raw/gh-pages/templates/blank.html
[dist]: https://github.com/rstacruz/flatdoc/tree/gh-pages/v/0.9.0



Flatdoc
=======

Basic Flatdoc module.

The main entry point is `Flatdoc.run()`, which invokes the [Runner].

```js
Flatdoc.run({
  fetcher: Flatdoc.github('rstacruz/backbone-patterns');
});
```

These fetcher functions are available:

```js
Flatdoc.github('owner/repo')
Flatdoc.github('owner/repo', 'API.md')
Flatdoc.github('owner/repo', 'API.md', 'branch')
Flatdoc.bitbucket('owner/repo')
Flatdoc.bitbucket('owner/repo', 'API.md')
Flatdoc.bitbucket('owner/repo', 'API.md', 'branch')
Flatdoc.file('http://path/to/url')
Flatdoc.file([ 'http://path/to/url', ... ])
```



### Flatdoc.run()

Creates a runner.
See [Flatdoc].

### Flatdoc.file()

File fetcher function.

Fetches a given `url` via AJAX.
See [Runner#run()] for a description of fetcher functions.

### Flatdoc.github()

Github fetcher.
Fetches from repo `repo` (in format 'user/repo').

If the parameter `filepath` is supplied, it fetches the contents of that
given file in the repo's default branch. To fetch the contents of
`filepath` from a different branch, the parameter `ref` should be
supplied with the target branch name.

See [Runner#run()] for a description of fetcher functions.

See: http://developer.github.com/v3/repos/contents/

### Flatdoc.bitbucket()

Bitbucket fetcher.
Fetches from repo `repo` (in format 'user/repo').

If the parameter `filepath` is supplied, it fetches the contents of that
given file in the repo.

See [Runner#run()] for a description of fetcher functions.

See: https://confluence.atlassian.com/display/BITBUCKET/src+Resources#srcResources-GETrawcontentofanindividualfile
See: http://ben.onfabrik.com/posts/embed-bitbucket-source-code-on-your-website
Bitbucket appears to have stricter restrictions on
Access-Control-Allow-Origin, and so the method here is a bit
more complicated than for Github

If you don't pass a branch name, then 'default' for Hg repos is assumed
For git, you should pass 'master'. In both cases, you should also be able
to pass in a revision number here -- in Mercurial, this also includes
things like 'tip' or the repo-local integer revision number
Default to Mercurial because Git users historically tend to use GitHub

Parser
------

Parser module.
Parses a given Markdown document and returns a JSON object with data
on the Markdown document.

```js
var data = Flatdoc.parser.parse('markdown source here');
console.log(data);

data == {
  title: 'My Project',
  content: '<p>This project is a...',
  menu: {...}
}
```



### Parser.parse()

Parses a given Markdown document.
See `Parser` for more info.

Transformer
-----------

Transformer module.
This takes care of any HTML mangling needed.  The main entry point is
`.mangle()` which applies all transformations needed.

```js
var $content = $("<p>Hello there, this is a docu...");
Flatdoc.transformer.mangle($content);
```

If you would like to change any of the transformations, decorate any of
the functions in `Flatdoc.transformer`.

### Transformer.mangle()

Takes a given HTML `$content` and improves the markup of it by executing
the transformations.

> See: [Transformer](#transformer)

### Transformer.addIDs()

Adds IDs to headings.

### Transformer.getMenu()

Returns menu data for a given HTML.

```js
menu = Flatdoc.transformer.getMenu($content);
menu == {
  level: 0,
  items: [{
    section: "Getting started",
    level: 1,
    items: [...]}, ...]}
```



### Transformer.buttonize()

Changes "button >" text to buttons.

### Transformer.smartquotes()

Applies smart quotes to a given element.
It leaves `code` and `pre` blocks alone.

Highlighters
------------

Syntax highlighters.

You may add or change more highlighters via the `Flatdoc.highlighters`
object.

```js
Flatdoc.highlighters.js = function(code) {
};
```

Each of these functions

### Highlighters.js

JavaScript syntax highlighter.

Thanks @visionmedia!

MenuView
--------

Menu view. Renders menus

Runner
------

A runner module that fetches via a `fetcher` function.

```js
var runner = new Flatdoc.runner({
  fetcher: Flatdoc.url('readme.txt')
});
runner.run();
```

The following options are available:

 - `fetcher` - a function that takes a callback as an argument and
   executes that callback when data is returned.

See: [Flatdoc.run()]

### Runner#highlight()

Syntax highlighting.

You may define a custom highlight function such as `highlight` from
the highlight.js library.

```js
Flatdoc.run({
  highlight: function (code, value) {
    return hljs.highlight(lang, code).value;
  },
  ...
});
```



### Runner#run()

Loads the Markdown document (via the fetcher), parses it, and applies it
to the elements.

### Runner#applyData()

Applies given doc data `data` to elements in object `elements`.


[Flatdoc]: #flatdoc
[Flatdoc.run()]: #flatdoc-run
[Flatdoc.file()]: #flatdoc-file
[Flatdoc.github()]: #flatdoc-github
[Flatdoc.bitbucket()]: #flatdoc-bitbucket
[Parser]: #parser
[Parser.parse()]: #parser-parse
[Transformer]: #transformer
[Transformer.mangle()]: #transformer-mangle
[Transformer.addIDs()]: #transformer-addids
[Transformer.getMenu()]: #transformer-getmenu
[Transformer.buttonize()]: #transformer-buttonize
[Transformer.smartquotes()]: #transformer-smartquotes
[Highlighters]: #highlighters
[Highlighters.js]: #highlighters-js
[MenuView]: #menuview
[Runner]: #runner
[Runner#highlight()]: #runner-highlight
[Runner#run()]: #runner-run
[Runner#applyData()]: #runner-applydata



