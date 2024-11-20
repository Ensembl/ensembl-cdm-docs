# Publication

| Field          | Type            | Description             |
|----------------|-----------------|-------------------------|
| authors        | array of string | Authors of publication  |            
| year           | string          |         YYYY            |
| pubmed_id      | ExternalReference      |  PubMed citation        | 
| pmc_id         | ExternalReference      |  EuropePMC citation     |
| doi            | ExternalReference      |  DOI citation           |
| ucsc_id        | ExteralReference       |  UCSC citation          |


## Examples
```json
{
   "authors": ["Farragher TM", "Plant D, Flynn E"],
   "year": "2007",
   "pubmed_id": {
      "accession_id": "18035074",
      "name": "Association of polymorphisms in platelet and hemostasis system genes with acute myocardial infarction",
      "description": null,
      "url": "https://pubmed.ncbi.nlm.nih.gov/18035074/",
      "source": {
         "id": "PubMed",
         "name": "PubMed",
         "description": "",
         "url": "https://pubmed.ncbi.nlm.nih.gov",
         "release": "",
      }
    } ,
   "pmc_id": {
      "accession_id": "PMC4031914",
      "name": "Association of polymorphisms in platelet and hemostasis system genes with acute myocardial infarction",
      "description": null,
      "url": "https://pmc.ncbi.nlm.nih.gov/articles/PMC4031914/",
      "source": {
         "id": "PMC",
         "name": "PMC",
         "description": "",
         "url": "https://pmc.ncbi.nlm.nih.gov",
         "release": "",
      }
    },
   "doi": {
      "accession_id": "10.1016/j.ahj.2007.05.021",
      "name": "Association of polymorphisms in platelet and hemostasis system genes with acute myocardial infarction",
      "description": null,
      "url": "https://doi.org/10.1016/j.ahj.2007.05.021",
      "source": {
         "id": "DOI",
         "name": "DOI",
         "description": "",
         "url": "https://www.sciencedirect.com",
         "release": "",
      }
   },
   "ucsc_id": {
      "accession_id": "ELSS0002870307005753",
      "name": "Association of polymorphisms in platelet and hemostasis system genes with acute myocardial infarction",
      "description": null,
      "url": null,
      "source": {
         "id": "",
         "name": "",
         "description": "",
         "url": "",
         "release": "",
      }
   }
}
```
