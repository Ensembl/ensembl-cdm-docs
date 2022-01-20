# Organism

The Organism data type contains information sufficient to describe a given specific instance of a species (such as a breed or strain). It consists of the following fields:

| Field                     | Type                    | Description                               | 
|---------------------------|-------------------------|-------------------------------------------|
| scientific_name           | string                  | Scientific name of the species.           
| scientific_parlance_name  | string or null          | Preferred name for the organism within the scientific domain.
| species                   | Species                 | The related NCBI species
| groups                    | array of OrganismGroup  | An array of OrganismGroups to provide additional information about the organism       


# OrganismGroup

The OrganismGroup data type contains information relating to the organism, including breed, strain, cultivar, division:

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
  "scientific_parlance_name": "cow",
  "species": {
    "scientific_name": "Bos taurus",
    "ncbi_common_name": "cattle",
    "alternative_names": ["bovine", "cow", "dairy cow", "domestic cattle", "domestic cow"],
    "taxon_id": 9913
  },
 "groups": [{
    "id": "hereford_breed",
    "type": "breed",
    "name": "Hereford"
  }]
 }
```

2. Escherichia coli — notice that the scientific_parlance_name field can now contain Ensembl's preferred abbreviated name

```json
{
  "scientific_name": "Escherichia coli str. K-12 substr. MG1655",
  "scientific_parlance_name": "E. coli K-12",
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
  "species": {
    "scientific_name": "Trypanosoma rangeli SC58",
    "ncbi_common_name": null, 
    "alternative_names": [],
    "taxon_id": 429131
  }
}
```

