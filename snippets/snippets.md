## 2021-11-12

### Species, strains, etc.

Discussed the relationship between species, sub-species groups, and supraspecies groupings. The proposal is to introduce a concept of a species group, which, hierarchically, can be either smaller or larger than a species, and thus can include strains, breeds, cultivars, divisions, populations, etc.

The data structure representing such a group will have the following fields:

```js
{
  id: string;
  type: srting; // probably a closed set of possible types; is this a value set?
  name: string; // human-readable name of this specific group
}
```

A species thus will be associated with multiple groups. There is also a need to have a field indicating whether a given species (organism) is a reference for a given group; but it isn't yet clear where this field should go.

Potential problems:
- Production, which proposed this model, has a concept of `organism`, which is a much better fit for such a model. An organism can only belong to a group. In contrast, CDM uses the concept of `species`, and does not have an `organism`, so the relationship between a species and a group is not clear.


Examples:

```js

// MOUSE

{
  species {
    groups: [
      {
        id: "mouse_strain"
        type: "strain",
        name: "mouse strains",
        is_reference_for_group: true
      },
      {
        id: "vertebrates",
        type: division,
        name: "Vertebrates",
        is_reference_for_group: false
      }
    ]
  }
}


//  Something for Compara
group: {
  id: 'fish_reference_set',
  type: 'compara',
  name: 'Fish reference set',
  is_reference_for_group: true // <-- we may only need it for compara groups
}


// WHEAT

{
  species: {
    groups: [
      {
        id: "wheat_cultivars"
        type: "cultivar",
        name: "wheat cultivars",
      },
      {
        id: "wheat_cultivars"
        type: "population",
        name: "Agricultural plants",
      },
      {
        id: "european_plants"
        type: "population",
        name: "European plants",
      },
      {
        id: "model_organisms"
        type: "division",
        name: "Model organisms",
      },
      {
        id: "plants",
        type: "division",
        name: "Plants",
      }
    ]
  }
}
```


## 2021-06-25

### RNA products

Discussed on the example of a miRNA, which has a premature stem-loop structure and mature RNAs. Agreed that the fact that the product gets split into multiple fragments is best represented as multiple product-generating contexts. Using such fields as `parent` and `children`, we could represent hierarchical relationships between the premature and the mature products; however, in order to do so, stable ids will be required on the RNA product.

```js
{
  "product_generating_contexts": [
     
    // PGC for the stem-loop sequence:
    {
      "cdna": {...}
      "cds": null,
      "phased_exons": [...] // regular exon, with phases -1, -1
      "product": {
        "type": "RNA",
        "length": 102,
        "external_references": [],
        "sequence": Sequence,
        "mappings": [{
          "source": "miRBase",
          "accession_id": "MI0015835",
          "description": "Stem-loop sequence hsa-mir-4305"
        }]
      }
    },
 
    // PGC for a mature miRNA
    {
      "cdna": {},
      "cds": null,
      "phased_exons": [...] // not sure; it is a fragment; what would its corresponding exon be?
      "product": {
        "type": "RNA",
        "length": 18,
        "external_references": [],
        "sequence": Sequence,
        "mappings": [{
          "source": "miRBase",
          "accession_id": "MIMAT0016857",
          "description": "Mature sequence hsa-miR-4305"
        }]
      }
    },
  ]
}
```

## 2021-02-05

### Metadata

Below is an example in which `biotype` is just a plain member of a value set, and other fields represent values of value sets with additional fields

- `gencode_primary` has a `reasons` field (reasons for inclusion)
- `mane` has an `ncbi_transcript` field
- `exonic_overlap_same_strand` has an `associated_features` field

```json

{
  "metadata": {

    "mane": {
      "accession_id": "mane.select",
      "value": "select",
      "label": "MANE Select",
      "definition": "Gene loci with at least one protein coding transcript.",
      "description": "???",
      "ncbi_transcript": {
        "id": "NM_001374244",
        "url": "https://www.ncbi.nlm.nih.gov/protein/NM_001374244"
      }
    },


    "gencode_primary": {
      "accession_id": "gencode_primary.true",
      "value": true,
      "label": "GENCODE Primary",
      "definition": "Gene loci with at least one protein coding transcript.",
      "description": "???",
      "reasons": [
        {
          "accession_id": "gencode_primary_inclusion_reason.thing_of_beauty",
          "value": "thing_of_beauty",
          "label": "Some reason",
          "definition": "",
          "description": ""
        }
      ]
    },


    "biotype": {
      "accession_id": "biotype.transcript_protein_coding",
      "value": "protein_coding",
      "label": "Protein coding",
      "definition": "An mRNA that can be translated into a protein.",
      "description": "???"
    },



    "exonic_overlap_same_strand": {
      "accession_id": "biotype_additional_attribute.exonic_overlap_same_strand",
      "value": "exonic_overlap_same_strand",
      "label": "Exonic overlap with another transcript (same strand)",
      "definition": "Exonic overlap (same strand) with another Ensembl/GENCODE transcript",
      "associated_features": [
        {
          "type": "Gene",
          "stable_id": "ENSG"
        }
      ]
    }
  }
}

```


## 2020-10-30

### Product (realistic response from the graphql server)

**Note**: according to the CDM, the product is expected to also have a `sequence_checksum` field, which the server cannot resolve at the moment, so it is not included in the sample response below 

```json
{
  "product": {
    "stable_id": "ENSP00000499625.1",
    "unversioned_stable_id": "ENSP00000499625",
    "version": 1,
    "type": "Protein",
    "so_term": "polypeptide",
    "length": 22,
    "external_references": [
      {
        "accession_id": "UPI00000747D7",
        "name": "UPI00000747D7",
        "description": null,
        "assignment_method": {
          "type": "CHECKSUM",
          "description": "A reference inferred from a sequence checksum match, such as when the sequences are equal"
        },
        "url": "https://www.ebi.ac.uk/cgi-bin/dbfetch?db=uniparc&id=UPI00000747D7",
        "source": {
          "id": "UniParc",
          "name": "UniParc",
          "description": null,
          "url": "https://www.ebi.ac.uk/uniparc/",
          "release": null
        }
      }
    ]
  }
}
```

## 2020-10-23

### GeneFamily
The value of the `tree` field is a string whose format the api user can choose by passing a parameter to this field's resolver (e.g. newick, phyloxml, or json). We established that a graphql api cannot respond with arbitrarily deep trees otherwise.

```json
{
    "type": "gene_family",
    "members": {
        "ENSG0001": {"symbol":"BRCA1", "species":"homo_sapiens"},
        "ENSG0002": {...},
        ...
        "ENSG000N": {}
    },
    "model_id": "RFAM0001",
    "tree": "((ENSG0001,ENSG0002),ENSG000N)",
    "homologies": [
        {
            "source_gene": "ENSG0001",
            "target_gene": "ENSG0002",
            "type": "homolog",
            "homology_type": "ortholog",
            "subtype": "one-to-one",
            "perc_id": 100.0,
            "goc_score": 100,
            "wga_score": 99.5,
            "high_conf": 1
        },
        {
            "source_gene": "ENSG0001",
            "target_gene": "ENSG000N",
            "type": "homolog",
            "homology_type": "paralog",
            "subtype": "other",
            "perc_id": 79.9,
            "goc_score": 50,
            "wga_score": 60.4,
            "high_conf": 0,
        }
    ]
}
```

## 2020-10-09

### GeneFamily

```json
{
    "type": "Gene Family",
    "members": {
        "ENSG0001": {"symbol":"BRCA1", "species":"homo_sapiens"},
        "ENSG0002": {...},
        ...
        "ENSG000N": {}
    },
    "model_id": "RFAM0001",
    "tree": "((ENSG0001,ENSG0002),ENSG000N)",
    "homologies": [
        {
            "source_gene": "ENSG0001",
            "target_gene": "ENSG0002",
            "type": "one2one ortholog",
            "perc_id": 100.0,
            "goc_score": 100,
            "wga_score": 99.5,
            "high_conf": 1
        },
        {
            "source_gene": "ENSG0001",
            "target_gene": "ENSG000N",
            "type": "other paralog",
            "perc_id": 79.9,
            "goc_score": 50,
            "wga_score": 60.4,
            "high_conf": 0,
        }
    ]
}
```


## 2020-11-06

### Alignments
```json
{
    "type": "Whole Genome Alignment",
    "name": "mammals",
    "method": "LASTZ pairwise",
    "alignment_blocks": [
        Alignment, Alignment, ...
    ],
}

{
    "type": "Alignment",
    "sequences": [Aligned Sequence, Aligned Sequence, ...]
}

{
    "type": "Aligned Sequence",
    "assembly": Assembly,
    "unaligned_sequence": "AAAAGGGGGTTTT....",
    "slice": Slice,
    "cigar": [
        [5, 'X'], ['100', 'M'], ['200', 'D'], ['1', 'M']
    ],
}
```
