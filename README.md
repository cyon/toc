# Table of Contents jQuery Plugin - jquery.toc

A minimal, tiny jQuery plugin that will generate a table of contents, drawing from headings on the
page.

The generated TOCs are semantic, nested lists (`ul` or `ol`) with hash-link anchors to the headings.

## Usage

The toc plugin can be used by downloading jquery.toc.js and including it in your html file.

Include jQuery (>= 1.6) and jquery.toc.js/jquery.toc.min.js on your page. The plugin can then be
used either via HTML5 data attributes, or via the programmatic API. See below for the available
options.

### Via data attributes

Minimal example:

    <div data-toc></div>

With options:

    <div data-toc="div.container" data-toc-headings="h2,h3,h4"></div>

### Via the JavaScript programmatic API

Minimal example:

    <div id="toc"></div>
    ...
    <script type="text/javascript">
        $("#toc").toc();
    </script>

With options:

    <div id="toc"></div>
    ...
    <script type="text/javascript">
        $("#toc").toc({content: "div.container", headings: "h2,h3,h4"});
    </script>

### Options

    <div data-toc="content" data-toc-headings="headings"></div>

    $(...).toc({content: "body", headings: "h1,h2,h3"});

The plugin has the following options:

* `content` is a selector where the plugin will look for headings to build up the TOC. The default
  value is `"body"`.
* `headings` is a string with a comma-separated list of selectors to be used as headings, in the
  order which defines their relative hierarchy level. The default value of `"h1,h2,h3"` will select
  all `h1`, `h2`, and `h3` elements to build the TOC, with `h1` being a level 1, `h2` a level 2, and
  so on. You can use any valid list of jQuery selectors; for example, if you just want `h1` tags
  with a specific class, and no `h3` tags, you could use `"h1.title,h2"` for this parameter.
* `minHeadings` is a number of headings that have to be in the document before
  the table of contents is displayed. All headings of the type specified in the `headings` option are counted.
* `title` is a simple string or html object that is being inserted right before the actual table of 
  contents.
* `minHeight` is the minimum height (in pixels) which the content has to have before
  a table of contents will be displayed. If a `minHeadings` has also been specified 
  then it will only be displayed if both conditions are fulfilled.

In addition, the plugin will create nested lists of the same type (`ul` or `ol`) as the element that
it is called on.

### Automatic ID generation

The plugin generates hash-links to the headings on the page, to allow users to jump to the heading
by clicking in the generated table of contents. This feature requires that the headings have IDs
assigned; if they do not, the plugin will generate and assign IDs automatically.

The generated IDs are based on the text inside the headings, and uses two simple rules:

* The ID must begin with a letter; so any non-letter (`[^A-Za-z]`) characters are discarded from the
  beginning of the string.
* For the rest of the ID, only letters and numbers are used from the heading text; all other
  characters (`[^A-Za-z0-9]`) are converted to underscores.

For example, a heading like `<h2>Heading 2.1</h2>` will get the ID `Heading_2_1`.

## Alternatives

If you're looking for a jQuery plugin that does more than just generate a minimal table of contents,
the project wiki [lists some more plugins](https://github.com/ndabas/toc/wiki/Alternatives).

## License

Licensed under the [Apache License, version 2.0](http://www.apache.org/licenses/LICENSE-2.0).

## Credits

Created by [Nikhil Dabas](http://www.nikhildabas.com/).