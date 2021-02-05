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
