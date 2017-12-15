# Simpla Link
[![Build status][travis-badge]][travis-url] ![Size][size-badge] ![Version][bower-badge] [![Published][webcomponents-badge]][webcomponents-url]

Simpla-link is an editable anchor that you can update inline on your page. You can wrap any other HTML element with it just as you would a regular `<a>`. It's built on the [Simpla][simpla] content system. 

<!---
```
<custom-element-demo>
  <template>
    <script src="../webcomponentsjs/webcomponents-lite.js"></script>
    <link rel="import" href="simpla-link.html">

    <script src="https://unpkg.com/simpla@^2.0.0"></script>
    <script>
      Simpla.init('local');
      Simpla.editable(true);
    </script>

    <style>
      body {
        height: 5rem;
      }
      simpla-link {
        margin: 2rem 0 0 2rem;
      }
    </style>
    <next-code-block></next-code-block>
  </template>
</custom-element-demo>
```
-->
```html
<simpla-link path="/link">
  Next page >
</simpla-link>
```

### Contents

- [Installation and setup](#installation-and-setup)
- [Editing content](#editing-content)
- [Saving content](#saving-content)
- [Initializing with static content](#initializing-with-static-content)
- [Custom placeholders](#custom-placeholders)
- [Readonly](#readonly)
- [Contributing](#contributing)

### Resources

- [API reference][api]
- [Demo][demo]
- [License][license]

## Installation and setup

Install simpla-link with Bower (Yarn support coming soon)

```sh
$ bower i simpla-link --save
```

[Setup Simpla][simpla-setup] on your page, then import simpla-link into your `<head>`

```html
<link rel="import" href="/bower_components/simpla-link/simpla-link.html">
```

Wrap the content you want to link with `<simpla-link>`. Give each link a unique `path`, where it will store its data in your project

```html
<simpla-link path="/link">
  Next page >
</simpla-link>
```

Simpla link plays nicely with other Simpla elements, so you can linkify editable content

```html
<simpla-link path="/button">
  <simpla-text path="/button/label" plaintext></simpla-text> 
</simpla-link>
```

## Editing content

Edit a simpla-link by entering edit mode with Simpla (which makes all Simpla elements on a page editable) or setting the `editable` property directly on an element.

```js
// Enter edit mode
Simpla.editable(true);
```

```html
<!-- Make only this image editable -->
<simpla-link path="/link" editable></simpla-link>
```

Entering edit mode with Simpla is the recommended way to edit links. It ensures all elements on a page remain in sync and updates Simpla's public `editable` state, which other elements may rely on.

## Saving content

Save a simpla-link by calling Simpla's `save()` method, which saves all modified content on the page. It returns a promise.

```js
// Save all modified Simpla content
Simpla.save();
```

> You must be authenticated with Simpla before saving content

## Initializing with static content

You can set the `href` of simpla-link just like you would with a regular `<a>`. If content for the link's path exists on Simpla's API, the locally set `href` will be overwritten

```html
<simpla-link href="https://google.com" path="/link">
  Visit google
</simpla-link>
```

Initializing with static content is useful for converting existing links and buttons to Simpla links, or bootstrapping a project with predefined content. By setting `href` and then calling `Simpla.save()` you can easily set content directly to Simpla.

> Since static content is overwritten by remote data, you should not have a href set in production

## Custom placeholders

You can set a custom placeholder for the link input prompt with a `placeholder` attribute

```html
<simpla-link path="/link" placeholder="URL for next page">
  Next page >
</simpla-link>
```

## Readonly

Simpla-link has a `readonly` property that stops it from becoming editable, even if Simpla is in edit mode or you try to set `editable` on the element directly. This is useful for using simpla-link to purely consume and display content from Simpla's API.

```html
<simpla-link path="/link" readonly>
  Next page >
</simpla-link>
```


## Contributing

If you find any issues with simpla-link please report them! If you'd like to see a new feature in supported file an issue. We also happily accept PRs. 

***

MIT © [Simpla][simpla]

[simpla]: https://www.simpla.io
[simpla-setup]: https://www.simpla.io/docs/guides/get-started

[api]: https://www.webcomponents.org/element/simplaio/simpla-link/page/API.md
[demo]: https://www.webcomponents.org/element/simplaio/simpla-link/demo/demo/index.html
[license]: https://github.com/simplaio/simpla-link/blob/master/LICENSE

[bower-badge]: https://img.shields.io/bower/v/simpla-link.svg
[bowerlicense-badge]: https://img.shields.io/bower/l/simpla-link.svg
[travis-badge]: https://img.shields.io/travis/simplaio/simpla-link.svg
[travis-url]: https://travis-ci.org/simplaio/simpla-link
[size-badge]: https://badges.herokuapp.com/size/github/simplaio/simpla-link/master/simpla-link.html?gzip=true
[webcomponents-badge]: https://img.shields.io/badge/webcomponents.org-published-blue.svg
[webcomponents-url]: https://www.webcomponents.org/element/simplaio/simpla-link

