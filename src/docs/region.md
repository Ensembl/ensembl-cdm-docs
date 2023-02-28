# Region

The `Region` data type describes the coordinate system that contains [Features](./feature.md). In biological terms, it represents a naturally occurring or an artificially produced polynucleotide. The `Region` has the following fields:

| Field                 | Type                        | Description                                                                                                               |
|-----------------------|-----------------------------|---------------------------------------------------------------------------------------------------------------------------|
| name                  | string                      | Region name                                                                                                               |
| alternative_names     | Array of string             | List of other names the region may be known as                                                                            |
| code                  | [ValueSet](./value_set.md)  | A ValueSet item containing information about the code of the region                                                       |
| is_top_level          | boolean                     | Flag to highlight whether or not the region can be considered as Top Level or not                                         |
| rank                  | int or null                 | The order of the region (resolves issues with alphanumeric character sorting)                                             |
| topology              | ValueSet                    | A ValueSet item describing the topology of the region - see below                                                         |
| parents               | Array of Region             | A list of the Regions which were used to generate the Region (these will typically be Regions smaller than the Region)    |
| children              | Array of Region             | A list of the Regions which the Region has been incorporated into (these will typically be larger than the Region)        |
| sequence              | Sequence                    | See [Sequence](./sequence.md)                                                                                             |
| assembly              | Assembly                    | See [Assembly](./assembly.md)                                                                                             |
| length                | integer                     | Length of the region, in nucleotides                                                                                      |
| metadata              | Metadata                    | See [Metadata](./generic_metadata.md)                                                                                     |

## Code ValueSet
The code ValueSet contains a description about different types of Region, including the following:
- `chromosome`
- `plasmid`
- `scaffold`
- `contig`


## Topology ValueSet
The topology ValueSet contains the following possible values:
- `linear`
- `circular`

## Region hierarchy 
The region hierarchy is defined by the relationships a region has with other regions through `parents` and `children`.  These relationships should only be one level deep both ways; a region can link to it direct parents and its direct children, but not directly to its grandparents and grandchildren. For example, a contig could have multiple parents which are scaffolds and it could have one child which is a chromosome. 

## Examples
```json
{
  "name": "13",
  "alternative_names":["chr13"]
  "code": {
    "accession_id": "region.chromosome",
    "value": "Chromosome",
    "label": "chromosome",
    "definition": "Chromosome",
    "description": "Structural unit composed of a nucleic acid molecule which controls its own replication through the interaction of specific proteins at one or more origins of replication."
  },
  "topology":{
    "accession_id": "topology.linear",
    "value": "Linear",
    "label": "linear",
    "definition": "Linear topology",
    "description": "Linear topology"
  },
  "is_top_level": true,
  "rank": 13,
  "parents": [{...}],
  "children": [],
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
