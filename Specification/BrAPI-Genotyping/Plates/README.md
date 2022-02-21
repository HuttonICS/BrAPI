
# Group Plates

API methods for tracking/managing Plates which contain samples and related meta-data. A 'Plate' is usually a plastic tray full of samples, or a collection of test tubes grouped together.





### Get - /plates [GET /brapi/v2/plates{?sampleDbId}{?sampleName}{?sampleGroupDbId}{?observationUnitDbId}{?plateDbId}{?plateName}{?germplasmDbId}{?studyDbId}{?trialDbId}{?commonCropName}{?programDbId}{?externalReferenceID}{?externalReferenceId}{?externalReferenceSource}{?page}{?pageSize}]

Get a filtered list of Plates. Each Plate is a collection of samples that are physically grouped together.



**Response Fields** 

|Field|Type|Description|
|---|---|---| 
|data|array[object]||
|additionalInfo|object|Additional arbitrary info|
|externalReferences|array[object]|An array of external reference ids. These are references to this piece of data in an external system. Could be a simple string or a URI.|
|referenceID|string|**Deprecated in v2.1** Please use `referenceId`. Github issue number #460   The external reference ID. Could be a simple string or a URI.|
|referenceId|string|The external reference ID. Could be a simple string or a URI.|
|referenceSource|string|An identifier for the source system or database of this reference|
|plateBarcode|string|A unique identifier physically attached to the plate|
|plateDbId|string|The ID which uniquely identifies a plate|
|plateFormat|string|Enum for plate formats, usually "PLATE_96" for a 96 well plate or "TUBES" for plateless format|
|plateName|string|A human readable name for a plate|
|programDbId|string|The ID which uniquely identifies a program within the given database server|
|sampleType|string|The type of samples taken. ex. 'DNA', 'RNA', 'Tissue', etc|
|studyDbId|string|The ID which uniquely identifies a study within the given database server|
|trialDbId|string|The ID which uniquely identifies a trial within the given database server|


 

+ Parameters
    + sampleDbId (Optional, ) ... The unique identifier for a Sample
    + sampleName (Optional, ) ... The human readable name of the sample
    + sampleGroupDbId (Optional, ) ... The unique identifier for a group of related Samples
    + observationUnitDbId (Optional, ) ... The ID which uniquely identifies an observation unit
    + plateDbId (Optional, ) ... The ID which uniquely identifies a plate of samples
    + plateName (Optional, ) ... The human readable name of a plate of samples
    + germplasmDbId (Optional, ) ... The ID which uniquely identifies a germplasm
    + studyDbId (Optional, ) ... The ID which uniquely identifies a study
    + trialDbId (Optional, ) ... The ID which uniquely identifies a trial
    + commonCropName (Optional, ) ... The BrAPI Common Crop Name is the simple, generalized, widely accepted name of the organism being researched. It is most often used in multi-crop systems where digital resources need to be divided at a high level. Things like 'Maize', 'Wheat', and 'Rice' are examples of common crop names.Use this parameter to only return results associated with the given crop. Use `GET /commoncropnames` to find the list of available crops on a server.
    + programDbId (Optional, ) ... A BrAPI Program represents the high level organization or group who is responsible for conducting trials and studies. Things like Breeding Programs and Funded Projects are considered BrAPI Programs. Use this parameter to only return results associated with the given program. Use `GET /programs` to find the list of available programs on a server.
    + externalReferenceID (Optional, ) ... **Deprecated in v2.1** Please use `externalReferenceId`. Github issue number #460 An external reference ID. Could be a simple string or a URI. (use with `externalReferenceSource` parameter)
    + externalReferenceId (Optional, ) ... An external reference ID. Could be a simple string or a URI. (use with `externalReferenceSource` parameter)
    + externalReferenceSource (Optional, ) ... An identifier for the source system or database of an external reference (use with `externalReferenceId` parameter)
    + page (Optional, ) ... Used to request a specific page of data to be returned.The page indexing starts at 0 (the first page is 'page'= 0). Default is `0`.
    + pageSize (Optional, ) ... The size of the pages to be returned. Default is `1000`.
    + Authorization (Optional, ) ... HTTP HEADER - Token used for Authorization <strong> Bearer {token_string} </strong>




+ Response 200 (application/json)
```
{
    "@context": [
        "https://brapi.org/jsonld/context/metadata.jsonld"
    ],
    "metadata": {
        "datafiles": [],
        "pagination": {
            "currentPage": 0,
            "pageSize": 1000,
            "totalCount": 10,
            "totalPages": 1
        },
        "status": [
            {
                "message": "Request accepted, response successful",
                "messageType": "INFO"
            }
        ]
    },
    "result": {
        "data": [
            {
                "additionalInfo": {},
                "externalReferences": [
                    {
                        "referenceId": "doi:10.155454/12341234",
                        "referenceSource": "DOI"
                    },
                    {
                        "referenceId": "75a50e76",
                        "referenceSource": "Remote Data Collection Upload Tool"
                    }
                ],
                "plateBarcode": "11223344",
                "plateDbId": "a106467f",
                "plateFormat": "PLATE_96",
                "plateName": "Plate_123_XYZ",
                "programDbId": "bd748e00",
                "sampleType": "TISSUE",
                "studyDbId": "64bd6bf9",
                "trialDbId": "d34c5349"
            }
        ]
    }
}
```

+ Response 400 (application/json)
```
"ERROR - 2018-10-08T18:15:11Z - Malformed JSON Request Object\n\nERROR - 2018-10-08T18:15:11Z - Invalid query parameter\n\nERROR - 2018-10-08T18:15:11Z - Required parameter is missing"
```

+ Response 401 (application/json)
```
"ERROR - 2018-10-08T18:15:11Z - Missing or expired authorization token"
```

+ Response 403 (application/json)
```
"ERROR - 2018-10-08T18:15:11Z - User does not have permission to perform this action"
```




### Post - /plates [POST /brapi/v2/plates]

Submit new Plate entities to the server

**Request Fields** 

|Field|Type|Description|
|---|---|---| 
|additionalInfo|object|Additional arbitrary info|
|externalReferences|array[object]|An array of external reference ids. These are references to this piece of data in an external system. Could be a simple string or a URI.|
|referenceID|string|**Deprecated in v2.1** Please use `referenceId`. Github issue number #460   The external reference ID. Could be a simple string or a URI.|
|referenceId|string|The external reference ID. Could be a simple string or a URI.|
|referenceSource|string|An identifier for the source system or database of this reference|
|plateBarcode|string|A unique identifier physically attached to the plate|
|plateFormat|string|Enum for plate formats, usually "PLATE_96" for a 96 well plate or "TUBES" for plateless format|
|plateName|string|A human readable name for a plate|
|programDbId|string|The ID which uniquely identifies a program within the given database server|
|sampleType|string|The type of samples taken. ex. 'DNA', 'RNA', 'Tissue', etc|
|studyDbId|string|The ID which uniquely identifies a study within the given database server|
|trialDbId|string|The ID which uniquely identifies a trial within the given database server|


**Response Fields** 

|Field|Type|Description|
|---|---|---| 
|data|array[object]||
|additionalInfo|object|Additional arbitrary info|
|externalReferences|array[object]|An array of external reference ids. These are references to this piece of data in an external system. Could be a simple string or a URI.|
|referenceID|string|**Deprecated in v2.1** Please use `referenceId`. Github issue number #460   The external reference ID. Could be a simple string or a URI.|
|referenceId|string|The external reference ID. Could be a simple string or a URI.|
|referenceSource|string|An identifier for the source system or database of this reference|
|plateBarcode|string|A unique identifier physically attached to the plate|
|plateDbId|string|The ID which uniquely identifies a plate|
|plateFormat|string|Enum for plate formats, usually "PLATE_96" for a 96 well plate or "TUBES" for plateless format|
|plateName|string|A human readable name for a plate|
|programDbId|string|The ID which uniquely identifies a program within the given database server|
|sampleType|string|The type of samples taken. ex. 'DNA', 'RNA', 'Tissue', etc|
|studyDbId|string|The ID which uniquely identifies a study within the given database server|
|trialDbId|string|The ID which uniquely identifies a trial within the given database server|


 

+ Parameters
    + Authorization (Optional, ) ... HTTP HEADER - Token used for Authorization <strong> Bearer {token_string} </strong>


 
+ Request (application/json)
```
[
    {
        "additionalInfo": {},
        "externalReferences": [
            {
                "referenceId": "doi:10.155454/12341234",
                "referenceSource": "DOI"
            },
            {
                "referenceId": "75a50e76",
                "referenceSource": "Remote Data Collection Upload Tool"
            }
        ],
        "plateBarcode": "11223344",
        "plateFormat": "PLATE_96",
        "plateName": "Plate_123_XYZ",
        "programDbId": "bd748e00",
        "sampleType": "TISSUE",
        "studyDbId": "64bd6bf9",
        "trialDbId": "d34c5349"
    }
]
```



+ Response 200 (application/json)
```
{
    "@context": [
        "https://brapi.org/jsonld/context/metadata.jsonld"
    ],
    "metadata": {
        "datafiles": [],
        "pagination": {
            "currentPage": 0,
            "pageSize": 1000,
            "totalCount": 10,
            "totalPages": 1
        },
        "status": [
            {
                "message": "Request accepted, response successful",
                "messageType": "INFO"
            }
        ]
    },
    "result": {
        "data": [
            {
                "additionalInfo": {},
                "externalReferences": [
                    {
                        "referenceId": "doi:10.155454/12341234",
                        "referenceSource": "DOI"
                    },
                    {
                        "referenceId": "75a50e76",
                        "referenceSource": "Remote Data Collection Upload Tool"
                    }
                ],
                "plateBarcode": "11223344",
                "plateDbId": "a106467f",
                "plateFormat": "PLATE_96",
                "plateName": "Plate_123_XYZ",
                "programDbId": "bd748e00",
                "sampleType": "TISSUE",
                "studyDbId": "64bd6bf9",
                "trialDbId": "d34c5349"
            }
        ]
    }
}
```

+ Response 400 (application/json)
```
"ERROR - 2018-10-08T18:15:11Z - Malformed JSON Request Object\n\nERROR - 2018-10-08T18:15:11Z - Invalid query parameter\n\nERROR - 2018-10-08T18:15:11Z - Required parameter is missing"
```

+ Response 401 (application/json)
```
"ERROR - 2018-10-08T18:15:11Z - Missing or expired authorization token"
```

+ Response 403 (application/json)
```
"ERROR - 2018-10-08T18:15:11Z - User does not have permission to perform this action"
```




### Put - /plates [PUT /brapi/v2/plates/]

Update the details of existing Plates

**Request Fields** 

|Field|Type|Description|
|---|---|---| 


**Response Fields** 

|Field|Type|Description|
|---|---|---| 
|data|array[object]||
|additionalInfo|object|Additional arbitrary info|
|externalReferences|array[object]|An array of external reference ids. These are references to this piece of data in an external system. Could be a simple string or a URI.|
|referenceID|string|**Deprecated in v2.1** Please use `referenceId`. Github issue number #460   The external reference ID. Could be a simple string or a URI.|
|referenceId|string|The external reference ID. Could be a simple string or a URI.|
|referenceSource|string|An identifier for the source system or database of this reference|
|plateBarcode|string|A unique identifier physically attached to the plate|
|plateDbId|string|The ID which uniquely identifies a plate|
|plateFormat|string|Enum for plate formats, usually "PLATE_96" for a 96 well plate or "TUBES" for plateless format|
|plateName|string|A human readable name for a plate|
|programDbId|string|The ID which uniquely identifies a program within the given database server|
|sampleType|string|The type of samples taken. ex. 'DNA', 'RNA', 'Tissue', etc|
|studyDbId|string|The ID which uniquely identifies a study within the given database server|
|trialDbId|string|The ID which uniquely identifies a trial within the given database server|


 

+ Parameters
    + Authorization (Optional, ) ... HTTP HEADER - Token used for Authorization <strong> Bearer {token_string} </strong>


 
+ Request (application/json)
```
{
    "<plateDbId_1>": {
        "additionalInfo": {},
        "externalReferences": [],
        "plateBarcode": "3a027b59",
        "plateFormat": "PLATE_96",
        "plateName": "Plate_alpha_20191022",
        "programDbId": "bd748e00",
        "sampleType": "Tissue",
        "studyDbId": "64bd6bf9",
        "trialDbId": "d34c5349"
    },
    "<plateDbId_2>": {
        "additionalInfo": {},
        "externalReferences": [],
        "plateBarcode": "27b593a0",
        "plateFormat": "PLATE_96",
        "plateName": "Plate_alpha_20191022",
        "programDbId": "bd748e00",
        "sampleType": "Tissue",
        "studyDbId": "64bd6bf9",
        "trialDbId": "d34c5349"
    }
}
```



+ Response 200 (application/json)
```
{
    "@context": [
        "https://brapi.org/jsonld/context/metadata.jsonld"
    ],
    "metadata": {
        "datafiles": [],
        "pagination": {
            "currentPage": 0,
            "pageSize": 1000,
            "totalCount": 10,
            "totalPages": 1
        },
        "status": [
            {
                "message": "Request accepted, response successful",
                "messageType": "INFO"
            }
        ]
    },
    "result": {
        "data": [
            {
                "additionalInfo": {},
                "externalReferences": [
                    {
                        "referenceId": "doi:10.155454/12341234",
                        "referenceSource": "DOI"
                    },
                    {
                        "referenceId": "75a50e76",
                        "referenceSource": "Remote Data Collection Upload Tool"
                    }
                ],
                "plateBarcode": "11223344",
                "plateDbId": "a106467f",
                "plateFormat": "PLATE_96",
                "plateName": "Plate_123_XYZ",
                "programDbId": "bd748e00",
                "sampleType": "TISSUE",
                "studyDbId": "64bd6bf9",
                "trialDbId": "d34c5349"
            }
        ]
    }
}
```

+ Response 400 (application/json)
```
"ERROR - 2018-10-08T18:15:11Z - Malformed JSON Request Object\n\nERROR - 2018-10-08T18:15:11Z - Invalid query parameter\n\nERROR - 2018-10-08T18:15:11Z - Required parameter is missing"
```

+ Response 401 (application/json)
```
"ERROR - 2018-10-08T18:15:11Z - Missing or expired authorization token"
```

+ Response 403 (application/json)
```
"ERROR - 2018-10-08T18:15:11Z - User does not have permission to perform this action"
```

+ Response 404 (application/json)
```
"ERROR - 2018-10-08T18:15:11Z - The requested object DbId is not found"
```




### Get - /plates/{plateDbId} [GET /brapi/v2/plates/{plateDbId}]

Get the details of a specific Plate. Each Plate is a collection of samples that are physically grouped together.



**Response Fields** 

|Field|Type|Description|
|---|---|---| 
|additionalInfo|object|Additional arbitrary info|
|externalReferences|array[object]|An array of external reference ids. These are references to this piece of data in an external system. Could be a simple string or a URI.|
|referenceID|string|**Deprecated in v2.1** Please use `referenceId`. Github issue number #460   The external reference ID. Could be a simple string or a URI.|
|referenceId|string|The external reference ID. Could be a simple string or a URI.|
|referenceSource|string|An identifier for the source system or database of this reference|
|plateBarcode|string|A unique identifier physically attached to the plate|
|plateDbId|string|The ID which uniquely identifies a plate|
|plateFormat|string|Enum for plate formats, usually "PLATE_96" for a 96 well plate or "TUBES" for plateless format|
|plateName|string|A human readable name for a plate|
|programDbId|string|The ID which uniquely identifies a program within the given database server|
|sampleType|string|The type of samples taken. ex. 'DNA', 'RNA', 'Tissue', etc|
|studyDbId|string|The ID which uniquely identifies a study within the given database server|
|trialDbId|string|The ID which uniquely identifies a trial within the given database server|


 

+ Parameters
    + plateDbId (Required, ) ... The ID which uniquely identifies a plate
    + Authorization (Optional, ) ... HTTP HEADER - Token used for Authorization <strong> Bearer {token_string} </strong>




+ Response 200 (application/json)
```
{
    "@context": [
        "https://brapi.org/jsonld/context/metadata.jsonld"
    ],
    "metadata": {
        "datafiles": [],
        "pagination": {
            "currentPage": 0,
            "pageSize": 1000,
            "totalCount": 10,
            "totalPages": 1
        },
        "status": [
            {
                "message": "Request accepted, response successful",
                "messageType": "INFO"
            }
        ]
    },
    "result": {
        "additionalInfo": {},
        "externalReferences": [
            {
                "referenceId": "doi:10.155454/12341234",
                "referenceSource": "DOI"
            },
            {
                "referenceId": "75a50e76",
                "referenceSource": "Remote Data Collection Upload Tool"
            }
        ],
        "plateBarcode": "11223344",
        "plateDbId": "a106467f",
        "plateFormat": "PLATE_96",
        "plateName": "Plate_123_XYZ",
        "programDbId": "bd748e00",
        "sampleType": "TISSUE",
        "studyDbId": "64bd6bf9",
        "trialDbId": "d34c5349"
    }
}
```

+ Response 400 (application/json)
```
"ERROR - 2018-10-08T18:15:11Z - Malformed JSON Request Object\n\nERROR - 2018-10-08T18:15:11Z - Invalid query parameter\n\nERROR - 2018-10-08T18:15:11Z - Required parameter is missing"
```

+ Response 401 (application/json)
```
"ERROR - 2018-10-08T18:15:11Z - Missing or expired authorization token"
```

+ Response 403 (application/json)
```
"ERROR - 2018-10-08T18:15:11Z - User does not have permission to perform this action"
```

+ Response 404 (application/json)
```
"ERROR - 2018-10-08T18:15:11Z - The requested object DbId is not found"
```




### Post - /search/plates [POST /brapi/v2/search/plates]

Submit a search request for `Plates`<br/>
Search requests allow a client to send a complex query for data. However, the server may not respond with the search results immediately. 
If a server needs more time to process the request, it might respond with a `searchResultsDbId`. 
Use the corresponding `GET /search/plates/{searchResultsDbId}` to retrieve the results of the search. <br/> 
Review the <a target="_blank" href="https://wiki.brapi.org/index.php/Search_Services#POST_Search_Entity">Search Services documentation</a> for additional implementation details.

**Request Fields** 

|Field|Type|Description|
|---|---|---| 
|commonCropNames|array[string]|The BrAPI Common Crop Name is the simple, generalized, widely accepted name of the organism being researched. It is most often used in multi-crop systems where digital resources need to be divided at a high level. Things like 'Maize', 'Wheat', and 'Rice' are examples of common crop names.  Use this parameter to only return results associated with the given crops.   Use `GET /commoncropnames` to find the list of available crops on a server.|
|externalReferenceIDs|array[string]|**Deprecated in v2.1** Please use `externalReferenceIds`. Github issue number #460   List of external reference IDs. Could be a simple strings or a URIs. (use with `externalReferenceSources` parameter)|
|externalReferenceIds|array[string]|List of external reference IDs. Could be a simple strings or a URIs. (use with `externalReferenceSources` parameter)|
|externalReferenceSources|array[string]|List of identifiers for the source system or database of an external reference (use with `externalReferenceIDs` parameter)|
|germplasmDbIds|array[string]|The ID which uniquely identifies a germplasm|
|germplasmNames|array[string]|List of human readable names to identify germplasm to search for|
|observationUnitDbIds|array[string]|The ID which uniquely identifies an observation unit|
|page|integer|Which result page is requested. The page indexing starts at 0 (the first page is 'page'= 0). Default is `0`.|
|pageSize|integer|The size of the pages to be returned. Default is `1000`.|
|plateBarcodes|array[string]|A unique identifier physically attached to the plate|
|plateDbIds|array[string]|The ID which uniquely identifies a plate of samples|
|plateNames|array[string]|The human readable name of a plate of samples|
|programDbIds|array[string]|A BrAPI Program represents the high level organization or group who is responsible for conducting trials and studies. Things like Breeding Programs and Funded Projects are considered BrAPI Programs.   Use this parameter to only return results associated with the given programs.   Use `GET /programs` to find the list of available programs on a server.|
|programNames|array[string]|Use this parameter to only return results associated with the given program names. Program names are not required to be unique.  Use `GET /programs` to find the list of available programs on a server.|
|sampleDbIds|array[string]|The ID which uniquely identifies a sample|
|sampleGroupDbIds|array[string]|The unique identifier for a group of related Samples|
|sampleNames|array[string]|The human readable name of the sample|
|studyDbIds|array[string]|List of study identifiers to search for|
|studyNames|array[string]|List of study names to filter search results|
|trialDbIds|array[string]|The ID which uniquely identifies a trial to search for|
|trialNames|array[string]|The human readable name of a trial to search for|


**Response Fields** 

|Field|Type|Description|
|---|---|---| 
|data|array[object]||
|additionalInfo|object|Additional arbitrary info|
|externalReferences|array[object]|An array of external reference ids. These are references to this piece of data in an external system. Could be a simple string or a URI.|
|referenceID|string|**Deprecated in v2.1** Please use `referenceId`. Github issue number #460   The external reference ID. Could be a simple string or a URI.|
|referenceId|string|The external reference ID. Could be a simple string or a URI.|
|referenceSource|string|An identifier for the source system or database of this reference|
|plateBarcode|string|A unique identifier physically attached to the plate|
|plateDbId|string|The ID which uniquely identifies a plate|
|plateFormat|string|Enum for plate formats, usually "PLATE_96" for a 96 well plate or "TUBES" for plateless format|
|plateName|string|A human readable name for a plate|
|programDbId|string|The ID which uniquely identifies a program within the given database server|
|sampleType|string|The type of samples taken. ex. 'DNA', 'RNA', 'Tissue', etc|
|studyDbId|string|The ID which uniquely identifies a study within the given database server|
|trialDbId|string|The ID which uniquely identifies a trial within the given database server|


 

+ Parameters
    + Authorization (Optional, ) ... HTTP HEADER - Token used for Authorization <strong> Bearer {token_string} </strong>


 
+ Request (application/json)
```
{
    "commonCropNames": [
        "Tomatillo",
        "Paw Paw"
    ],
    "externalReferenceIDs": [
        "doi:10.155454/12341234",
        "14a19841"
    ],
    "externalReferenceIds": [
        "doi:10.155454/12341234",
        "14a19841"
    ],
    "externalReferenceSources": [
        "DOI",
        "Field App Name"
    ],
    "germplasmDbIds": [
        "d745e1e2",
        "6dd28d74"
    ],
    "germplasmNames": [
        "A0000003",
        "A0000477"
    ],
    "observationUnitDbIds": [
        "3cd0ca36",
        "983f3b14"
    ],
    "page": 0,
    "pageSize": 1000,
    "plateBarcodes": [
        "11223344",
        "55667788"
    ],
    "plateDbIds": [
        "0cac98b8",
        "b96125fb"
    ],
    "plateNames": [
        "0cac98b8",
        "b96125fb"
    ],
    "programDbIds": [
        "8f5de35b",
        "0e2d4a13"
    ],
    "programNames": [
        "Better Breeding Program",
        "Best Breeding Program"
    ],
    "sampleDbIds": [
        "3bece2ca",
        "dd286cc6"
    ],
    "sampleGroupDbIds": [
        "45e1e2d7",
        "6cc6dd28"
    ],
    "sampleNames": [
        "SA_111",
        "SA_222"
    ],
    "studyDbIds": [
        "cf6c4bd4",
        "691e69d6"
    ],
    "studyNames": [
        "The First Bob Study 2017",
        "Wheat Yield Trial 246"
    ],
    "trialDbIds": [
        "d2593dc2",
        "9431a731"
    ],
    "trialNames": [
        "All Yield Trials 2016",
        "Disease Resistance Study Comparison Group"
    ]
}
```



+ Response 200 (application/json)
```
{
    "@context": [
        "https://brapi.org/jsonld/context/metadata.jsonld"
    ],
    "metadata": {
        "datafiles": [],
        "pagination": {
            "currentPage": 0,
            "pageSize": 1000,
            "totalCount": 10,
            "totalPages": 1
        },
        "status": [
            {
                "message": "Request accepted, response successful",
                "messageType": "INFO"
            }
        ]
    },
    "result": {
        "data": [
            {
                "additionalInfo": {},
                "externalReferences": [
                    {
                        "referenceId": "doi:10.155454/12341234",
                        "referenceSource": "DOI"
                    },
                    {
                        "referenceId": "75a50e76",
                        "referenceSource": "Remote Data Collection Upload Tool"
                    }
                ],
                "plateBarcode": "11223344",
                "plateDbId": "a106467f",
                "plateFormat": "PLATE_96",
                "plateName": "Plate_123_XYZ",
                "programDbId": "bd748e00",
                "sampleType": "TISSUE",
                "studyDbId": "64bd6bf9",
                "trialDbId": "d34c5349"
            }
        ]
    }
}
```

+ Response 202 (application/json)
```
{
    "@context": [
        "https://brapi.org/jsonld/context/metadata.jsonld"
    ],
    "metadata": {
        "datafiles": [],
        "pagination": {
            "currentPage": 0,
            "pageSize": 1000,
            "totalCount": 10,
            "totalPages": 1
        },
        "status": [
            {
                "message": "Request accepted, response successful",
                "messageType": "INFO"
            }
        ]
    },
    "result": {
        "searchResultsDbId": "551ae08c"
    }
}
```

+ Response 400 (application/json)
```
"ERROR - 2018-10-08T18:15:11Z - Malformed JSON Request Object\n\nERROR - 2018-10-08T18:15:11Z - Invalid query parameter\n\nERROR - 2018-10-08T18:15:11Z - Required parameter is missing"
```

+ Response 401 (application/json)
```
"ERROR - 2018-10-08T18:15:11Z - Missing or expired authorization token"
```

+ Response 403 (application/json)
```
"ERROR - 2018-10-08T18:15:11Z - User does not have permission to perform this action"
```




### Get - /search/plates/{searchResultsDbId} [GET /brapi/v2/search/plates/{searchResultsDbId}{?page}{?pageSize}]

Get the results of a `Plates` search request <br/>
Clients should submit a search request using the corresponding `POST /search/plates` endpoint.
Search requests allow a client to send a complex query for data. However, the server may not respond with the search results immediately. 
If a server needs more time to process the request, it might respond with a `searchResultsDbId`. 
Use this endpoint to retrieve the results of the search. <br/> 
Review the <a target="_blank" href="https://wiki.brapi.org/index.php/Search_Services#POST_Search_Entity">Search Services documentation</a> for additional implementation details.



**Response Fields** 

|Field|Type|Description|
|---|---|---| 
|data|array[object]||
|additionalInfo|object|Additional arbitrary info|
|externalReferences|array[object]|An array of external reference ids. These are references to this piece of data in an external system. Could be a simple string or a URI.|
|referenceID|string|**Deprecated in v2.1** Please use `referenceId`. Github issue number #460   The external reference ID. Could be a simple string or a URI.|
|referenceId|string|The external reference ID. Could be a simple string or a URI.|
|referenceSource|string|An identifier for the source system or database of this reference|
|plateBarcode|string|A unique identifier physically attached to the plate|
|plateDbId|string|The ID which uniquely identifies a plate|
|plateFormat|string|Enum for plate formats, usually "PLATE_96" for a 96 well plate or "TUBES" for plateless format|
|plateName|string|A human readable name for a plate|
|programDbId|string|The ID which uniquely identifies a program within the given database server|
|sampleType|string|The type of samples taken. ex. 'DNA', 'RNA', 'Tissue', etc|
|studyDbId|string|The ID which uniquely identifies a study within the given database server|
|trialDbId|string|The ID which uniquely identifies a trial within the given database server|


 

+ Parameters
    + searchResultsDbId (Required, ) ... Unique identifier which references the search results
    + page (Optional, ) ... Used to request a specific page of data to be returned.The page indexing starts at 0 (the first page is 'page'= 0). Default is `0`.
    + pageSize (Optional, ) ... The size of the pages to be returned. Default is `1000`.
    + Authorization (Optional, ) ... HTTP HEADER - Token used for Authorization <strong> Bearer {token_string} </strong>




+ Response 200 (application/json)
```
{
    "@context": [
        "https://brapi.org/jsonld/context/metadata.jsonld"
    ],
    "metadata": {
        "datafiles": [],
        "pagination": {
            "currentPage": 0,
            "pageSize": 1000,
            "totalCount": 10,
            "totalPages": 1
        },
        "status": [
            {
                "message": "Request accepted, response successful",
                "messageType": "INFO"
            }
        ]
    },
    "result": {
        "data": [
            {
                "additionalInfo": {},
                "externalReferences": [
                    {
                        "referenceId": "doi:10.155454/12341234",
                        "referenceSource": "DOI"
                    },
                    {
                        "referenceId": "75a50e76",
                        "referenceSource": "Remote Data Collection Upload Tool"
                    }
                ],
                "plateBarcode": "11223344",
                "plateDbId": "a106467f",
                "plateFormat": "PLATE_96",
                "plateName": "Plate_123_XYZ",
                "programDbId": "bd748e00",
                "sampleType": "TISSUE",
                "studyDbId": "64bd6bf9",
                "trialDbId": "d34c5349"
            }
        ]
    }
}
```

+ Response 202 (application/json)
```
{
    "@context": [
        "https://brapi.org/jsonld/context/metadata.jsonld"
    ],
    "metadata": {
        "datafiles": [],
        "pagination": {
            "currentPage": 0,
            "pageSize": 1000,
            "totalCount": 10,
            "totalPages": 1
        },
        "status": [
            {
                "message": "Request accepted, response successful",
                "messageType": "INFO"
            }
        ]
    },
    "result": {
        "searchResultsDbId": "551ae08c"
    }
}
```

+ Response 400 (application/json)
```
"ERROR - 2018-10-08T18:15:11Z - Malformed JSON Request Object\n\nERROR - 2018-10-08T18:15:11Z - Invalid query parameter\n\nERROR - 2018-10-08T18:15:11Z - Required parameter is missing"
```

+ Response 401 (application/json)
```
"ERROR - 2018-10-08T18:15:11Z - Missing or expired authorization token"
```

+ Response 403 (application/json)
```
"ERROR - 2018-10-08T18:15:11Z - User does not have permission to perform this action"
```

+ Response 404 (application/json)
```
"ERROR - 2018-10-08T18:15:11Z - The requested object DbId is not found"
```
