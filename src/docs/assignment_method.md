# AssignmentMethod
The `AssignmentMethod` data type describes the method by which an [external reference](./external_reference.md) was assigned to an item.

| Field       | Type           | Description |
|-------------|----------------|-------------|
| type        | string         | A member of a short list of keywords
| description | string or null | Brief human-readable explanation

## Note
`assignment_method`.`type` can have one of the following values:
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

## Examples
```json
{
    "type": "DIRECT",
    "description": "A reference made by an external resource of annotation to an Ensembl feature that Ensembl imports without modification"
}
```
