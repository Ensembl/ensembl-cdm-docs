# Subassembly

The `Subassembly` data type corresponds a distinct set of chromosomes within a (polyploid) assembly. It includes the following fields:

| Field             | Type              | Description                                                     |
|-------------------|-------------------|-----------------------------------------------------------------|
| id                | string            | A unique identifier for the subassembly (UUID)                  |
| name              | string            | The name provided to this subassembly by the assembly creator   |
| assembly          | Assembly          | See [Assembly](./assembly.md)                                   |
| regions           | array of Region   | See [Region](./region.md)                                       |

## Notes

1. Each `subassembly` will only link to one `assembly`.
2. Only *chromosome* `regions` can be part of a `subassembly`.
3. For monoploid (`ploidy=1`) and diploid (`ploidy=2`) `assemblies`, a single `subassembly` named `default` will include all the chromosome `regions` of the `assembly`.

## Examples

```json
{
  "id": "67299654-876f-402d-8eaa-0e4531628982",
  "name": "default",
  "assembly": { ... },
  "regions": [...]
}
```

```json
{
  "id": "6d2058c8-e0b2-4edc-8c1f-47736e3b455c",
  "name": "A",
  "assembly": { ... },
  "regions": [...]
}
```
