# AssignmentMethod
The `AssignmentMethod` data type describes the method by which an [external reference](./external_reference.md) was assigned to an item.

| Field           | Type           | Description                                                        |
|-----------------|----------------|--------------------------------------------------------------------|
| type            | string         | A member of a short list of keywords
| name            | string or null | Name of the assignment method (software package or algorithm used)
| description     | string or null | Brief human-readable explanation
| method_version  | string or null | Optional version of the software / algorithm used in assignment

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
  - `ENSEMBL_ML`


## Examples
```json
{
    "type": "DIRECT",
    "name": null,
    "description": "A reference made by an external resource of annotation to an Ensembl feature that Ensembl imports without modification",
    "version": null
}
```

```json
{
    "type": "ENSEMBL_ML",
    "name": "Ensembl Machine Learning Gene Name assignment",
    "description": "Predicted using Ensembl Machine Learning Gene Name assignment method",
    "version": "VERT_NN_1"

}
```
