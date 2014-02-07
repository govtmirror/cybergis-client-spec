Just-in-Time Specification, Version 1.0
================

| Specifications: | [Client](https://github.com/state-hiu/cybergis-client-spec/blob/master/1.0/README.md) | [Properties](https://github.com/state-hiu/cybergis-client-spec/blob/master/1.0/cybergis-client-spec-properties-1.0.md) | [Proto](https://github.com/state-hiu/cybergis-client-spec/blob/master/1.0/cybergis-client-spec-proto-1.0.md) | [Carto](https://github.com/state-hiu/cybergis-client-spec/blob/master/1.0/cybergis-client-spec-carto-1.0.md) | [JIT](https://github.com/state-hiu/cybergis-client-spec/blob/master/1.0/cybergis-client-spec-jit-1.0.md) | [Glossaries](https://github.com/state-hiu/cybergis-client-spec/blob/master/1.0/cybergis-client-spec-glossary-1.0.md) | [Bookmarks](https://github.com/state-hiu/cybergis-client-spec/blob/master/1.0/cybergis-client-spec-bookmarks-1.0.md) |
| ---- |  ---- |  ---- |  ---- |  ---- |  ---- |   ---- |   ---- |

## Description

The just-in-time specification is used for specifying just-in-time compiliation of layers.

## Specifications

### Properties

**General**: [Type](#type), [Refresh](#refresh), [Tasks](#tasks)

**Advanced**:  [Remote](#remote)

#### Type

The type property is a string.  It specifies the type of a just-in-time compilation for the layer.  Simple just-in-time compilation executes immediately after the layer loads its data.  Advanced just-in-time compilation uses data from a shared data source or performs another asynchronous request to get the secondary data.  Either way, the execution order is maintained as it re-exectutes all jobs on load of any resource.

**Options**

| Type | Alias 1 | 
| ---- | ---- |
| Simple | simple |
| Advanced | advanced |

Examples

- `"type":"simple"`
- `"type":"advanced"`

#### Refresh

The refresh property is an object.  It specifies when to execute just-in-time compilation for a layer.  Just-in-time compilation can happen when a layer loads its initial data and when a feature is focused (read: selected).

**Example**

```JSON
"refresh":{"init":true,"focus":false}
```

#### Tasks

The tasks property is an object.  It specifies a list of tasks for each jit job.

**Example**

```JSON
"tasks":
[
	{"op":"concat","output":"location","input":["${City}",", ","${State}"]},
	{"op":"concat","output":"title","input":["${name}"," (","Incident",")"]},
			
	{"op":"strip_fields","fields":["Description","Title","SubCity"],"characters":" '\t\n\""},
			
	{"op":"split","output":"categories_2","input":"categories","delimiter":","},
	{"op":"grep","output":"categories_3","input":"categories_2","values":["Extrajudicial Killing"],"keep":false}
]
```

#### Remote

## Examples

## Contributing

HIU is currently not accepting pull requests for this repository.

## License
This project constitutes a work of the United States Government and is not subject to domestic copyright protection under 17 USC § 105.
