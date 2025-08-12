# Example of model (gene, transcript, exons and product)

A worked example of the model demonstrating the relationship between [Genes](./gene.md), [Transcripts](./transcript.md), [exons](./exon.md) and [products](./product.md).  This example starts with the Gene GSX2 in Canis lupus familiarus, and the continues onto its transcript and associated protein.

```json
{
    "symbol": "GSX2",
    "name": null,
    "alternative_symbols": [],
    "alternative_names": [],
    "stable_id": "ENSCAFG00030018607.1",
    "version": 1,
    "unversioned_stable_id": "ENSCAFG00030018607",
    "type": "Gene",
    "metadata": {...},
    "slice": {
        "region": {
            "accession_id": "CM016443.1",
            "name": "13",
            "assembly": {
                "accession_id": "GCA_004886185.1",
                "organism": {
                    "scientific_parlance_name": "dog",
                    "scientific_name": "Canis lupus familiaris",
                    "species": {
                        "ncbi_common_name": "dog",
                        "scientific_name": "Canis lupus familiaris",
                        "taxon_id": 9615
                    }
                }
             }
        },
        "location": {
            "end": 46407641,
            "length": 2423,
            "start": 46405219
        },
        "strand": {
            "code": "forward",
            "value": 1
        }
    },
    "transcripts": [
    {
        "symbol": "GSX2-201",
        "relative_location": {
            "end": 2423,
            "length": 2423,
            "start": 1
        },
        "stable_id": "ENSCAFT00030034252.1",
        "version": 1,
        "unversioned_stable_id": "ENSCAFT00030034252",
        "type": "Transcript",
        "slice": {
            "default": true,
            "location": {
                "end": 46407641,
                "length": 2423,
                "start": 46405219
            }
        },    
        "spliced_exons": [
        {
            "index": 1,
            "relative_location": {
                "end": 753,
                "length": 753,
                "start": 1
            },
            "exon": {
                "version": 1,
                "stable_id": "ENSCAFE00030165581.1",
                "unversioned_stable_id": "ENSCAFE00030165581",
                "type": "Exon",
                "transcripts": {...},
                "metadata": {...}                        
            }
        },
        {
            "index": 2,
            "relative_location": {
                "end": 2423,
                "length": 951,
                "start": 1473
            },
            "exon": {
                "version": 1,
                "stable_id": "ENSCAFE00030165704.1",
                "unversioned_stable_id": "ENSCAFE00030165704",
                "type": "Exon",
                "transcripts": {...},
                "metadata": {...}                        
            }
        }],    
        "introns": [
        {
            "index": 1,
            "slice": {...},
            "relative_location": {
                "end": 1472,
                "length": 719,
                "start": 754
            },
            "type": "Intron"
        }],
        "product_generating_contexts": [
        {
            "product_type": "Protein",
            "default": true,
            "phased_exons": [
            {
                "index": 1,
                "start_phase": -1,
                "end_phase": 1,
                "exon": {
                    "version": 1,
                    "stable_id": "ENSCAFE00030165581.1",
                    "unversioned_stable_id": "ENSCAFE00030165581",
                    "type": "Exon",
                    "transcripts": {...},
                    "metadata": {...}                        
                },        
            },
            {
                "index": 2,
                "start_phase": 1,
                "end_phase": -1,
                "exon": {
                    "version": 1,
                    "stable_id": "ENSCAFE00030165704.1",
                    "unversioned_stable_id": "ENSCAFE00030165704",
                    "type": "Exon",
                    "transcripts": {...},
                    "metadata": {...}                        
                }
            }],
            "product": {
                "type": "Protein",
                "stable_id": "ENSCAFP00030029865.1",
                "unversioned_stable_id": "ENSCAFP00030029865",
                "version": 1,
                "length": 306,
                "external_references": [
                {
                    "accession_id": "A0A8I3NJN2",
                    "name": "A0A8I3NJN2.4",
                    "description": "GS homeobox 2 ",
                    "url": "http://purl.uniprot.org/uniprot/A0A8I3NJN2",
                    "assignment_method": {
                        "type": "SEQUENCE_MATCH",
                        "name": "Sequence match",
                        "description": "A reference inferred by the best match of two sequences",
                        "method_version": null
                    },
                    "source": {
                        "id": "Uniprot/SPTREMBL",
                        "name": "UniProtKB/TrEMBL",
                        "description": "UniProtKB/TrEMBL",
                        "url": "https://www.uniprot.org/",
                        "release": "Release 2025_03"
                    },
                }],
                "sequence": {
                    "alphabet": {
                        "accession_id": "alphabet.amino_acid",
                        "label": "Amino acid notation",
                        "value": "amino_acid_alphabet",
                        "definition": "IUPAC notation for amino acids",
                        "description": "One letter representation of amino acids inline with the IUPAC specification."
                    },
                    "checksum": "c87515930b692e0906e03805b8ce682f"
                },                    
                "family_matches": [
                {   
                    "sequence_family": {
                        "source": {
                            "id": "PFAM",
                            "name": "Pfam",
                            "description": "Pfam is a database of protein families that includes their annotations and multiple sequence alignments generated using hidden Markov models.",
                            "url": "http://pfam.xfam.org/",
                            "release": "35.0"
                        },
                        "accession_id": "PF00046",
                        "name": "PF00046",
                        "description": "Homeodomain",
                        "url": "https://www.ebi.ac.uk/interpro/entry/pfam/PF00046"
                    },
                    "via": {
                        "source": {
                            "id": "Interpro",
                            "name": "InterPro",
                            "description": "InterPro provides functional analysis of proteins by classifying them into families and predicting domains and important sites.",
                            "url": "https://www.ebi.ac.uk/interpro",
                            "release": "5.60-92.0"
                        },
                        "accession_id": "IPR001356",
                        "description": "Homeobox domain",
                        "url": "https://www.ebi.ac.uk/interpro/entry/InterPro/IPR001356"
                    },
                    "relative_location": {
                        "end": 261,
                        "length": 57,
                        "start": 205
                    },
                    "hit_location": {
                        "end": 57,
                        "length": 57,
                        "start": 1
                    },
                    "score": 77.2,
                    "evalue": 6.3e-22
                }]
             }
        }],
        "metadata": {
            "canonical": {
                "definition": "A single, representative transcript identified at every locus",
                "description": null,
                "label": "Ensembl canonical",
                "value": true
            }
        },
    }]
}
```