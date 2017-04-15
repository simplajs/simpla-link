# Simpla Link
![Version][bower-badge] [![Build status][travis-badge]][travis-url] ![Size][size-badge] [![Published][webcomponents-badge]][webcomponents-url] [![Simpla slack group][slack-badge]][slack-url]

`simpla-link` is an editable link built on the [Simpla](https://www.simpla.io) content system. You can wrap any other HTML element with it just as you would a regular `<a>` link.

<!---
```
<custom-element-demo>
  <template>
    <script src="../webcomponentsjs/webcomponents-lite.js"></script>
    <link rel="import" href="simpla-link.html">

    <script src="https://unpkg.com/simpla@^2.0.0"></script>
    <script>
      Simpla.init('dummy');
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
<simpla-link path="/my-link">
  Click me!
</simpla-link>

<script>
  Simpla.editable(true);
</script>
```

## Installation and setup

Install simpla-link with Bower (Yarn support coming soon)

```sh
$ bower install simpla-link --save
```

Then include the Simpla library and setup a project (read more about [setting up Simpla](https://www.simpla.io/docs/guides/get-started))

```html
<script src="https://unpkg.com/simpla@^2.0.0"></script>
<script>
  // TODO: replace 'project-id' with your project ID
  Simpla.init('project-id')
</script>
```

Import simpla-link into the `<head>` of your document

```html
<link rel="import" href="/bower_components/simpla-link/simpla-link.html">
```

And wrap whatever content you want to create a link for with a `<simpla-link>` element. You must also specify a content path (where the link's data will be stored on Simpla's API) in a `path` attribute.

```html
<simpla-link path="/my-link">
  Next page >
</simpla-link>
```

> Read more about [Simpla's content model](https://www.simpla.io/docs/guides/content-model)

Simpla link plays nicely with other Simpla elements, so you can linkify editable content

```html
<!-- Robust button -->
<simpla-link path="/button">
  <simpla-text plaintext path="/button/text"></simpla-text> 
</simpla-link>

<!-- Thumbnail prevew image -->
<simpla-link path="/preview">
  <img is="simpla-img" path="/preview/thumbnail">
</simpla-link>
```

### Polyfills for cross-browser support

`simpla-link` relies on emerging standards, for full cross-browser support make sure you include the [Web Components Lite](https://github.com/webcomponents/webcomponentsjs) polyfill.

```html
<script src="https://unpkg.com/webcomponents.js@^0.7.24/webcomponents-lite.min.js"></script>
```

## Editing content

Edit a simpla-link by entering edit mode with Simpla (which makes all Simpla elements on a page editable) or setting the `editable` property directly on an element.

```js
// Enter edit mode
Simpla.editable(true);
```

```html
<!-- Make only this image editable -->
<simpla-link path="/my-link" editable></simpla-link>
```

Entering edit mode with Simpla is the recommended way to edit links. It ensures all elements on a page remain in sync and updates Simpla's public `'editable'` state, which other elements may rely on.

> If you include the [simpla-admin](https://webcomponents.org/element/SimplaElements/simpla-admin) component on your page, you can also enter edit mode by adding #edit to the end of your URL

## Saving content

Save a `simpla-link` by calling Simpla's `save` method, which will save all modified content on the page. It returns a promise.

```js
// Save all modified Simpla content
Simpla.save();
```

Note you must be authenticated before saving content - either login with `simpla-admin` or the `Simpla.login()` method.

> If you have included the [simpla-admin](http://webcomponents.org/element/SimplaElements/simpla-admin) component on your site, you can save content by entering edit mode and just pressing the 'save' button.

## Initializing with static content

You can set the `href` of simpla-link just like you would with a regular `<a>`. If content for the link's `path` exists on Simpla's API, the locally set `href` will be overwritten

```html
<simpla-link href="https://google.com" path="/my-link"></simpla-link>
```

Initializing with static content is useful for converting existing links and buttons to Simpla links, or bootstrapping a project with predefined content. By setting `href` and then calling `Simpla.save()` you can easily set content directly to Simpla.

## Custom placeholders

You can set a custom placeholder for the link prompt with the `placeholder` attribute

```html
<simpla-link path="/next-page" placeholder="URL for next page">
  Next page >
</simpla-link>
```


## API reference

### Properties

Property      | Type    | Default           | Description                                                   
------------- | ------- | ----------------- | -----------                                                   
`href`        | String  | `''`              | Href of the link
`path`        | String  | `undefined`       | Path to the data for this link on Simpla's API            
`placeholder` | String  | `Enter a URL...`  | Placeholder for the link prompt
`editable`    | Boolean | `false`           | Whether the link is editable                                 
`active`      | Boolean | `false`           | Whether the link prompt is open

Properties can be set either directly with JavaScript or as attributes on the element

```html
<!-- Set property as attribute -->
<simpla-link path="/my-link" editable></simpla-link>
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

## Contributing

If you find any issues with simpla-link please report them! If you'd like to see a new feature in supported file an issue or let us know in Simpla's public [Slack group](https://slack.simpla.io). We also happily accept PRs. 

***

MIT © Simpla <friends@simpla.io>

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

