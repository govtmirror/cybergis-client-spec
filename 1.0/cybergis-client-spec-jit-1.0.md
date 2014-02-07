Just-in-Time Specification, Version 1.0
================

| Specifications: | [Client](https://github.com/state-hiu/cybergis-client-spec/blob/master/1.0/README.md) | [Properties](https://github.com/state-hiu/cybergis-client-spec/blob/master/1.0/cybergis-client-spec-properties-1.0.md) | [Proto](https://github.com/state-hiu/cybergis-client-spec/blob/master/1.0/cybergis-client-spec-proto-1.0.md) | [Carto](https://github.com/state-hiu/cybergis-client-spec/blob/master/1.0/cybergis-client-spec-carto-1.0.md) | [JIT](https://github.com/state-hiu/cybergis-client-spec/blob/master/1.0/cybergis-client-spec-jit-1.0.md) | [Glossaries](https://github.com/state-hiu/cybergis-client-spec/blob/master/1.0/cybergis-client-spec-glossary-1.0.md) | [Bookmarks](https://github.com/state-hiu/cybergis-client-spec/blob/master/1.0/cybergis-client-spec-bookmarks-1.0.md) |
| ---- |  ---- |  ---- |  ---- |  ---- |  ---- |   ---- |   ---- |

## Description

The just-in-time specification is used for specifying just-in-time compiliation of layers.

**Just-in-Time**

Just-in-time (JIT) compilation, also known as dynamic translation, in the general programming concept that source code is compiled into machine code at run time.  Although the concept cannot be ported entirely to web mapping applications, much of the functionality is maintained.  In regards to the CyberGIS, JIT references the _compilation_ of _resources_ into _features_ for layers.  These resources includes a layer's standard data retrived from OGC services, but can also include shared resources (resources shared across layers) and remote resources (resources treated as unique for each layer).

**Functional Paradigm**

The just-in-time specification has been developed using a functional programming paradigm, as opposed to an object-oriented paradigm.  Most other CyberGIS specifications have been developed using a object-oriented paradigm.  See http://en.wikipedia.org/wiki/Functional_programming and http://en.wikipedia.org/wiki/Programming_paradigm for more information.  Therefore, jobs and tasks are always executed in the order they are specified.

**Jobs**

Just-in-time compilation for a layer is broken down into jobs.  Each job may specify a resource and how to compile it once the resource's data has been loaded.  Each job contains a list of tasks, represented as an array of objects, that will execute whenever the job's data is loaded.  If a job doesn't specify a resource, the tasks will execute whenever the layer's main data is loaded.  Jobs will always be execute in the order they appear in the array.

**Tasks**

Jobs are furthermore broken down into tasks.  Tasks are discrete programmatic commands to execute in order once a resource's data is loaded.  Tasks will always execute in order that they appear in the array.

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

The tasks property is an array of objects.  It specifies a list of tasks for each jit job.

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

The remote property is an object.  It specifies how to load the resource for a job.  The object specifies how to retrieve the data (from a shared resource or remote resource) and how to merge the data with the layer's main data.

**Example**

```JSON
"remote":
{
	"join"{"left""name","right":"name","type":"single","include":"all"},
	"source":"articles"
}
```

## Examples

## Contributing

HIU is currently not accepting pull requests for this repository.

## License
This project constitutes a work of the United States Government and is not subject to domestic copyright protection under 17 USC § 105.
