# External Reference

The `External Reference` data type represents a reference to a database outside of Ensembl. It has the following fields:

| Field             | Type             | Description |
|-------------------|------------------|-------------|
| accession_id      | string           | item's identifier in a foreign database
| name              | string           | item name
| description       | string or null   | additional information about the item
| url               | string or null   | url for accessing the item in another resource
| assignment_method | AssignmentMethod | see below
| source            | ExternalDB       | see below

## AssignmentMethod
A data type describing the method by which an external reference was assigned to an item.

| Field       | Type           | Description |
|-------------|----------------|-------------|
| type        | string         | a member of a short list of keywords
| description | string or null | brief human-readable explanation 

## ExternalDB

| Field       | Type           | Description |
|-------------|----------------|-------------|
| id          | string         | identifier of foreign database
| name        | string         | name of foreign database
| description | string or null | additional information about the database
| url         | string or null | url of the database
| release     | string or null | identifier of data release

## Notes
1. `accession_id` of a given reference is not guaranteed to be unique
2. `assignment_method.type` can have one of the following values: 
  - `CHECKSUM`
  - `COORDINATE_OVERLAP`
  - `DEPENDENT`
  - `DIRECT`
  - `INFERRED_PAIR`
  - `MISC`
  - `NONE`
  - `PROBE`
  - `PROJECTION`
  - `SEQUENCE_MATCH`
  - `UNMAPPED`
