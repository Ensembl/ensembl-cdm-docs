# AssignmentMethod
Data type describing the method by which an external reference was assigned to an item.

| Field       | Type           | Description |
|-------------|----------------|-------------|
| type        | string         | a member of a short list of keywords
| description | string or null | brief human-readable explanation

## Note
`assignment_method.type` can have one of the following values:
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

  ```json
  "assignment_method": {
    "type": "DIRECT",
    "description": "A reference made by an external resource of annotation to an Ensembl feature that Ensembl imports without modification"
  }
  ```
