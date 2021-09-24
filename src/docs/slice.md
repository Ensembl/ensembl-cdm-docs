# Slice

The Slice data type contains the information sufficient to describe the position of a Feature on a coordinate system. It consists of the following fields:

| Field     | Type     | Description |
|-------    |----------|-------------|
| region    | Region   | see Region
| location  | Location | see Location
| strand    | Strand   | see Strand

## Examples

1. Slice taken by transcript ENST00000671466.1 (BRCA2-211):

```json
{
  "location": {
    "start": 32315086,
    "end": 32316527,
    "length": 1442
  },
  "region": {
    "name": "13",
    "code": "chromosome",
    "topology": "linear",
    "length": 114364328
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
    "length": 1032
  },
  "region": {
    "name": "Chromosome",
    "code": "chromosome",
    "topology": "circular",
    "length": 5057142
  },
  "strand": {
    "code": "reverse",
    "value": -1
  }
}
```
