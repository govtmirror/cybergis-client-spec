Properties Specification, Version 1.0
================

| Specifications: | [Client](https://github.com/state-hiu/cybergis-client-spec/blob/master/1.0/README.md) | [Properties](https://github.com/state-hiu/cybergis-client-spec/blob/master/1.0/cybergis-client-spec-properties-1.0.md) | [Proto](https://github.com/state-hiu/cybergis-client-spec/blob/master/1.0/cybergis-client-spec-proto-1.0.md) | [Carto](https://github.com/state-hiu/cybergis-client-spec/blob/master/1.0/cybergis-client-spec-carto-1.0.md) | [JIT](https://github.com/state-hiu/cybergis-client-spec/blob/master/1.0/cybergis-client-spec-jit-1.0.md) | [Glossaries](https://github.com/state-hiu/cybergis-client-spec/blob/master/1.0/cybergis-client-spec-glossary-1.0.md) | [Bookmarks](https://github.com/state-hiu/cybergis-client-spec/blob/master/1.0/cybergis-client-spec-bookmarks-1.0.md) |
| ---- |  ---- |  ---- |  ---- |  ---- |  ---- |   ---- |   ---- |

## Description

The properties file is used to configue which layers and controls to show on the map. The properties file also contains pointers to shared external resources that are not specific to individual layers, such as P-Codes, Glossaries, Bookmarks, etc.


## Specifications

### Blank Configuration

```JSON
{
	"element":"",
	"name": "",
	"title":"",
	"domain":"",
	"context":"",
	"pages":
	{
		"main":"",
		"thumbnail":"",
		"embed":""
	},
	"classification":"",
	"projection":"",
	"zoom":7,
	"minZoom":0,
	"maxZoom":18,
	"resolutions":[],
	"controls":{},	
	"apps":[],
	"wikis":[],
	"datasources":[],
	"bookmarks":{},
	"glossaries":[],
	"hashmaps":{},
	"pcodes":[],
	
	"baseLayers":[],
	"featureLayers":[],
	"renderLayers":[],
	"searchLayers":[],
	"legendLayers":[]
}
```
### Properties

**General**: [Element](#element), [Name](#name), [Title](#title), [Domain](#context), [Context](#context), [Pages](#pages), [Classification](#classification), [Projection](#projection), [Zoom](#zoom), [Minimum Zoom](#minimum-zoom-minzoom), [Maximum Zoom](#maximum-zoom-maxzoom), [Resolutions](#resolutions), [Controls](#controls), [Applications](#applications-apps), [Wikis](#wikis), [Data Sources](#data-sources), [Bookmarks](#bookmarks),[Glossaries](#glossaries), [HashMaps](#hashmaps),  [P-Codes](#p-codes-pcodes),

**Layers**: [Base Layers](#base-layers),  [Feature Layers](#feature-layers), [Render Layers](#render-layers), [Search Layers](#search-layers),  [Legend Layers](#legend-layers),  [Box Layers](#box-layers),  [Chart Layers](#chart-layers)

#### Element

The element property is a string.  It specifies the DIV that will contain the OpenLayers map.

Example

`"element":"map"`

#### Name

The name property is a string.  It specifies the name of the CyberGIS client application.  The name is used for the page headers, about dialog, and other ways on the page.

**Cascading**

| Order | Level | Property 1 | Property 2 | Property 3 |  Property 4 |
| ---- | ---- | ---- | ---- | ---- | ---- |
| 1 | Query String | n | name |
| 2 | DOM |
| 3 | File | name |

**Example**

`"name":"Demo"`

#### Title

The title property is a string.  It specifies the title of the CyberGIS client application.  The title is used for the page title (read: browser history).

Example

`"title":"Demo - Organization"`

#### Domain

The domain property is a string.  It specifies the domain that the application is on.  Actually, the string should include the protocol + domain (http + example.com).  It should not have a trailing slash.

Example

`"domain":"http://example.com"`

#### Context

The context property is a string.  It specifies the context path that the application is on.  It should have a preceding slash.

Example

`"context":"/cybergis/apps"`

#### Pages

The pages property is an object that contains the page names for the main page, thumbnail page, and embed page.

Example

```JSON
"pages":
{
	"main":"hello-world.html",
	"thumbnail":"hello-world-thumbnail.html",
	"embed":"hello-world-embed.html"
}
```

#### Classification

The classification property is a string.  It specifies the classification marking of the application.  It does not represent the classification of the application name or metadata.  The property represents the highest classification level of the data contained in the application.

Examples

* `"classification":"Unclassified"`
* `"classification":"Unclassified//SBU"`
* `"classification":"Unclassified//FOUO"`

#### Projection

The projection property is a string.  It specifies the EPSG code of the projection of the map.  It should almost always be set to `"EPSG:900913"`.

**Cascading**

| Order | Level | Property 1 | Property 2 | Property 3 |  Property 4 |
| ---- | ---- | ---- | ---- | ---- | ---- |
| 1 | DOM | mapProjection |
| 2 | File | projection |

**Example**

`"projection":"EPSG:900913"`

#### Zoom

The zoom property is an integer.  It specifies the default zoom level of the application.

**Cascading**

| Order | Level | Property 1 | Property 2 | Property 3 | Property 4 |
| ---- | ---- | ---- | ---- | ---- |  ---- |
| 1 | Query String | q | query | z | zoom |
| 2 | DOM | mapZoom |
| 3 | File | name |
| 4 | Base Layer | minZoom |

**Fallback**: 3

**Example**

`"zoom":7`

#### Minimum Zoom (minZoom)

The minZoom property is an integer.  It specifies the minimum zoom level for the application.  It is most frequently 0.

**Fallback**: 0

**Example**

`"minZoom":0`

#### Maximum Zoom (maxZoom)

The maxZoom property is an integer.  It specifies the maximum zoom level for the application.  It is most frequently 18.

**Fallback**: Length of [Resolutions](#resolutions) - 1

**Example**

`"maxZoom":18`

#### Resolutions

The resolutions property is an array of floats.  It specifies the resolutions for each zoom level.  This array almost always contains the resolutions for each level of an EPSG:900913 TMS service.

**Example**

`"resolutions":[156543.03390625,78271.516953125,39135.7584765625,19567.87923828125,9783.939619140625,4891.9698095703125,2445.9849047851562,1222.9924523925781,611.4962261962891,305.74811309814453,152.87405654907226,76.43702827453613,38.218514137268066,19.109257068634033,9.554628534317017,4.777314267158508,2.388657133579254,1.194328566789627,0.5971642833948135]`

#### Controls

The controls property is an object that includes the custom options that will get passed to the map controls, such as search, select, and disclaimer.

Example

```JSON
"controls":
{
	"search":{"mode":"flexible","acLabel":"name_search"},
	"select":{"stopDown":false},
	"disclaimer":
	{
		"leftText":"Names and boundary representation are not necessarily authoritative.",
		"middleText":"Names and boundary representation are not necessarily authoritative.<br>Basemap: Copyright <a href=\"http://openstreetmap.org/\">OpenStreetMap</a> contributors",
		"rightText":"Basemap: Copyright <a href=\"http://openstreetmap.org/\">OpenStreetMap</a> contributors"
	}
}
```

#### Applications (apps)

The apps property is an object that includes descriptions of other web mapping applications, including cybergis client applications.  By specifying here you can jump between applications seamlessly.  For example, in an conflict incidents application, you click on an incident, open a popup, and click on a link within the popup to jump to same location in OpenStreetMap.

Example

```JSON
"apps":
[
	{"name":"hello_world_2","label":"Hello World 2","classification":"Unclassified","description":"","url":{"page":"/cybergis/apps/hello-world-2.html","querystring":"z={z}&lon={x}&lat={y}","precision":4}},
		
	{"name":"google","label":"Google Maps","classification":"Unclassified","description":"","url":{"page":"https://maps.google.com/maps?q=","delimiter":",","order":"y,x"}},
	{"name":"osm","label":"OpenStreetMap","classification":"Unclassified","description":"","url":{"page":"http://www.openstreetmap.org/#map=","delimiter":"/","order":"z,y,x","precision":4}}
]
```

#### Wikis

The wikis property is an object that includes descriptions of other applications.  It is not used to enable geographically context sensitive jumps, but is instead used to link to articles in a wiki or other environment.  For example, linking to the wikipedia page on a given city or linking to a source report for an incident.

Example

```JSON
"wikis":
[
	{"name":"wikipedia","label":"Wikipedia","classification":"Unclassified","description":"","url":"http://en.wikipedia.org/wiki/"},
	{"name":"sharepoint","label":"SharePoint Document Library","classification":"Unclassified//SBU","description":"","url":"http://example.com/sites/default/files/"}
]
```

#### Data Sources

The data sources property is an object that includes strategy and protocol information for loading shared external resources.  Resources are specified here if they are used by multiple layers or are not used by the map itself.  Consequently, they only need to be loaded once over the network.

Example

```JSON
"datasources":
[
	{"name":"articles","label":"Articles","type":"hashmap","key":"name","delimiter":"\t","url":"links/articles.tsv"},
	{"name":"timeline","label":"Timeline","type":"hashmap","key":"entity","delimiter":"\t","url":"links/timeline.tsv"}
]
```

#### Bookmarks

The bookmarks property is an object that includes strategy and protocol information for loading spatiotemporal bookmarks.  Bookmarks are shared among users to decrease the amount of time it takes to find a high interest feature, such as the most used border crossing, most populous refugee camp, etc.  The actual location and/or feature information is specified in the bookmarks file.  See the related specification for the bookmarks file [here](https://github.com/state-hiu/cybergis-client-spec/blob/master/1.0/cybergis-client-spec-bookmarks-1.0.md).

Example

```JSON
"bookmarks": {"delimiter":"\t","url":"bookmarks/bookmarks.tsv"}
```

#### Glossaries

The glossaries property is an array of objects that includes strategy and protocol information for loading glossaries of terms and definitions.  Glossaries are shared among users and are generally accessible through the data popup.  See the related specification for glossary files [here](https://github.com/state-hiu/cybergis-client-spec/blob/master/1.0/cybergis-client-spec-glossary-1.0.md).

Example

```JSON
"glossaries":
[
	{"name":"glossary","label":"Glossary","delimiter":"\t","url":"glossaries/glossary.tsv"}
],
```

#### HashMaps

The hashmaps property is a object that includes hashmap keys and values for mapping integer keys to strings.  Additionally, the hashmaps property is first broken down by namespace to faciliate multiple hashmaps.  It can be used for translation or more frequently by decreasing network load.  For example, if you request alot of data about countries, then the WFS will only need to return a single number for each country instead of its name.  Since it is a hashmap, lookup is almost instantaneous once initialized.

Example

```JSON
"hashmaps":
{
	"boundaries":
	{
		"countries":
		[
			{"id":87,"name":"Jordan"},
			{"id":81,"name":"Iraq"},
			{"id":98,"name":"Lebanon"},
			{"id":171,"name":"Syria"},
			{"id":180,"name":"Turkey"}
		]
	}
}
```

#### P-Codes (pcodes)

The P-Codes property is an array of objects that includes strategy and protocol information for loading P-Code attributes.  By separating P-Code attributes from their geometry network load is decreased as you don't need to load the names for a parent administrative district for every one of its child districts.

Example

```JSON
	"pcodes":
	[
		{"level":1,"delimiter":"\t","url":"pcodes/pcodes-admin1.tsv"},
		{"level":2,"delimiter":"\t","url":"pcodes/pcodes-admin2.tsv"}
	]
```

#### Base Layers

The base layers property is an array of strings that specifies which layers to use as base layers.  Base layers are non-interactive and are not-included in the legend, search, or any other interactive controls.  For example, OSM, MapBox, and imagery are base layers.  GeoJSON, KML, and WFS layers are not base layers.

**Cascading**

| Order | Level | Property 1 | Property 2 | Property 3 | Property 4 |
| ---- | ---- | ---- | ---- | ---- |  ---- |
| 1 | Query String | bl | baseLayer | baseLayers |
| 2 | DOM | mapBaseLayer | mapBaseLayers
| 3 | File | baseLayers |

**Example**

```JSON
"baseLayers": ["osm"]
```

#### Feature Layers

The feature layers property is an array of strings that specifies which layers to use as feature layers.  Feature layers are interactive and are eligible for use in the legend, search, or any other interactive controls.  For example, GeoJSON, KML, and WFS layers are feature layers.  OSM, MapBox, and imagery layers are not feature layers.

**Cascading**

| Order | Level | Property 1 | Property 2 | Property 3 | Property 4 |
| ---- | ---- | ---- | ---- | ---- |  ---- |
| 1 | Query String | fl | featureLayer | featureLayers | layers |
| 2 | DOM | mapFeatureLayers | mapFeatureLayer | featureLayers | featureLayer |
| 3 | File | featureLayers | featureLayer |

**Example**

```JSON
"featureLayers": ["incidents"]
```

#### Render Layers

The render layers property is an array of strings that specifies which layers to actually render.   When specified. the CyberGIS Client renders this set of layers instead of feature layers.  The primary purpose is to increase performance.  For example, you are creating a thumbnail and no a priori that a layer won't be displayed.  Then render layers can be used to shortcut the loading of that layer, but still maintain the same user interaction when clicking on the map (mainly going to the full map).

**Cascading**

| Order | Level | Property 1 | Property 2 | Property 3 | Property 4 |
| ---- | ---- | ---- | ---- | ---- |  ---- |
| 1 | Query String | rl | renderLayer | renderLayers |  |
| 2 | DOM | mapRenderLayers | mapRenderLayer | renderLayers | renderLayer |
| 3 | File | renderLayers | renderLayer |
| 4 | Feature Layers |

**Example**

```JSON
"featureLayers": ["incidents"]
```

#### Search Layers

The search layers property is an array of strings that specifies which layers are searchable in the search control.

**Cascading**

| Order | Level | Property 1 | Property 2 | Property 3 | Property 4 |
| ---- | ---- | ---- | ---- | ---- |  ---- |
| 1 | Query String | sl | searchLayer | searchLayers | layers |
| 2 | DOM | mapSearchLayers |
| 3 | File | searchLayers |

**Example**

```JSON
"searchLayers": ["incidents"]
```

#### Legend Layers

The legend layers property is an array of strings that specifies the order of layers in the legend from top to bottom.

**Cascading**

| Order | Level | Property 1 | Property 2 | Property 3 | Property 4 |
| ---- | ---- | ---- | ---- | ---- |  ---- |
| 1 | Query String | legendLayer | legendLayers |
| 2 | DOM | mapLegendLayers |
| 3 | File | legendLayers |

**Fallback**: [Feature Layers](#feature-layers)

**Example**

```JSON
"legendLayers": ["incidents"]
```

#### Box Layers

The box layers property is (1) a string or (2) an array of strings that specifies the layer(s) to use in the box control.

**Cascading**

| Order | Level | Property 1 | Property 2 | Property 3 | Property 4 |
| ---- | ---- | ---- | ---- | ---- |  ---- |
| 1 | Query String | boxLayers | boxLayer |
| 2 | DOM | mapBoxLayers | mapBoxLayer |
| 3 | File | boxLayers | boxLayer |

**Example**

```JSON
"boxLayer": "incidents"
```

#### Chart Layers

The chart layers property is either (1) a string or (2) an array of strings that specifies the layer(s) to use in the chart control.

**Cascading**

| Order | Level | Property 1 | Property 2 | Property 3 | Property 4 |
| ---- | ---- | ---- | ---- | ---- |  ---- |
| 1 | Query String | chartLayers | chartLayer |
| 2 | DOM | mapChartLayers | mapChartLayer |
| 3 | File | chartLayers | chartLayer |

**Example**

```JSON
"chartLayer": "incidents"
```

## Examples

- [Properties, Version 1.0](https://github.com/state-hiu/cybergis-client-spec/blob/master/1.0/cybergis-client-example-properties-1.0.json)

## Contributing

HIU is currently not accepting pull requests for this repository.

## License
This project constitutes a work of the United States Government and is not subject to domestic copyright protection under 17 USC § 105.
