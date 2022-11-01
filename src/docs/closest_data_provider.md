# ClosestDataProvider

For cases when a match was calculated using an aggregator database, such as Interpro, this is the reference to the record in such database.

| Field        | Type       | Description |
|--------------|------------|-------------|
| source       | ExternalDB | See [ExternalDB](./external_db.md) in the documentation
| accession_id | string     | Unique identifier of the family in the database
| description  | string     | A textual description of the record in the database
| url          | string     | URL for accessing the family in the source database

## Examples
```json
{
  "source": { ...  },
  "accession_id": "IPR002093",
  "description": "The breast cancer type 2 susceptibility protein has a number of...",
  "url": "https://www.ebi.ac.uk/interpro/entry/InterPro/IPR002093/"
}
```
