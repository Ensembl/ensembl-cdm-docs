# Region

The Region data type describes the coordinate system that contains Features. In biological terms, it represents a naturally occurring or an artificially produced polynucleotide. The Region has the following fields:

| Field     | Type           | Description |
|-------    |----------------|-------------|
| name      | string         | region name
| code      | RegionCode     | code of the region
| topology  | RegionTopology | a string describing the topology of the region
| sequence  | Sequence       | see Sequence
| assembly  | Assembly       | see Assembly
| length    | integer        | length of the region, in nucleotides
| metadata  | Metadata       | 

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
  }
}
```
