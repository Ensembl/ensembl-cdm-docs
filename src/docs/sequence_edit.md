# SequenceEdit

The `SequenceEdit` data type contains information about modifications which have been made to a given sequence:

| Field             | Type                | Description |
|-------------------|---------------------|-------------|
| type              | string              | Description of the type of modification taking place. See notes below.
| metadata          | various             | See [generic_metadata](./generic_metadata.md)
| edit_level        | string              | The type of entity undergoing sequence modification
| start             | integer             | The coordinate the modification starts at
| end               | integer             | The coordinate the modification end at
| new_sequence      | Sequence            | The modified sequence  
| original_sequence | Sequence            | The original sequence
|order              | integer             | The sequence the modifications take place in (i.e. 1, 2, 3 where 1 is the first and three is the last)

## Notes
Type is a controlled vocabulary.  Acceptable options are:
- insertion
- deletion
- modification
- `editLevel` refers to the entity whose sequence has been modified.  In a `ProductGeneratingContext`, a `SequenceEdit` can refer to `protein` (the resulting `product`) or `cdna`


## Examples


### Ribosomal +1 frameshift example

```
 |Start|AAC GAA AAU CTG UUC GCU
 | AA  | N   E   N   L   F   A  
A|Start|ACG AAA AUC UGU UCG CUU
-|Start|123 123 123 123 123 123
 | AA  | T   K   I   C   S   L   
 ```

```json
{
  	"type": "delete",
  	"metadata": {
      "ontology_term":
      {
        "accession_id": "SO:0001211",
        "value": "plus_1_translational_frameshift",
        "url": "http://www.sequenceontology.org/browser/current_release/term/SO:0001211",
        "source": {
          "name": "Sequence Ontology",
          "url": "www.sequenceontology.org",
          "description": "The Sequence Ontology..."
        }
      }
    },
    "edit_level": "cdna",
  	"start": 1,
  	"end": 1,
  	"original_sequence" : {
      "alphabet": {
        "accession_id": "sequence_alphabet.dna",
        "value": "dna",
        "label": "DNA",
        "definition": "IUPAC notation for DNA sequence",
        "description": null
      },
      "checksum": "05k9059b95b89459k0k5904j89j",
      "sequence": "A"
    },
    "new_sequence" : {
      "alphabet": {
        "accession_id": "sequence_alphabet.dna",
        "value": "dna",
        "label": "DNA",
        "definition": "IUPAC notation for DNA sequence",
        "description": null
      },
      "checksum": "",
      "sequence": ""
    },
	  "order": 1
  }

```

### Ribosomal -1 frameshift example

```
|Start|AAC GAA AAU CTG UUC GCU UCA ...
| AA  | N   E   N   L   F   A   S  ...                         
|Start|AAC GAA AAU CUG UUC CGC UUC ...
| AA  | N   E   N   L   F   R   F  ...
 ```

```json
{
  	"type": "insertion",
  	"metadata": {
      "ontology_term":
      {
        "accession_id": "SO:0002329",
        "value": "minus_1_translational_frameshift",
        "url": "http://sequenceontology.org/browser/current_svn/term/SO:0002329",
        "source": {
          "name": "Sequence Ontology",
          "url": "www.sequenceontology.org",
          "description": "The Sequence Ontology..."
        }
      }
    },
    "edit_level": "cdna",
  	"start": 16,
  	"end": 16,
  	"original_sequence" : {
      "alphabet": {
        "accession_id": "sequence_alphabet.dna",
        "value": "dna",
        "label": "DNA",
        "definition": "IUPAC notation for DNA sequence",
        "description": null
      },
      "checksum": "5j84068658kv9403486b9309usocongi",
      "sequence": "G"
    },
    "new_sequence" :{
      "alphabet": {
        "accession_id": "sequence_alphabet.dna",
        "value": "dna",
        "label": "DNA",
        "definition": "IUPAC notation for DNA sequence",
        "description": null
      },
      "checksum": "v5m0936809k503069548989895v",
      "sequence": "C"
    },
	  "order": 1
  }

```


### Selenocysteine substitution example

```
ATG ACC ATT ACC TGA ... TGA
AUG ACC AUU ACC UGA ... UGA
 M   T   I   T   U  ...  *
                 ^
```

```json
{
  	"type": "modification",
  	"metadata": {
      "ontology_term":
      {
        "accession_id": "GO:0035368",
        "value": "selenocysteine insertion sequence binding",
        "url": "http://www.ncbi.nlm.nih.gov/pubmed/10760958",
        "source": {
          "name": "Sequence Ontology",
          "url": "www.sequenceontology.org",
          "description": "The Sequence Ontology..."
        }
      }
    },
    "edit_level": "protein",
  	"start": 5,
  	"end": 5,
  	"original_sequence" : {
      "alphabet": {
        "accession_id": "sequence_alphabet.aa",
        "value": "aa",
        "label": "AA",
        "definition": "IUPAC notation for Amino Acids",
        "description": null
      },
      "checksum": "e8f2b6ffd919c3cd2m39n093509vk030",
      "sequence": "*"
    },
    "new_sequence" : {
      "alphabet": {
        "accession_id": "sequence_alphabet.aa",
        "value": "aa",
        "label": "AA",
        "definition": "IUPAC notation for Amino Acids",
        "description": null
      },
      "checksum": "j389j5w93j89bw5d209cb68afe8872da",
      "sequence": "U"
    },
	  "order": 1
  }

```

### Patch example

Note: A "Patch" `SequenceEdit` should occur outside of `ProductGeneratingContexts`

```
Original: ATG ACC ATT ACC ATT CAT CCT ACT ...
Patched:  ATG ACT TAC GCT CGA CAT CCT ACT ...
             |<------------->|             
```

```json
{
  	"type": "modification",
  	"metadata": {
      "ontology_term":
      {
        "accession_id": "ENSGLOSSARY_0000188",
        "value": "Patch",
        "url": "http://ensembl.org/glossary/ENSGLOSSARY_0000188",
        "source": {
          "name": "Ensembl Glossary",
          "url": "http://ensembl.org/glossary",
          "description": "The Ensembl Glossary"
        }
      }
    },
    "edit_level": "transcript",
  	"start": 4,
  	"end": 15,
  	"original_sequence" : {
      "alphabet": {
        "accession_id": "sequence_alphabet.aa",
        "value": "aa",
        "label": "AA",
        "definition": "IUPAC notation for Amino Acids",
        "description": null
      },
      "checksum": "e8f2b6ffd9198uw3r9irp68afe8872da",
      "sequence": "ACC ATT ACC ATT"
    },
    "new_sequence" : {
      "alphabet": {
        "accession_id": "sequence_alphabet.aa",
        "value": "aa",
        "label": "AA",
        "definition": "IUPAC notation for Amino Acids",
        "description": null
      },
      "checksum": "e8f2bersedtfugiet4e8872da",
      "sequence": "ACT TAC GCT CGA"
    },
	  "order": 1
  }

```
