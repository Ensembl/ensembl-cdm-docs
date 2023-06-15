# Assembly

The `Assembly` data type corresponds to an assembled sequence comprised of aligned reads

| Field             | Type              | Description
|-------------------|-------------------|--------------------------------------------------------------------------------------
| id                | string            | A unique identifier for the assembly (UUID)
| name              | string            | The name provided by the assembly creator
| accession_id      | string            | Name provided by an accessioning body
| accessioning_body | string            | The independent assigner of an identity to the assembly
| organism          | Organism          | The [organism](./organism.md) entity to which many assemblies may belong
| regions           | array of Region   | see [Region](./region.md)
| default           | boolean           | The "best" assembly for the organism, for when the user does not want to choose
| tolid             | string or null    | [Tree of Life identifier](https://id.tol.sanger.ac.uk/) (NB: This will be versioned)
| metadata          | AssemblyMetadata  | See [metadata](./metadata.md) and [assembly metadata](./assembly_metadata.md)   


## Notes
1. Not all assemblies have yet been recognised by accessioning bodies like INSDC, so the accession_id and accessioning_body may be null
2. Not all assemblies will have a Tree of Life Identifier (`tolid`)˜

## Examples
```json
{
  "id": "028db6ef-2b84-4cea-a9c9-707321e15e7d",
  "name": "GRCh38",
  "accession_id": "GCA_000001405.14",
  "accessioning_body": "EGA",
  "organism": { ... },
  "regions": [ ... ],
  "default": true,
  "tolid": null,
  "metadata": {...}
}
```

```json
{
  "id": "e191c702-f66f-46de-ab02-2bfb99c652cf",
  "name": "GCA_905171775.1",
  "accession_id": "GCA_905171775",
  "accessioning_body": "DToL",
  "organism": { ... },
  "regions": [ ... ],
  "default": true,
  "tolid": "aRanTem1.1",
  "metadata": {...}
}
```
