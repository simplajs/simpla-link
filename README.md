# Simpla Link
[![Build status][travis-badge]][travis-url] ![Size][size-badge] ![Version][bower-badge] [![Published][webcomponents-badge]][webcomponents-url] [![Simpla slack group][slack-badge]][slack-url]

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

## Installation and setup

Install simpla-link with Bower (Yarn support coming soon)

```sh
$ bower i simpla-link --save
```

[Setup Simpla][setup-simpla] on your page, then import simpla-link into your `<head>`

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
<simpla-link href="https://google.com" path="/link"></simpla-link>
```

Initializing with static content is useful for converting existing links and buttons to Simpla links, or bootstrapping a project with predefined content. By setting `href` and then calling `Simpla.save()` you can easily set content directly to Simpla.

> Since static content is overwritten by remote data, you should not have a href set in production

## Custom placeholders

You can set a custom placeholder for the link input prompt with a `placeholder` attribute

```html
<simpla-link path="/next-page" placeholder="URL for next page">
  Next page >
</simpla-link>
```

## API reference

### Properties

Property      | Type    | Default           | Description                                                   
------------- | ------- | ----------------- | -----------     
`path`        | String  | `undefined`       | Path to the data for this link on Simpla's API                                                          
`href`        | String  | `''`              | Href of the link
`placeholder` | String  | `Enter a URL...`  | Placeholder for the link prompt
`editable`    | Boolean | `false`           | Whether the link is editable                                 
`active`      | Boolean | `false`           | Whether the link prompt is open
`loaded`      | Boolean | `false`           | Whether the link href has loaded

Properties can be set either directly with JavaScript or as attributes on the element

```html
<!-- Set property as attribute -->
<simpla-link path="/link" editable></simpla-link>
```

```js
// Set property with JavaScript
document.querySelector('simpla-link').editable = true;
```

### Events

Event              | Description                                    
------------------ | -----------                                    
`href-changed`     | Fired whenever the `src` property changes      
`editable-changed` | Fired whenever the `editable` property changes 
`active-changed`   | Fired whenever the `active` property changes   
`loaded-changed`   | Fired whenever the `loaded` property changes   

## Contributing

If you find any issues with simpla-link please report them! If you'd like to see a new feature in supported file an issue or let us know in Simpla's public [Slack group](https://slack.simpla.io). We also happily accept PRs. 

***

MIT © [Simpla][simpla]

[simpla]: https://www.simpla.io
[setup-simpla]: https://www.simpla.io/docs/guides/get-started
[bower-badge]: https://img.shields.io/bower/v/simpla-link.svg
[bowerlicense-badge]: https://img.shields.io/bower/l/simpla-link.svg
[travis-badge]: https://img.shields.io/travis/SimplaElements/simpla-link.svg
[travis-url]: https://travis-ci.org/SimplaElements/simpla-link
[bowerdeps-badge]: https://img.shields.io/gemnasium/SimplaElements/simpla-link.svg
[bowerdeps-url]: https://gemnasium.com/bower/simpla-link
[size-badge]: https://badges.herokuapp.com/size/github/SimplaElements/simpla-link/master/simpla-link.html?gzip=true
[webcomponents-badge]: https://img.shields.io/badge/webcomponents.org-published-blue.svg
[webcomponents-url]: https://www.webcomponents.org/element/SimplaElements/simpla-link
[slack-badge]: http://slack.simpla.io/badge.svg
[slack-url]: https://slack.simpla.io

