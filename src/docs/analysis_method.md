# AnalysisMethod
Analysis method is to group relavant items for running a program

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
