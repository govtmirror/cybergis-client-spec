Bookmarks Specification, Version 1.0
================

## Description

A bookmarks file describes spatiotemporal bookmarks. The bookmarks file usually contains the highest interest features or locations.

## Specification

A bookmarks file is generally a tab delimited TSV file.  However, it can be delimited in a variety of ways.  The delimiter is set in the properties file.

A boookmarks file can contain two types of bookmarks: location and feature.

### Location Bookmarks

Location bookmarks jump the user to a given location when triggered.  Location bookmarks can also include a zoom, too.

### Feature Bookmarks

Feature bookmarks jump the user to a given feature.  If a location and/or zoom is specified it is also respected.  The application will attempt to launch a popup if it is specified for the given layer when a bookmark is triggered.

### Columns

A bookmarks file contains the following columns: name, label, type, latitude, longitude, zoom, layer, field, and value.

### Related Specifications

See the related specifications for: [Proto](https://github.com/state-hiu/cybergis-client-spec/blob/master/1.0/cybergis-client-spec-proto-1.0.md), [Carto](https://github.com/state-hiu/cybergis-client-spec/blob/master/1.0/cybergis-client-spec-carto-1.0.md), [Glossaries](https://github.com/state-hiu/cybergis-client-spec/blob/master/1.0/cybergis-client-spec-glossary-1.0.md), and [Bookmarks](https://github.com/state-hiu/cybergis-client-spec/blob/master/1.0/cybergis-client-spec-bookmarks-1.0.md).

## Examples

To load a glossary file it first must be linked to in the properties file.

### Properties File

```JSON
"bookmarks": {"delimiter":"\t","url":"bookmarks/bookmarks.tsv"}
```

### Bookmarks File

| name | label | type | latitude | longitude | zoom | layer | field | value |
| ---- | ----  | ---- | ----     | ----      | ---- | ----  | ----  | ----  |
| full_extent | Full Extent| location | 35.2330 | 38.1318 | 7 | -  | -  | -  |
| aleppo | Aleppo | feature | - | - | - | syria_pcodes_admin4  | name  | SY020000C1007  |
| damascus | Damascus | feature | - | - | - | syria_pcodes_admin4  | name  | SY010000C1001  |
| homs | Homs | feature | - | - | - | syria_pcodes_admin1  | name  | SY04  |

## Contributing

HIU is currently not accepting pull requests for this repository.

## License
This project constitutes a work of the United States Government and is not subject to domestic copyright protection under 17 USC § 105.
