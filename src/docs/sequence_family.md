# Sequence Family

Reference to the sequence family record in the database that is the original provider of the data about this family.

| Field        | Type           | Description |
|--------------|----------------|-------------|
| source       | ExternalDB     | See [ExternalDB](./external_db.md) in the documentation
| accession_id | string         | Unique identifier of the family in the source database
| name         | string         | Name of the family
| description  | string or null | Description of the family
| url          | string or null | Url for accessing the family in the source database

```json
{
  "source": {
    "id": ???,
    "name": "Pfam",
    "description": null,
    "url": "https://pfam.xfam.org",
    "release": 34
  },
  "accession_id": "PF00634",
  "name": "BRCA2 repeat",
  "description" : "...",
  "url": "https://pfam.xfam.org/family/PF00634"
}
```
