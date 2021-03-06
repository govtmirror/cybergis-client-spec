cybergis-client-spec
================

| Specifications: | [Client](https://github.com/state-hiu/cybergis-client-spec/blob/master/1.0/README.md) | [Properties](https://github.com/state-hiu/cybergis-client-spec/blob/master/1.0/cybergis-client-spec-properties-1.0.md) | [Proto](https://github.com/state-hiu/cybergis-client-spec/blob/master/1.0/cybergis-client-spec-proto-1.0.md) | [Carto](https://github.com/state-hiu/cybergis-client-spec/blob/master/1.0/cybergis-client-spec-carto-1.0.md) | [JIT](https://github.com/state-hiu/cybergis-client-spec/blob/master/1.0/cybergis-client-spec-jit-1.0.md) | [Glossaries](https://github.com/state-hiu/cybergis-client-spec/blob/master/1.0/cybergis-client-spec-glossary-1.0.md) | [Bookmarks](https://github.com/state-hiu/cybergis-client-spec/blob/master/1.0/cybergis-client-spec-bookmarks-1.0.md) |
| ---- |  ---- |  ---- |  ---- |  ---- |  ---- |   ---- |   ---- |

## CyberGIS
The Humanitarian Information Unit has been developing a sophisticated geographic computing infrastructure referred to as the CyberGIS. The CyberGIS provides highly available, scalable, reliable, and timely geospatial services capable of supporting multiple concurrent projects.  The CyberGIS relies on primarily open source projects, such as PostGIS, GeoServer, GDAL, OGR, and OpenLayers.  The name CyberGIS is dervied from the term geospatial cyberinfrastructure.

## Description

This repository contains specifications for CyberGIS client applications.  These specifications are currently only implemented for OpenLayers 2.13.

CyberGIS Client applications are configured using three files: [a properties file](#properties), [a layer prototype file (proto file)](#proto), and [a cartography file (carto file)](#carto).  A CyberGIS client application may also use a few optional files: 0 or 1 [bookmarks files](#bookmarks), 0 or more [glossary files](#glossary), etc.  The specifications for each of these files should be compatabile for each version number.

### Cascading

A general design principal for the CyberGIS clients is cascading.  Many configuration options can be specifed in multiple locations.  For example, the option to decide which non-basemap layers to display (featureLayers), can be specified as a query string parameter, in the HTML document as a HTML5 data attribute, or in the properties file.  Additionally, many options can be specified using different identifiers.  For example, the baselayers can be specified using baselayer or baselayers.  The initialization routing also attempts to infer good fallback values.  The initialization routing also detects and autocorrects conflicting configuration values, such as setting the center outside the max extent.

Although the initialization routine can't compete with the simpliest of hard-coded leaflet maps in startup time, through cascading it is possible to configure a feature rich CyberGIS client application with the literal bare-minimum customization that is required.

The usual cascading order is:

1.  Query String parameter

2.  HTML5 Data Attribute

3.  Properties File

4.  Fallback

## Specifications

### [Properties](https://github.com/state-hiu/cybergis-client-spec/blob/master/1.0/cybergis-client-spec-properties-1.0.md)

The properties file is used to configue which layers and controls to show on the map.  The properties file also contains pointers to shared external resources that are not specific to individual layers, such as P-Codes, Glossaries, Bookmarks, etc. 

### [Proto](https://github.com/state-hiu/cybergis-client-spec/blob/master/1.0/cybergis-client-spec-proto-1.0.md)

The layer prototype file (or protolayer file or proto file) links layer identifiers with (1) metadata and (2) strategy/protocol information for loading layers.

### [Carto](https://github.com/state-hiu/cybergis-client-spec/blob/master/1.0/cybergis-client-spec-carto-1.0.md)

The cartography file (or carto file) describes the cartography for each layer.  Additionally, the carto file describes the visual representation of a layer within a chart and box.  Generally speaking, any visualization of a layer is described in the carto file.

### [Bookmarks](https://github.com/state-hiu/cybergis-client-spec/blob/master/1.0/cybergis-client-spec-bookmarks-1.0.md)

A bookmarks file describes spatiotemporal bookmarks.  The bookmarks file usually contains the highest interest features or locations.

### [Glossaries](https://github.com/state-hiu/cybergis-client-spec/blob/master/1.0/cybergis-client-spec-glossary-1.0.md)

A glossary file describes a glossary of terms and definition.  Generally speaking, this information is not used within the map, but used elsewhere in application to help users understand vague or unknown terms.

## Versions

| Version | Purpose |
| ---- | ---- |
| 1.0 | Stable |
| 1.1 | Development |
| N | Nightly |

| Version | Client | Properties | Proto | Carto | JIT | Glossaries | Bookmarks |
| ---- |  ---- |  ---- |  ---- |  ---- |  ---- |   ---- |   ---- |
| 1.0 | [Client](https://github.com/state-hiu/cybergis-client-spec/blob/master/1.0/README.md) | [Properties](https://github.com/state-hiu/cybergis-client-spec/blob/master/1.0/cybergis-client-spec-properties-1.0.md) | [Proto](https://github.com/state-hiu/cybergis-client-spec/blob/master/1.0/cybergis-client-spec-proto-1.0.md) | [Carto](https://github.com/state-hiu/cybergis-client-spec/blob/master/1.0/cybergis-client-spec-carto-1.0.md) | [JIT](https://github.com/state-hiu/cybergis-client-spec/blob/master/1.0/cybergis-client-spec-jit-1.0.md) | [Glossaries](https://github.com/state-hiu/cybergis-client-spec/blob/master/1.0/cybergis-client-spec-glossary-1.0.md) | [Bookmarks](https://github.com/state-hiu/cybergis-client-spec/blob/master/1.0/cybergis-client-spec-bookmarks-1.0.md) |
| 1.1 | [Client](https://github.com/state-hiu/cybergis-client-spec/blob/master/1.0/README.md) | [Properties](https://github.com/state-hiu/cybergis-client-spec/blob/master/1.0/cybergis-client-spec-properties-1.0.md) | [Proto](https://github.com/state-hiu/cybergis-client-spec/blob/master/1.0/cybergis-client-spec-proto-1.0.md) | [Carto](https://github.com/state-hiu/cybergis-client-spec/blob/master/1.0/cybergis-client-spec-carto-1.0.md) | [JIT](https://github.com/state-hiu/cybergis-client-spec/blob/master/1.0/cybergis-client-spec-jit-1.0.md) | [Glossaries](https://github.com/state-hiu/cybergis-client-spec/blob/master/1.0/cybergis-client-spec-glossary-1.0.md) | [Bookmarks](https://github.com/state-hiu/cybergis-client-spec/blob/master/1.0/cybergis-client-spec-bookmarks-1.0.md) |

## Usage

Use these specifications to configure new CyberGIS clients.

## Contributing

HIU is currently not accepting pull requests for this repository.

## License
This project constitutes a work of the United States Government and is not subject to domestic copyright protection under 17 USC § 105.
