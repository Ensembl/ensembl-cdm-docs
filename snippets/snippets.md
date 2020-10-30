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
