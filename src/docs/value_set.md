## ValueSet

A `ValueSet` is a collection of key/value pairs that are related to a given topic. For example, biotypes, APPRIS annotation terms, or transcript support level (TSL) definitions.

ValueSets are used extensively in the CoreDataModel (e.g. [ValueSetMetaData](./metadata.md) or [SequenceAlphabet](./sequence_alphabet.md)).

A `ValueSet` item should have the following fields:

| Field        | Type           |
|--------------|----------------|
| accession_id | string         |
| label        | string         |
| value        | string         |
| definition   | string or null |
| description  | string or null |

### Notes

#### Accession_id
An `accession_id` will have the format of `topic`.`unique_identifier`, where the `unique_identifier` is unique within the `topic` namespace.  Examples of this are:
- `gene_biotype.protein_coding_gene`
- `mane.select`


#### Label
A short human readable name for the `ValueSet` item, which could be used for display purposes.
Examples are:
- `protein coding gene`
- `MANE Select`


#### Value
A short machine readable name for the `ValueSet` item.  This should be lowercase and `snake_case`.
Examples are:
- `protein_coding_gene`
- `select`


#### Defintion
A short description of the `ValueSet` item.
Example:
- `A Transcript which is matched between Ensembl/GENCODE and RefSeq as part of the MANE project`


#### Description
An optional and more verbose definition of the `ValueSet` item.

Examples:
`The Matched Annotation from NCBI and EMBL-EBI is a collaboration between Ensembl/GENCODE and RefSeq. The MANE Select is a default transcript per human gene that is representative of biology, well-supported, expressed and highly-conserved. This transcript set matches GRCh38 and is 100% identical between RefSeq and Ensembl/GENCODE for 5' UTR, CDS, splicing and 3'UTR.`


#### Mutability
Implementations of `ValueSet` should specify whether or not their `ValueSet` items are mutable.  If they are not, then it should be acknowledged that alterations to `ValueSet` items will have global implications.


----

### Future fields
Additional fields which have been discussed but have not been included in the Core Data Model are:

#### Identical terms
This would be a list of terms which are semantically ***identical*** to the `ValueSet` item.  For example, this could be a SequenceOntology term.  It is still to be decided if this would be an accession_id to another term (e.g. SO:0001217), or it would have to contain the [source](./external_db.md) of the term.  This list could be empty.

#### Similar or equivalent terms
This would be a list of terms which are semantically ***similar*** to the `ValueSet` item.  For example, this could be a SequenceOntology term, or another `ValueSet` item.  It is still to be decided if this would be an accession_id to another term (e.g. SO:0001217), or it would have to contain the [source](./external_db.md) of the term.  This list could be empty.


Transcripts in the MANE Plus Clinical set are additional transcripts per locus necessary to support clinical variant reporting, for example transcripts containing known Pathogenic or Likely Pathogenic clinical variants not reportable using the MANE Select set. Note there may be additional clinically relevant transcripts in the wider RefSeq and Ensembl/GENCODE sets but not yet in MANE.																						

---

### Example

```json
{
  "accession_id": "mane.plus_clinical",
  "value": "MANE Plus Clinical",
  "label": "plus_clinical",
  "definition": "The MANE Plus Clinical set",
  "description": "Transcripts in the MANE Plus Clinical set are additional
  transcripts per locus..."
}
```
