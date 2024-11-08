# Publication

| Field          | Type            | Description             |
|----------------|-----------------|-------------------------|
| authors        | array of string | Authors of publication  |            
| year           | string          |         YYYY            |
| pubmed_id           | ExternalDB      |  PubMed citation        | 
| pmc_id          | ExternalDB      |  EuropePMC citation     |
| doi            | ExternalDB      |  DOI citation           |
| ucsc_id        | ExteralDB       |  UCSC citation          |


## Examples
```json
{
   "authors": ["Farragher TM", "Plant D, Flynn E"],
   "year": "2007",
   "pubmed_id": {
      "id": "18035074",
      "name": "Association of polymorphisms in platelet and hemostasis system genes with acute myocardial infarction",
      "description": null,
      "url": "https://pubmed.ncbi.nlm.nih.gov/18035074/",
      "release": null
    } ,
   "pmc_id": {
      "id": "PMC4031914",
      "name": "Association of polymorphisms in platelet and hemostasis system genes with acute myocardial infarction",
      "description": null,
      "url": "https://pmc.ncbi.nlm.nih.gov/articles/PMC4031914/",
      "release": null
    },
   "doi": {
      "id": "10.1016/j.ahj.2007.05.021",
      "name": "Association of polymorphisms in platelet and hemostasis system genes with acute myocardial infarction",
      "description": null,
      "url": "https://doi.org/10.1016/j.ahj.2007.05.021",
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
