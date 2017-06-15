# API reference

## Properties

Property      | Type      | Default           | Description                                                   
------------- | --------- | ----------------- | -----------     
`path`        | `String`  | `undefined`       | Path to the data for this link on Simpla's API                                                          
`href`        | `String`  | `''`              | Href of the link
`placeholder` | `String`  | `Enter a URL...`  | Placeholder for the link prompt
`editable`    | `Boolean` | `false`           | Whether the link is editable                                 
`active`      | `Boolean` | `false`           | Whether the link prompt is open
`loaded`      | `Boolean` | `false`           | Whether the link href has loaded

Properties can be set either directly with JavaScript or as attributes on the element

```html
<simpla-link path="/link" editable></simpla-link>

<script>
  document.querySelector('simpla-link').editable = true;
</script>
```

## Schema

**Type:** `'Link'`

Data   | Type      | Description                                           
------ | --------- | -----------                                           
`href` | `String`  | Href of the link

```json
{
  "path": "/link/path",
  "type": "Link",
  "data": {
    "href": "https://www.simpla.io"
  },
  "createdAt": "2017-04-16T09:58:56.276Z",
  "updatedAt": "2017-05-09T09:25:36.835Z"
}
```

## Events

Event              | Description                                    
------------------ | -----------                                    
`href-changed`     | Fired whenever the `src` property changes      
`editable-changed` | Fired whenever the `editable` property changes 
`active-changed`   | Fired whenever the `active` property changes   
`loaded-changed`   | Fired whenever the `loaded` property changes   