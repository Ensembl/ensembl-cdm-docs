# Publication

| Field          | Type            | Description             |
|----------------|-----------------|-------------------------|
| authors        | array of string | Authors of publication  |            
| year           | string          |         YYYY            |
| title          | string          | Title of publication    |
| doi            | string or null        | DOI
| publication_references  | array of ExternalReference or []| Pubmed, PMC, UCSC citations

## Examples
```json
{
   "authors": [
      "Knowles JW", 
      "Wang H", 
      "Itakura H", 
      "Southwick A",
   ],
   "year": "2007",
   "title": "Association of polymorphisms in platelet and hemostasis system genes with acute myocardial infarction",
   "doi": "10.1016/j.ahj.2007.05.021",
   "publication_references": [
      {
         "accession_id": "18035074",
         "name": "Association of polymorphisms in platelet and hemostasis system genes with acute myocardial infarction",
         "description": null,
         "url": "https://pubmed.ncbi.nlm.nih.gov/18035074/",
         "source": {
               "id": "PubMed",
               "name": "PubMed",
               "description": "",
               "url": "https://pubmed.ncbi.nlm.nih.gov",
               "release": ""
         }
      },
      {
         "accession_id": "PMC4031914",
         "name": "Association of polymorphisms in platelet and hemostasis system genes with acute myocardial infarction",
         "description": null,
         "url": "https://pmc.ncbi.nlm.nih.gov/articles/PMC4031914/",
         "source": {
               "id": "PMC",
               "name": "PMC",
               "description": "",
               "url": "https://pmc.ncbi.nlm.nih.gov",
               "release": ""
         }
      },
      {
         "accession_id": "10.1016/j.ahj.2007.05.021",
         "name": "Association of polymorphisms in platelet and hemostasis system genes with acute myocardial infarction",
         "description": null,
         "url": "https://doi.org/10.1016/j.ahj.2007.05.021",
         "source": {
               "id": "DOI",
               "name": "DOI",
               "description": "",
               "url": "https://www.sciencedirect.com",
               "release": ""
         }
      },
      {
         "accession_id": "ELSS0002870307005753",
         "name": "Association of polymorphisms in platelet and hemostasis system genes with acute myocardial infarction",
         "description": null,
         "url": null,
         "source": {
               "id": "",
               "name": "",
               "description": "",
               "url": "",
               "release": ""
         }
      }
   ]
}
```
