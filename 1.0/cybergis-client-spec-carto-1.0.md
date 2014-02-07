Carto Specification, Version 1.0
================

| Specifications: | [Client](https://github.com/state-hiu/cybergis-client-spec/blob/master/1.0/README.md) | [Properties](https://github.com/state-hiu/cybergis-client-spec/blob/master/1.0/cybergis-client-spec-properties-1.0.md) | [Proto](https://github.com/state-hiu/cybergis-client-spec/blob/master/1.0/cybergis-client-spec-proto-1.0.md) | [Carto](https://github.com/state-hiu/cybergis-client-spec/blob/master/1.0/cybergis-client-spec-carto-1.0.md) | [JIT](https://github.com/state-hiu/cybergis-client-spec/blob/master/1.0/cybergis-client-spec-jit-1.0.md) | [Glossaries](https://github.com/state-hiu/cybergis-client-spec/blob/master/1.0/cybergis-client-spec-glossary-1.0.md) | [Bookmarks](https://github.com/state-hiu/cybergis-client-spec/blob/master/1.0/cybergis-client-spec-bookmarks-1.0.md) |
| ---- |  ---- |  ---- |  ---- |  ---- |  ---- |   ---- |   ---- |

## Description

The cartography file (or carto file) describes the cartography for each layer. Additionally, the carto file describes the visual representation of a layer within a chart and box. Generally speaking, any visualization of a layer is described in the carto file.

## Specifications

The layer cartography file includes a map of layer identifiers to layer cartography.  Information is specified at the layer level.  No information is specified at the application level.  A future revision will further abstract layer identifiers with namespaces.

### Blank Configuration

```JSON
{
	"layers":
	{
	
	}
}
```

### Simple Configuration

```JSON
{
	"layers":
	{
    "pcodes_admin1":
    {
      "style":
      {
        "intents":
        {
          "default":
          {
            "templates":"core:pcodes, core:label_pcode",
            "properties":
            {
              "label": "",
              "strokeOpacity": 0,
              "fillOpacity": 0
            }
          },
          "select":
          {
            "templates":"core:pcodes",
            "properties":
            {
              "label": "${label}",
              "strokeWidth": 4,
              "strokeColor": "blue",
              "fillColor": "blue",
              "fillOpacity": 0.2
            }
          },
          "close":
          {
            "templates":"core:close"
          }
        }
      },
      "classifications":
      [
        {
          "type": "single",
          "field": "hover",
          "value": "on",
          "style":
          {
              "label": "${label}",
              "strokeWidth": 4,
              "strokeColor": "green",
              "fillColor": "green",
              "fillOpacity": 0.2
          }
        }
      ]
	  },
	  "incidents":
	  {
      "style":{...},
      "legend":{"label":"Incidents","symbol":"circle","radius":10},
      "popup":{...}
	  }
	}
}
```


### Properties

## Examples

## Contributing

HIU is currently not accepting pull requests for this repository.

## License
This project constitutes a work of the United States Government and is not subject to domestic copyright protection under 17 USC § 105.
