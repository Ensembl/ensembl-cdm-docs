# Organism

The Organism data type contains information sufficient to describe a given specific instance of a species (such as a breed or strain). It consists of the following fields:

| Field                     | Type                    | Description                               | 
|---------------------------|-------------------------|-------------------------------------------|
| scientific_name           | string                  | Scientific name of the species.           
| curated_common_name       | string or null          | Preferred name for display purposes, which can be the same as NCBI's common name
| species                   | Species                 | The related species
| groups                    | array of OrganismGroup  | An array of OrganismGroups to provide additional information about the organism       


# OrganismGroup

The OrganismGroup data type contains information relating to the organism, including breed, stain, division:

| Field         | Type                   | Description                               | 
|---------------|------------------------|-------------------------------------------|
| id            | string                 | ID for the species group           
| type          | string                 | Type of the species group   
| name          | string                 | Name of the species group     




## Examples

1. Representation of Cow:

```json
{
  "scientific_name": "Bos taurus",
  "curated_common_name": "cow",
  "species": {
    "scientific_name": "Bos taurus",
    "ncbi_common_name": "cattle",
    "curated_common_name": "cow",
    "alternative_names": ["bovine", "cow", "dairy cow", "domestic cattle", "domestic cow"],
    "taxon_id": 9913,
    "species_groups" : []
  },
 "groups": [{
    "id": "hereford_breed",
    "type": "breed",
    "name": "Hereford"
  }]
 }
```
