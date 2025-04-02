# AnalysisMethod
Analysis method is to group relevant items for running a program

| Field             | Type                | Description
|-------------------|---------------------|---------------------
| tool              | string              | Program name eg PolyPhen-2
| version           | string              | Version of program
| qualifier         | AnalysisMethodQualifier or null | Additional data for using the tool
| reference_data    | array of ExternalDB or [] | Reference data used in running the tool

# AnalysisMethodQualifier 
Analysis method qualifier include the type of result and the modes of running a program
| Field             | Type                | Description
|-------------------|---------------------|---------------------
| result_type       | string  or null           | Type of result
| modes              | array of string or []      | Modes of use, eg HumVar or HumDiv for Polyhen-2, raw or PHRED style for CADD


## Example
```json
{
"tool": "PolyPhen-2",
"version": "2.2.3",
"qualifier": 
    {
    "modes": ["HumVar"]
    }
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
                    "qualifier": {
                        "result_type": "delta score acceptor loss", 
                        "modes": ["masked scores"]
                    }
                    "reference_data": 
                    {
                    "id": "Ensembl_GENCODE_v24_canonical",
                    "name": "Ensembl GENCODE v24 canonical",
                    "description": null,
                    "url": null,
                    "release": null
                    }
                    }
        },
        {
        "score": 43,
        "analysis_method": { 
            "tool": "SpliceAI",      
            "version": "1.3.1",  
            "qualifier": {
                        "result_type": "position acceptor loss", 
                        "modes": ["masked scores"]
                    }  
            "reference_data": 
                {
                "id": "Ensembl_GENCODE_v24_canonical",
                "name": "Ensembl GENCODE v24 canonical",
                "description": null,
                "url": null,
                "release": null
                }
        }
        }
    ]

}


```
