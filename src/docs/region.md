# Region

The `Region` data type describes the coordinate system that contains [Features](./feature.md). In biological terms, it represents a naturally occurring or an artificially produced polynucleotide. The `Region` has the following fields:

| Field                  | Type            | Description |
|------------------------|-----------------|-------------|
| name                   | string          | Region name
| code                   | RegionCode      | Code of the region - see below
| topology               | RegionTopology  | A string describing the topology of the region - see below
| sequence               | Sequence        | See [Sequence](./sequence.md)
| assembly               | Assembly        | See [Assembly](./assembly.md)
| length                 | integer         | Length of the region, in nucleotides
| metadata               | Metadata        | See [Metadata](./generic_metadata.md)
| top_level_region_rank  | integer or null | The ranking of the region, if the region is top-level. For chromosomes this will be the same as the karyotype rank. For non-top-level regions this will be null.

## RegionCode
RegionCode is an enum of strings with the following possible values:
- `chromosome`
- `plasmid`
- `scaffold`

## RegionTopology
RegionTopology is an enum of strings with the following possible values:
- `linear`
- `circular`

## Examples
```json
{
  "name": "13",
  "code": "chromosome",
  "topology": "linear",
  "sequence": { ... },
  "assembly": { ... },
  "length": 114364328,
  "metadata": {
    "ontology_terms": [
      {
        "accession_id": "SO:0000340",
        "value": "chromosome",
        "url": "www.sequenceontology.org/browser/current_release/term/SO:0000340",
        "source": {
          "name": "Sequence Ontology",
          "url": "www.sequenceontology.org",
          "description": "The Sequence Ontology..."
        }
      }
    ]
  },
  "top_level_region_rank": 13
}
```
