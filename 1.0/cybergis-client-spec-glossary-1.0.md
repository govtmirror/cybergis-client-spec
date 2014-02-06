Glossary Specification, Version 1.0
================

## Description

A glossary file describes a glossary of terms and definition. Generally speaking, this information is not used within the map, but used elsewhere in application to help users understand vague or unknown terms.


## Specification

A glossary file is generally a tab delimited TSV file.  However, it can be delimited in a variety of ways.  The delimiter is set in the properties file.

### Columns

A glossary file contains the following columns: term and definition.

### Related Specifications

See the related specifications for: [Proto](https://github.com/state-hiu/cybergis-client-spec/blob/master/1.0/cybergis-client-spec-proto-1.0.md), [Carto](https://github.com/state-hiu/cybergis-client-spec/blob/master/1.0/cybergis-client-spec-carto-1.0.md), [Glossaries](https://github.com/state-hiu/cybergis-client-spec/blob/master/1.0/cybergis-client-spec-glossary-1.0.md), and [Bookmarks](https://github.com/state-hiu/cybergis-client-spec/blob/master/1.0/cybergis-client-spec-bookmarks-1.0.md).

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
