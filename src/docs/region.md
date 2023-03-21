# Region

The `Region` data type describes the coordinate system that contains [Features](./feature.md). In biological terms, it represents a naturally occurring or an artificially produced polynucleotide. The `Region` has the following fields:

| Field                 | Type                        | Description                                                                                                               |
|-----------------------|-----------------------------|---------------------------------------------------------------------------------------------------------------------------|
| accession_id          | string                      | INSDC identifier for the region                                                                                           |
| name                  | string                      | Commonly used name for region (e.g. 1, 2, 3, X, Y etc.)                                                                   |
| synonyms              | Array of string             | List of other names or synonyms the region may be known as                                                                |
| code                  | [ValueSet](./value_set.md)  | A ValueSet item containing information about the code of the region                                                       |
| is_top_level          | boolean                     | Flag to highlight whether or not the region can be considered as Top Level or not                                         |
| rank                  | int or null                 | The order of the region (resolves issues with alphanumeric character sorting)                                             |
| topology              | ValueSet                    | A ValueSet item describing the topology of the region - see below                                                         |
| assembled_from        | Array of Region             | A list of the Regions which were used to generate the Region (these will typically be Regions smaller than the Region)    |
| assembled_to          | Array of Region             | A list of the Regions which the Region has been incorporated into (these will typically be larger than the Region)        |
| sequence              | Sequence                    | See [Sequence](./sequence.md)                                                                                             |
| assembly              | Assembly                    | See [Assembly](./assembly.md)                                                                                             |
| length                | integer                     | Length of the region, in nucleotides                                                                                      |
| metadata              | Metadata                    | See [Metadata](./region_metadata.md)                                                                                      |

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
The region hierarchy is defined by the relationships a region has with other regions through `assembled_from` and `assembled_to`.  These relationships should only be one level deep both ways; a region can link to it direct "parents" and its direct "children", but not directly to its "grandparents" and "grandchildren". For example, a scaffold could be assembled from multiple contigs and be assembled into one chromosome - there is no direct link from the chromosome to the contigs. 

## Examples
```json
{
  "accession_id": "CM000675.2",
  "name": "13",
  "synonyms": ["13", "chr13", "NC_000001.11", "CM000675"],
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
  "assembles_to": [{...}],
  "assembled_from": [],
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
    ],
    "synonyms": [
      {
        "accession_id": "CM000675.2",
        "value": "CM000675.2",
        "url": "https://www.ncbi.nlm.nih.gov/nuccore/CM000675.2",
        "source": {
          "id": "INSDC",
          "name": "INSDC",
          "url": "https://insdc.org",
          "description": "INSDC"
        }
      },
      {
        "accession_id": "NC_000013.11",
        "value": "NC_000013.11",
        "url": "https://www.ncbi.nlm.nih.gov/nuccore/NC_000013",
        "source": {
          "id": "RefSeq",
          "name": "RefSeq",
          "url": "https://refseq.org",
          "description": "RefSeq"
        }
      },
      {
        "accession_id": "CM000675.2",
        "value": "13",
        "url": "https://ftp.ncbi.nlm.nih.gov/genomes/all/GCF/000/001/405/GCF_000001405.40_GRCh38.p14/GCF_000001405.40_GRCh38.p14_assembly_report.txt",
        "source": {
          "id": "GenBank",
          "name": "GenBank",
          "url": "https://GenBank.org",
          "description": "GenBank"
        }
      }
    ]
  }
}
```
