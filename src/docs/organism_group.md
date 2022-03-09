# OrganismGroup

The OrganismGroup data type contains information relating to the groups an [organism](./organism.md "Organism") is in.  These include breed, strain, cultivar, population and division. It can also identify if a related Organism is the reference for the group.


| Field                     | Type               | Description                               |
|---------------------------|--------------------|-------------------------------------------|
| code                      | string             | A code for the species group           
| type                      | string             | Type of the species group   
| name                      | string             | Name of the species group     
| organisms                 | array of [Organism](../organism.md)  | An array of related organisms belonging to the group
| is_reference_organism     | Boolean            | Indicates that the organism is the reference for a particular OrganismGroup

Note: The field `is_reference_organism` is only present if the OrganismGroup is accessed from an Organism (and therefore identifies that Organism as being one of the references for the group).  

## Examples

1. Representation of Cow showing and array of OrganismGroup (as groups) with `is_reference_organism` present. :

```json
{
  "scientific_name": "Bos taurus",
  "scientific_parlance_name": "cow",
  "id": "Bos Taurus (bos_taurus)",
  "species": {
    "scientific_name": "Bos taurus",
    "ncbi_common_name": "cattle",
    "alternative_names": ["bovine", "cow", "dairy cow", "domestic cattle", "domestic cow"],
    "taxon_id": 9913
  },
 "groups": [
 {
    "code": "hereford_breed",
    "type": "breed",
    "name": "Hereford",
    "is_reference_organism": "true",
    "organisms": [...]
  },
  {
    "code": "farmed_animals",
    "type": "population",
    "name": "Farmed Animals",
    "is_reference_organism": "false",
    "organisms": [...]
  }],
  "assemblies" : [...]
 }
```

2. Representation of an OrganismGroup showing a breed group for a Cow (note: `is_reference_organism` is not present as the OrganismGroup has been accessed directly.):

```json
{
    "code": "hereford_breed",
    "type": "breed",
    "name": "Hereford",
    "organisms":[
        {
          "scientific_name": "Bos taurus",
          "scientific_parlance_name": "cow",
          "id": "Bos Taurus (bos_taurus)",
          "groups": [...],
          "assemblies" : [...],
          "is_reference_organism": "true",
          "species": {
            "scientific_name": "Bos taurus",
            "ncbi_common_name": "cattle",
            "alternative_names": ["bovine", "cow", "dairy cow", "domestic cattle", "domestic cow"],
            "taxon_id": 9913
         }},
        {...}]
  }

```
