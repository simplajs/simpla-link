# API reference

## Properties

Property      | Type      | Default           | Description                                                   
------------- | --------- | ----------------- | -----------     
`path`        | `String`  | `undefined`       | Path to the data for this link on Simpla's API                                                          
`href`        | `String`  | `''`              | Href of the link
`placeholder` | `String`  | `Enter a URL...`  | Placeholder for the link prompt
`editable`    | `Boolean` | `false`           | Whether the link is editable                                 
`readonly`    | `Boolean` | `false`           | Whether the link is able to become editable                                 
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

Event              | Properties       | Description                                    
------------------ | ---------------- | -----------                                    
`href-changed`     | `value{String}`  | Fired when `href` property changes      
`editable-changed` | `value{Boolean}` | Fired when `editable` property changes 
`active-changed`   | `value{Boolean}` | Fired when `active` property changes   
`loaded-changed`   | `value{Boolean}` | Fired when `loaded` property changes   