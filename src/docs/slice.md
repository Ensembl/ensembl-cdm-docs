# Slice

The `Slice` data type contains the information sufficient to describe the position of a Feature on a coordinate system. It consists of the following fields:

| Field     | Type     | Description |
|-------    |----------|-------------|
| region    | Region   | see [Region](./region.md)
| location  | Location | see [Location](./location.md)
| strand    | Strand   | see [Strand](./strand.md)

## Examples

1. Slice taken by transcript ENST00000671466.1 (BRCA2-211):

```json
{
  "location": {
    "start": 32315086,
    "end": 32316527,
    "length": 1442,
    "location_modifier": null
  },
  "region": {
    "name": "13",
    "code": "chromosome",
    "topology": "linear",
    "sequence": { ... },
    "assembly": { ... },
    "length": 114364328,
    "metadata": { ... }
  },
  "strand": {
    "code": "forward",
    "value": 1
  }
}
```



2. Slice taken by the `hemE` gene — a gene on a circular bacterial chromosome (which Ensembl labels simply as "Chromosome") that overlaps the origin:

```json
{
  "location": {
    "start": 5056183,
    "end": 72,
    "length": 1032,
    "location_modifier": null
  },
  "region": {
    "name": "Chromosome",
    "code": "chromosome",
    "topology": "circular",
    "sequence": { ... },
    "assembly": { ... },
    "length": 5057142,
    "metadata": { ... }
  },
  "strand": {
    "code": "reverse",
    "value": -1
  }
}
```
