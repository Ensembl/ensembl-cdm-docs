# ExternalDB
Data type describing the source of the external reference.

| Field       | Type           | Description |
|-------------|----------------|-------------|
| id          | string         | identifier of external database
| name        | string         | name of external database
| description | string or null | additional information about the database
| url         | string or null | url of the database
| release     | string or null | identifier of data release

```json
{
  "id": "RefSeq_mRNA",
  "name": "RefSeq mRNA",
  "description": null,
  "url": "https://www.ncbi.nlm.nih.gov/projects/RefSeq/",
  "release": null
}
```
