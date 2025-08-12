# Region

The `Region` data type describes the coordinate system that contains [Features](./feature.md). In biological terms, it represents a naturally occurring or an artificially produced polynucleotide. The `Region` has the following fields:

| Field                 | Type                        | Description                                                                                                                                   |
|-----------------------|-----------------------------|-----------------------------------------------------------------------------------------------------------------------------------------------|
| accession_id          | string                      | INSDC identifier for the region                                                                                                               |
| name                  | string                      | Commonly used name for region (e.g. 1, 2, 3, X, Y etc.)                                                                                       |
| synonyms              | Array of RegionSynonymMetadata             | List of synonyms the region may be known as (including `name`)                                                                                |
| coordinate_system     | [ValueSet](./value_set.md)  | A ValueSet item containing information about the coordinate_system (e.g chromosome, contig) of the region                                     |
| genetic_code          | integer                     | Genetic code based on the [NCBI's list of genetic codes](https://www.ncbi.nlm.nih.gov/Taxonomy/taxonomyhome.html/index.cgi?chapter=cgencodes) |
| is_top_level          | boolean                     | Flag to explicitly mark a selected subset of regions as "top Level"                                                                           |
| rank                  | int or null                 | The order of the region (resolves issues with alphanumeric character sorting)                                                                 |
| topology              | ValueSet                    | A ValueSet item describing the topology of the region - see below                                                                             |
| made_from             | Array of Region             | A list of the Regions which were used to generate the Region (these will typically be Regions smaller than the Region)                        |
| part_of               | Array of Region             | A list of the Regions which the Region has been incorporated into (these will typically be larger than the Region)                            |
| sequence              | Sequence                    | See [Sequence](./sequence.md)                                                                                                                 |
| assembly              | Assembly                    | See [Assembly](./assembly.md)                                                                                                                 |
| length                | integer                     | Length of the region, in nucleotides                                                                                                          |
| metadata              | Metadata                    | See [Metadata](./region_metadata.md)                                                                                                          |

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


## Synonyms
`synonyms` for a region cover alternative means of reference including accession IDs (both versioned and unversioned) and other commonly used names (such as "3" and "chr5").  It should be noted that the latter tend not to have a specific identifiable source and as such do not have accession IDs in their `external_reference` metadata.

## Region hierarchy
The region hierarchy is defined by the relationships a region has with other regions through `made_from` and `part_of`.  These relationships should only be one level deep both ways; a region can link to it direct "parents" and its direct "children", but not directly to its "grandparents" and "grandchildren". For example, a scaffold could be `made_of` from multiple contigs and be `part_of` one chromosome - there is no direct link from the chromosome to the contigs.  

## Assembly
Each `region` will only link to one `assembly`.

## Rank
Based on the order within the karyotype Chromosome 1 = 1, X = 23, Y = 24 (in Human for example).  

## Ordering
To ensure regions are returned in a specific order, it is suggested that implementations of this model extend it with an additional field to capture an "order". This has not been included in the model as it is not essential for describing a region and may be implementation specific.  Ranked regions should be returned first.

## Examples
```json
{
  "accession_id": "CM000675.2",
  "name": "13",
  "synonyms": ["13", "chr13","NC_000013.11", "CM000675", "NC_000013"],
  "coordinate_system": {
    "accession_id": "region.chromosome",
    "value": "Chromosome",
    "label": "chromosome",
    "definition": "Chromosome",
    "description": "Structural unit composed of a nucleic acid molecule which controls its own replication through the interaction of specific proteins at one or more origins of replication."
  },
  "genetic_code" : 1,
  "is_top_level": true,
  "rank": 13,
  "topology":{
    "accession_id": "topology.linear",
    "value": "Linear",
    "label": "linear",
    "definition": "Linear topology",
    "description": "Linear topology"
  },
  "made_from": [{...}], 
  "part_of": [],
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
      }, 
      {...}
    ],
 
    "synonyms": [
      {        
      "accession" : null,
        "value": "13",
        "url": "https://ftp.ncbi.nlm.nih.gov/genomes/all/GCA/000/001/405/GCA_000001405.40_GRCh38.p14/GCA_000001405.40_GRCh38.p14_assembly_report.txt", 
        "source": {
          "id": "GenBank",
          "name": "GenBank",
          "url": "https://GenBank.org",
          "description": "GenBank"
        }
      },
      {
        "accession" : null,
        "value": "chr13",
        "url": "https://ftp.ncbi.nlm.nih.gov/genomes/all/GCA/000/001/405/GCA_000001405.40_GRCh38.p14/GCA_000001405.40_GRCh38.p14_assembly_report.txt",
        "source": {
          "id": "GenBank",
          "name": "GenBank",
          "url": "https://GenBank.org",
          "description": "GenBank"
        }
      } ,
      {
        "accession_id": "CM000675.2",
        "value": "CM000675",
        "url": "https://www.ncbi.nlm.nih.gov/nuccore/CM000675.2",
        "source": {
          "id": "INSDC",
          "name": "INSDC",
          "url": "https://insdc.org",
          "description": "INSDC"
        }
      },
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
        "url": "https://www.ncbi.nlm.nih.gov/nuccore/NC_000013.11",
        "source": {
          "id": "RefSeq",
          "name": "RefSeq",
          "url": "https://refseq.org",
          "description": "RefSeq"
        }
      },
      {
        "accession_id": "NC_000013.11",
        "value": "NC_000013",
        "url": "https://www.ncbi.nlm.nih.gov/nuccore/NC_000013.11", 
        "source": {
          "id": "NCBI",
          "name": "NCBI",
          "url": "www.ncbi.nlm.nih.gov",
          "description": "RefSeq"
        }
      }
    ],

    "biological_locations" : [
      {
        "accession_id": "SO:0000628",
        "value": "chromosomal_structural_element",
        "url": "http://sequenceontology.org/browser/current_release/term/SO:0000628",
        "source": {
            "id": "SO",
            "name": "Sequence ontology",
            "url": "sequenceontology.org",
            "description": "The Sequence Ontology is a set of terms and relationships used to describe the features and attributes of biological sequence."
        }
      }
    ]
  }
}
```
