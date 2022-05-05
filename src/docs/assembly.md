# Assembly

The `Assembly` data type corresponds to an assembled sequence comprised of aligned reads

| Field             | Type            | Description
|-------------------|-----------------|---------------------
| id                | string          | The accession provided by the assembly creator
| name              | string          | The name provided by the assembly creator
| accession_id      | string          | Name provided by an accessioning body
| accessioning_body | string          | The independent assigner of an identity to the assembly
| organism          | Organism        | The organism entity to which many assemblies may belong
| regions           | array of Region | see Region
| default           | boolean         | The "best" assembly for the organism, for when the user does not want to choose
| tol_id            | string or null  | Tree of Life identifier

## Notes
1. Not all assemblies have yet been recognised by accessioning bodies like INSDC, so the accession_id and accessioning_body may be null
2. Not all assemblies will have ToLID

## Example
```json
{
  "id": "GRCh38.p13",
  "name": "GRCh38",
  "accession_id": "GCA_000001405.14",
  "accessioning_body": "EGA",
  "organism": { ... },
  "regions": [ ... ],
  "default": true,
  "tol_id": null
}
```

```json
{
  "id": "GCA_905171775.1",
  "name": "GCA_905171775.1",
  "accession_id": "GCA_905171775",
  "accessioning_body": "DToL",
  "organism": { ... },
  "regions": [ ... ],
  "default": true,
  "tol_id": "aRanTem1"
}
```
