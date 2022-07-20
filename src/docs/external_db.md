# ExternalDB
Data type describing the source of the [external reference](./external_reference.md).

| Field       | Type           | Description |
|-------------|----------------|-------------|
| id          | string         | Identifier of external database
| name        | string         | Name of external database
| description | string or null | Additional information about the database
| url         | string or null | URL of the database
| release     | string or null | Identifier of data release

### Examples

```json
{
  "id": "RefSeq_mRNA",
  "name": "RefSeq mRNA",
  "description": null,
  "url": "https://www.ncbi.nlm.nih.gov/projects/RefSeq/",
  "release": null
}
```
