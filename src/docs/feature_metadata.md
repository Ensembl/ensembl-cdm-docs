# Feature metadata

A feature may have various kinds of metadata associated with it. These pieces of metadata are described by the Metadata data type.

## A metadata item

All metadata items will have the following fields in common:

| Field        | Type                        
|--------------|-----------------------------
| value        | string, number, or boolean
| accession_id | string

Metadata items tend to fall into one of two categories: metadata derived from an external reference (XrefMetadata), and metadata derived from a value set (ValueSetMetadata).

An ExternalReferenceMetadata item will have the following shape (cf. [ExternalReference](./external_reference.md)):

| Field          | Type        | Description |
|----------------|-------------|-------------|
| accession_id   | string      | item's identifier in an external database
| value          | string      | relevant information about the item
| url            | string      | url for accessing the item in another resource
| source         | ExternalDB  | see ExternalDB

A ValueSetMetadata item will have the following shape:

| Field          | Type                       | Description |
|----------------|----------------------------|-------------|
| accession_id   | string                     | item's identifier in a value sets glossary
| value          | string, number, or boolean | value intended for programmatic use by the consumer
| label          | string                     | a short, human-readable and display-friendly label
| definition     | string                     | succinct definition of the term
| description    | string or null             | optional longer description that can contain nuances

**Note**: apart from the fields listed in the table above, ValueSetMetadata items may also contain additional optional fields unique for each given kind of metadata. See [TranscriptManeMetadata](./transcript_metadata.md) for an example.
