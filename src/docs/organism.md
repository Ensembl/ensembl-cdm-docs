# Organism

The Organism data type contains information sufficient to describe a given specific instance of a species (such as a breed or strain). It consists of the following fields:

| Field                     | Type                    | Description                               | 
|---------------------------|-------------------------|-------------------------------------------|
| scientific_name           | string                  | Scientific name of the species.           
| scientific_parlance_name  | string or null          | Preferred name for the organism within the scientific domain.
| species                   | Species                 | The related NCBI species
| id                        | string                  | A unique identifier for an organism
| groups                    | array of OrganismGroup  | An array of OrganismGroups to provide additional information about the organism
| is_reference_organism     | Boolean                 | Indicates that the organism is the reference for a particular OrganismGroup

Note: The field is_reference_organism is only present if Organism is access from an OrganismGroup.  If the Organism is referenced directly, it will not be present.


# OrganismGroup

The OrganismGroup data type contains information relating to the organism, including breed, strain, cultivar, population and division:

| Field         | Type                   | Description                               | 
|---------------|------------------------|-------------------------------------------|
| code          | string                 | A code for the species group           
| type          | string                 | Type of the species group   
| name          | string                 | Name of the species group     
| organisms     | array of Organism      | An array of related organisms



## Examples

1.a. Representation of Cow:

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
  }]
 }
```

1.b. Representation of Cow:

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


2. Escherichia coli — notice that the scientific_parlance_name field can now contain Ensembl's preferred abbreviated name

```json
{
  "scientific_name": "Escherichia coli str. K-12 substr. MG1655",
  "scientific_parlance_name": "E. coli K-12",
  "id": "E. coli (str. K-12 substr. MG1655)",
  "species": {
    "scientific_name": "Escherichia coli str. K-12 substr. MG1655",
    "ncbi_common_name": null, 
    "alternative_names": [],
    "taxon_id": 511145
  }
}
```

3. Pieris rapae (no scientific_parlance_name provided)

```json
{
  "scientific_name": "Pieris rapae",
  "scientific_parlance_name": null,
  "id": "Pieris rapae",
  "species": {
    "scientific_name": "Pieris rapae",
    "ncbi_common_name": "cabbage white", 
    "alternative_names": ["small cabbage white", "small white", "european cabbage white"],
    "taxon_id": 64459
  }
}
```

4. Trypanosoma rangeli SC58 (only scientific_name provided)

```json
{
  "scientific_name": "Trypanosoma rangeli SC58",
  "scientific_parlance_name": null,
  "id": "Trypanosoma rangeli (SC58)"
  "species": {
    "scientific_name": "Trypanosoma rangeli SC58",
    "ncbi_common_name": null, 
    "alternative_names": [],
    "taxon_id": 429131
  }
}
```

