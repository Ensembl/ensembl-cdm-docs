# Example of model (species, organism and assembly)

A worked example of the model demonstrating the relationship between [Species](./species.md), [Organism](./organism.md) and [Assembly](./assembly.md).  This example starts with the species Bombus terrestris and includes its associated organism and assembly.

```json

{
    "scientific_name": "Bombus terrestris",
    "ncbi_common_name": "buff-tailed bumblebee",
    "alternative_names": ["large earth bumblebee"],
    "taxon_id": 30195,
    "organisms": [
        {
            "scientific_name": "Bombus terrestris",
            "scientific_parlance_name": "buff-tailed bumblebee",
            "tolid": "iyBomTerr1", 
            "id" : "c2c77798-5818-49e9-ac12-c6176627599f", 
            "species": {...},
            "groups": [
            {
                "code": "insects",
                "type": "division",
                "name": "Insects",
                "is_reference_organism": "false",
                "organisms": [...],
                "metadata": {
                    "grouping_method": {
                        "accession_id": "grouping_method.consortium",
                        "value": "consortium",
                        "label": "Consortium",
                        "definition": "Consortium defined",
                        "description": "This grouping was defined by a consortium"
                    }
                }   
            }
        ],
        "assemblies" : [
            {
                "id": "6da5d92c-f674-4876-bc40-f700f59ed489", 
                "name": "iyBomTerr1.1",
                "accession_id": "GCA_910591885.1",  
                "accessioning_body": "ENA",
                "organism": {...},
                "default": false,
                "tolid": "iyBomTerr1.1",
                "regions": [
                    {
                        "accession_id": "OU342921.1",
                        "name": "1",
                        "synonyms": ["1", "OU342921"],
                        "coordinate_system": {
                            "accession_id": "region.chromosome",
                            "value": "Chromosome",
                            "label": "chromosome",
                            "definition": "Chromosome",
                            "description": "Structural unit composed of a nucleic acid molecule which controls its own replication through the interaction of specific proteins at one or more origins of replication."
                        },
                        "genetic_code": 1,
                        "is_top_level": true,
                        "rank": 1,
                        "topology":{
                            "accession_id": "topology.linear",
                            "value": "Linear",
                            "label": "linear",
                            "definition": "Linear topology",
                            "description": "Linear topology"
                        },
                        "made_from": [], 
                        "part_of": [],
                        "sequence": {
                            "alphabet": {
                                "accession_id": "sequence_alphabet.dna",
                                "value": "dna",
                                "label": "DNA",
                                "definition": "IUPAC notation for DNA sequence",
                                "description": null
                            },
                            "checksum": "1205ad8ae0c9d9ef3ebf66de5285cd96",
                        },
                        "assembly": {...}, 
                        "length": 18372659,
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
                                "accession" : "OU342921.1",
                                "value": "1",
                                "url": "https://www.ebi.ac.uk/ena/browser/view/OU342921.1", 
                                "source": {
                                    "id": "ENA",
                                    "name": "ENA",
                                    "url": "www.ebi.ac.uk/ena",
                                    "description": "ENA - European Nucleotide Archive"
                                }
                            },
                            {        
                                "accession" : "OU342921.1",
                                "value": "OU342921",
                                "url": "https://www.ebi.ac.uk/ena/browser/view/OU342921.1", 
                                "source": {
                                    "id": "ENA",
                                    "name": "ENA",
                                    "url": "www.ebi.ac.uk/ena",
                                    "description": "ENA - European Nucleotide Archive"
                                }
                            }
                        ]
                    }
                    }
                ]
            },
            {
                "id": "9899f7aa-966b-4de1-953d-cd2ccc5fe86f",
                "name": "iyBomTerr1.2",
                "accession_id": "GCA_910591885.2",
                "accessioning_body": "ENA",
                "organism": { },
                "default": true,
                "tolid": "iyBomTerr1.2",
                "regions": [ {...} ]
            },
            {
                "id": "bcb88ab8-1652-44f5-8bd4-8689951eada7",
                "name": "iyBomTerr1.2 alternate haplotype",
                "accession_id": "GCA_9105921952",
                "accessioning_body": "ENA",
                "organism": { },
                "default": false,
                "tolid": "iyBomTerr1.2",
                "regions": [ {...} ]
            } 
        ] 
    }]
}
```
