Bookmarks Specification, Version 1.0
================

## Description

A bookmarks file describes spatiotemporal bookmarks. The bookmarks file usually contains the highest interest features or locations.

## Specification

A bookmarks file is generally a tab delimited TSV file.  However, it can be delimited in a variety of ways.  The delimiter is set in the properties file.

A boookmarks file can contain two types of bookmarks: location and feature

### Location Bookmarks

Location bookmarks jump the user to a given location when triggered.  Location bookmarks can also include a zoom, too.

### Feature Bookmarks

Feature bookmarks jump the user to a given feature.  If a location and/or zoom is specified it is also respected.  The application will attempt to launch a popup if it is specified for the given layer when a bookmark is triggered.

### Columns

A bookmarks file contains the following columns: name, label, type, latitude, longitude, zoom, layer, field, and value.

## Examples

To load a glossary file it first must be linked to in the properties file.

### Properties File

```JSON
"glossaries":
[
	{"name":"glossary","label":"Glossary","delimiter":"\t","url":"glossaries/glossary.tsv"}
]
```

### Glossary File

| term  | definition                                                |
| ---- |:------------------------------------------------------     |
| CSO   | Bureau of Conflict Stabilization Operations (DOS/CSO)     |
| DRL   | Bureau of Democracy, Human Rights, and Labor (DOS/DRL)    |
| FFP   | Office of Food for Peace (USAID/DCHA/FFP)                 |
| HIU   | Humanitarian Information Unit (DOS/HIU)                   |
| USG   | United States Government                                  |

## Contributing

HIU is currently not accepting pull requests for this repository.

## License
This project constitutes a work of the United States Government and is not subject to domestic copyright protection under 17 USC § 105.
