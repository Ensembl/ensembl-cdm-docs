# Assembly

The `Assembly` data type corresponds to an assembled sequence comprised of aligned reads

| Field             | Type                            | Description
|-------------------|---------------------------------|---------------------
| id                | string                          | A unique identifier for the `assembly`
| name              | string                          | The name provided by the `assembly` creator
| accession_id      | string or null                  | Name provided by an accessioning body
| accessioning_body | string or null                  | The organisation which assigned the `accession_id` to the `assembly`
| organism          | Organism                        | The `organism` the assembly represents.  See [Organism](./organism.md)
| regions           | array of Region                 | see [Region](./region.md)
| default           | boolean                         | The "best" `assembly` for the organism

## Notes
1. Not all `assemblies` have yet been recognised by accessioning bodies like INSDC, so the `accession_id` and accessioning_body may be null

## Examples
```json
{
  "id": "GRCh38.p13",
  "name": "GRCh38",
  "accession_id": "GCA_000001405.14",
  "accessioning_body": "EGA",
  "organism": { ... },
  "regions": [ ... ],
  "default": true
}
```

```json
{
  "id": "iwgsc_refseqv1.0",
  "name": "IWGSC RefSeq v1.0",
  "accession_id": "GCA_900519105.1",
  "accessioning_body": "ENA",
  "organism": { ... },
  "regions": [ ... ],
  "default": true
}
```
