# Region

The Region data type describes the coordinate system that contains Features. In biological terms, it represents a naturally occurring or an artificially produced polynucleotide. The Region has the following fields:

| Field     | Type           | Description |
|-------    |----------------|-------------|
| name      | string         | region name
| code      | RegionCode     | code of the region
| topology  | RegionTopology | a string describing the topology of the region
| so_term   | string         | accession code in Sequence Ontology
| length    | integer        | length of the region, in nucleotides

## RegionCode
RegionCode is an enum of strings with the following possible values:
- `chromosome`
- `plasmid`
- `scaffold`

## RegionTopology
RegionCode is an enum of strings with the following possible values:
- `linear`
- `circular`

## Examples
```json
{
  "name": "13",
  "code": "chromosome",
  "topology": "linear",
  "so_term": "???",
  "length": 114364328
}
```
