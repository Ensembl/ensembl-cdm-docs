# Publication

| Field          | Type            | Description             |
|----------------|-----------------|-------------------------|
| authors        | array of string | Authors of publication  |            |
| year           | string          |                         |
| pmid           | ExternalDB      |  PubMed citation        | 
| pmcid          | ExternalDB      |  EuropePMC citation     |
| doi            | ExternalDB      |  DOI citation           |
| ucsc_id        | ExteralDB       |  UCSC citation          |


## Examples
```json
{
   "authors": ["Farragher TM", "Plant D, Flynn E"],
   "year": {
      "day": null,
      "month": null,
      "year": 2007,
   },
   "pmid": {
      "id": "18035074",
      "name": null,
      "description": null,
      "url": null,
      "release": null
    } ,
   "pmcid": {
      "id": "PMC4031914",
      "name": null,
      "description": null,
      "url": null,
      "release": null
    },
   "doi": {
      "id": "10.1016/j.ahj.2007.05.021",
      "name": null,
      "description": null,
      "url": null,
      "release": null
   },
   "ucsc_id": {
      "id": "ELSS0002870307005753",
      "name": null,
      "description": null,
      "url": null,
      "release": null
   }
}
```
