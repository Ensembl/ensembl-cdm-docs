# AnalysisMethod
Analysis method is to group relevant items for running a program

| Field             | Type                | Description
|-------------------|---------------------|---------------------
| tool              | string              | Program name eg PolyPhen-2
| version           | string              | Version of program
| qualifier         | string or null      | Mode of use/ type of result eg HumVar or HumDiv for Polyhen-2, raw or PRED style for CADD
| reference_data    | array of ExternalDB | Reference data used in running the tool

## Example
```json
{
"tool": "PolyPhen-2",
"version": "2.2.3",
"qualifier": "HumVar",
"reference_data": [
    {
    "id": "Uniref90",
    "name": "Uniref90",
    "description": null,
    "url": null,
    "release": null
    }
]
}
``` 

```json
{
"tool": "PolyPhen-2",
"version": "2.2.3",
"qualifier": "HumVar",
"reference_data": [
    {
    "id": "Uniref90",
    "name": "Uniref90",
    "description": null,
    "url": null,
    "release": null
    }
]
}
```

### Example for tool giving multiple prediction result
```json
{
    "prediction_results": [
        {
        "score": 0.83,
        "analysis_method": {       
                    "tool": "SpliceAI",  
                    "version":  "1.3.1",
                    "qualifier": "delta score acceptor loss",
                    "reference_data": "Masked scores ( Ensembl GENCODE v24 canonical)"
                    }
        },
        {
        "score": 0.83,
        "analysis_method": { 
            "tool": "SpliceAI",      
            "version": "1.3.1",  
            "qualifier": "position acceptor loss",     
            "reference_data": "Raw scores ( Ensembl GENCODE v24 canonical)"     
        }
        }
    ]

}


```
