# Metadata

A feature or product may have various kinds of metadata associated with it. These pieces of metadata are described by the Metadata data type.

## A Metadata item

All metadata items will have the following fields in common:

| Field        				  | Type                        |Description 																			   |   
|-----------------------|-----------------------------|----------------------------------------------------|
| value        					| string                    	| The value of the piece of metadata   
| accession_id 					| string 											| The identifier relating to the piece of metadata


Metadata items tend to fall into one of two categories: metadata derived from an external reference (`ExternalReferenceMetadata`), and metadata derived from a [value set](./value_set.md) (`ValueSetMetadata`).

An `ExternalReferenceMetadata` item will have the following shape:

| Field          | Type                | Description 																				|
|----------------|---------------------|----------------------------------------------------|
| accession_id   | string              | Item's identifier in an external database
| value          | string              | Relevant information about the item
| url            | string              | URL for accessing the item in another resource
| source         | ExternalDB or null  | See [ExternalDB](./external_db.md)

A `ValueSetMetadata` item will have the following shape:

| Field          				| Type                       | Description 																										 |
|-----------------------|----------------------------|-----------------------------------------------------------------|
| accession_id   				| string                     | Item's identifier in a value sets glossary
| value          				| string                     | Value intended for programmatic use by the consumer
| label          				| string                     | A short, human-readable and display-friendly label
| definition     				| string                     | Succinct definition of the term
| description    				| string or null             | Optional longer description that can contain nuances


**Note**: apart from the fields listed in the table above, `ValueSetMetadata` items may also contain additional optional fields unique for each given kind of metadata. See [TranscriptManeMetadata](./transcript_metadata.md) or [GeneMetadata](./gene_metadata.md) for examples.
