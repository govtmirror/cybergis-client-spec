Proto Specification, Version 1.0
================

## Description

The layer prototype file (or protolayer file or proto file) links layer identifiers with (1) metadata and (2) strategy/protocol information for loading layers.

## Specifications

The layer prototype file includes a map of layer identifiers to layer prototypes.  Information is specified at the layer level.  No information is specified at the application level.  A future revision will further abstract layer identifiers with namespaces.

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
	  "osm"
	  {
	    "name":"OSM",
	    "classification":"Unclassififed",
	    "description":"OpenStreetMap is a free, editable map of the whole world.",
	    "type":"OSM"
	  },
	  "incidents":
	  {
	    "name":"Incidents",
	    "classification":"Unclassififed",
	    "description":"Incidents derived from ...",
	    "type":"GeoJSON",
	    "projection":"EPSG:4326",
	    "minZoom":0,
	    "maxZoom":8,
	    "url":"data/incidents.geojson",
	    "select":true
	  }
	}
}
```


### Properties

**General**: [Name](#name), [Classification](#classification), [Description](#description-1), [Type](#type), [Projection](#projection), [Minimum Zoom](#minimum-zoom-minzoom), [Maximum Zoom](#maximum-zoom-maxzoom), [URL](#url),  [Select](#select)

**MapBox**: [Layer Name](#layer-name)

**SharePoint**: [List](#list), [Columns](#columns)

**Just-in-Time**: [Just-in-Time](#just-in-time)

#### Name

The name property is a string.  It specifies the name of a layer.  The name is used for the data dialog and other ways on the page.

Example

`"name":"OSM"`

#### Classification

The classification property is a string.  It specifies the classification marking of the layer.  It does not represent the classification of the layer name or metadata.  The property represents the highest classification level of the data contained within the layer.

Examples

* `"classification":"Unclassified"`
* `"classification":"Unclassified//SBU"`
* `"classification":"Unclassified//FOUO"`

#### Description

The description property is a string.  It specifies the description of a layer.  The description is used for the data dialog and other ways on the page.

Example

`"description":"OpenStreetMap is a free, editable map of the whole world."`

#### Type

The type property is a string.  It specifies the type of a layer.  The type can be a variety of options.  The options are aliased and case insensitive.  For example, you can specify a MapBox Layer with "Openlayers.Layer.Mapbox" or "MapBox".

**Options**

| Type | Alias 1 | Alias 2 | Alias 3 | Alias 4 |
| ---- | ----    | ----    | ----    | ----    |
| MapBox | MapBox | Openlayers.Layer.Mapbox  | - | - |
| OSM | OSM | OpenLayers.Layer.OSM  | OpenStreetMap | - |
| WMS | WMS | OpenLayers.Layer.WMS  | - | - |
| ArcGIS | ArcGIS | OpenLayers.Layer.ArcGIS93Rest  | - | - |
| GeoJSON | GeoJSON | OpenLayers.Layer.GeoJSON  | - | - |
| KML | KML | OpenLayers.Layer.KML  | - | - |
| TSV | TSV | OpenLayers.Layer.TSV  | - | - |
| Placeholder | Placeholder | OpenLayers.Layer.Placeholder  | - | - |
| SharePoint | SharePoint | OpenLayers.Layer.SOAP  | SOAP | - |
| Vector | Vector | OpenLayers.Layer.Vector  | - | - |
| TimeVector | TimeVector | OpenLayers.Layer.TimeVector  | - | - |

Examples

`"type":"OSM"`

#### Projection

The projection property is a string.  It specifies the EPSG code of the projection of the layer.  It should almost always be set to `"EPSG:326"` or `"EPSG:900913"`.

Examples

- `"projection":"EPSG:4326"`
- `"projection":"EPSG:900913"`

#### Minimum Zoom (minZoom)

The minZoom property is an integer.  It specifies the minimum zoom level for the layer.  It is most frequently 0.

**Fallback**: [Map Minimum Zoom](https://github.com/state-hiu/cybergis-client-spec/blob/master/1.0/cybergis-client-spec-properties-1.0.md#minimum-zoom-minzoom)

**Example**

`"minZoom":0`

#### Maximum Zoom (maxZoom)

The maxZoom property is an integer.  It specifies the maximum zoom level for the layer.  It is most frequently 18.

**Fallback**: [Map Maximum Zoom](https://github.com/state-hiu/cybergis-client-spec/blob/master/1.0/cybergis-client-spec-properties-1.0.md#maximum-zoom-maxzoom)

**Example**


`"maxZoom":18`

#### URL

The url property is a string.  It specifies where to load the data for the layer.  The url is used diferently depending on the layer type, protocol, and strategy.  It should be intuitive.  Frequently it is not required when the server is implicit from the type, such as for OpenStreetMap, MapBox, etc.

Example

`"url":"data/incident.geojson"`

#### Select

The select property is a boolean.  It specified whether the layer is selectable.  The CyberGIS client application determines the best selection interaction depending on which feature layer are selectable.  For example, if only one feature layer is selectable, then you can bypass a lot of selection code.

Example

`"select":true`

#### Layer Name

The layer name property is a string.  It specifies MapBox layers using a comma-separted list of layers.  The layers are composited into tiles.

**Example**

```JSON
"layername": "mapbox.world-blank-light,hiu.lsib-dark"
```

#### List

The list property is a string.  It specifies the SharePoint List to load for the layer.  The OpenLayers.Format.SOAP class that reads in the data parses geometry using the following cascading rules.

**Cascading**

OpenLayers.Format.SOAP checks (1) first for a comma separated latlon pair, (2) then for a comma separated lonlat pair, (3) then for latitude and longitude as separate columns, (4) then for a comma separated yx pair, (5) then for a comma separated xy pair, and (4) then for y and x and separate columns

| Order | Level | Column 1 | Column 2 | Column 3 | Column 4 |  Column 5 |  Column 6 |
| ---- | ---- | ---- | ---- | ---- |  ---- |   ---- |   ---- |
| 1 | LatLon | latlon | latlong | lat__lon | lat long |
| 2 | LonLat | lonlat | longlat | long_lat | long lat |
| 3 | Lat | lat | latitude | lat_dd | latitude_dd |
| 3 | Lon | lon | long | longitude | lon_dd | long_dd | longitude_dd |
| 4 | YX | yx | y_x | y x |
| 5 | XY | xy | x_y | x y |
| 6 | Y | y |
| 6 | X | x |

**Example**

```JSON
"list": "incidents"
```

#### Columns

The columns property is an array of strings.  It specifies the columns to load from a SharePoint List.  If columns is not specified, then the results of the SOAP call are not consistent between SharePoint versions.  It is highly advised to set this property.

**Example**

```JSON
"columns":
[
	"Title","Description","Date Published","Date Entered","Date Incident",
	"Country","State","City","SubCity","Latitude","Longitude",
	"Fatalities (Combatants)","Fatalities (Non-Combatants)"
]
```

### Related Specifications

See the related specifications for: [Proto](https://github.com/state-hiu/cybergis-client-spec/blob/master/1.0/cybergis-client-spec-proto-1.0.md), [Carto](https://github.com/state-hiu/cybergis-client-spec/blob/master/1.0/cybergis-client-spec-carto-1.0.md), [Glossaries](https://github.com/state-hiu/cybergis-client-spec/blob/master/1.0/cybergis-client-spec-glossary-1.0.md), and [Bookmarks](https://github.com/state-hiu/cybergis-client-spec/blob/master/1.0/cybergis-client-spec-bookmarks-1.0.md).
## Examples

- [Properties, Version 1.0](https://github.com/state-hiu/cybergis-client-spec/blob/master/1.0/cybergis-client-example-properties-1.0.json)

## Contributing

HIU is currently not accepting pull requests for this repository.

## License
This project constitutes a work of the United States Government and is not subject to domestic copyright protection under 17 USC § 105.
