cybergis-client-spec
================

## Description

This repository contains specifications for CyberGIS client applications.  These specifications are currently only implemented for OpenLayers 2.13.

CyberGIS Client applications are configured using three file: a properties file, a layer prototype file (proto file), and a cartography file (carto file). The specifications for each of these files should be compatabile for each version number.

### Properties

The properties file is used to configue which layers and controls to show on the map.  The properties file also contains pointers to shared external resources that are not specific to individual layers, such as P-Codes, Glossaries, Bookmarks, etc. 

### Proto

The layer prototype file (or protolayer file or proto file) links layer identifiers with (1) metadata, and (2) strategy/protocol information for loading layers.

### Carto

The cartography file (or carto file) describes the cartography for each layer.  Additionally, the carto file describes the visual representation of a layer within a chart and box.  Generally speaking, any visualization of a layer is described in the carto file.

### Cascading

A general design principal for the CyberGIS clients is cascading.  Many configuration options can be specifed in multiple locations.  For example, the option to decide which non-basemap layers to display (featureLayers), can be specified as a query string parameter, in the HTML document as a HTML5 data attribute, or in the properties file.  Additionally, many options can be specified using different identifiers.  For example, the baselayers can be specified using baselayer or baselayers.  The initialization routing also attempts to infer good fallback values.  The initialization routing also detects and autocorrects conflicting configuration values, such as setting the center outside the max extent.

Although the initialization routine can't compete with the simpliest of hard-coded leaflet maps, through cascading it is possible to configure a feature rich CyberGIS client application with the literal bare-minimum customization that is required.

The usual cascading order is:
1.  Query String parameter
2.  HTML5 Data Attribute
3.  Properties File
4.  Fallback

### CyberGIS
The Humanitarian Information Unit has been developing a sophisticated geographic computing infrastructure referred to as the CyberGIS. The CyberGIS provides highly available, scalable, reliable, and timely geospatial services capable of supporting multiple concurrent projects.  The CyberGIS relies on primarily open source projects, such as PostGIS, GeoServer, GDAL, OGR, and OpenLayers.  The name CyberGIS is dervied from the term geospatial cyberinfrastructure.

## Specification

### [CyberGIS Client, Version 1.0](https://github.com/state-hiu/cybergis-client-spec/blob/master/1.0/)

Stable version

- [Properties, Version 1.0](https://github.com/state-hiu/cybergis-client-spec/blob/master/1.0/cybergis-client-spec-properties-1.0.md)

- [Proto, Version 1.0](https://github.com/state-hiu/cybergis-client-spec/blob/master/1.0/cybergis-client-spec-proto-1.0.md)

- [Carto, Version 1.0](https://github.com/state-hiu/cybergis-client-spec/blob/master/1.0/cybergis-client-spec-carto-1.0.md)

### [1.1](https://github.com/state-hiu/cybergis-client-spec/blob/master/1.1/)

Development version

Coming soon!

## Usage

Use these specifications to configure new CyberGIS clients.

## Contributing

HIU is currently not accepting pull requests for this repository.

## License
This project constitutes a work of the United States Government and is not subject to domestic copyright protection under 17 USC § 105.
