# GenomicMappingLocation
`GenomicMappingLocation` provides the information about how the mapping between an Ensembl [product](./product.md) and an external feature projects back onto the genomic space.

| Field        | Type           | Description |
|--------------|----------------|-------------|
| slice        | Slice          | see [Slice](./slice.md)
| cigar_string | string         | a string representing the alignment

### Examples
```json
{
  "slice": { ... },
  "cigar_string": "3M1I3M1D5M"
}
```
