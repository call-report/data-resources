# Data Resources for Analyzing US Bank Regulatory Data

## Federal Reserve Attribute File (until 2019)
Location: [`attributes/all_attributes_until_20191231.tar.xz`](https://github.com/call-report/data-resources/raw/main/attributes/all_attributes_until_20191231.tar.xz)

### How to extract

Using MacOS or Linux, the file, which is a compress CSV, may be extracted via the terminal command: `tar xvJf all_attributes_until_20191231.tar.xz`

### About

This file was obtained via a FOIA request to the Federal Reserve; data contained therein comprise a CSV file with all structural "changes" received by the Federal Reserve from regulated institutions. 


This contents of this file differ from the daily data `ATTRIBUTES` data releases from the FFIEC; the FFIEC data releases comprise the latest day's snapshot of the Federal Reserve's internal ATTRIBUTES data table. The file included in this repo is the actual source data table, with all original data until 12/31/2019.

#### Data Dictionary

The official data dictionary for the attributess file is located in PDF format [here](https://www.ffiec.gov/nicpubweb/content/DataDownload/NPW%20Data%20Dictionary.pdf).

An edited CSV-version of the data contained in the above PDF is provded as a resource in this repository: [`attributes/attributes_file_data_dictionary.csv`](https://github.com/call-report/data-resources/raw/main/attributes/attributes_file_data_dictionary.csv)

An edited CSV-version that expands the enumerated values contained within the data dictionary is also provided as a resource in within this respository: [`attributes/attribute_value_expansion.csv`](https://github.com/call-report/data-resources/raw/main/attributes/attribute_value_expansion.csv)

## Machine-Readable Version of UBPR Technical Manual

### About

For each revision of the Universal Bank Performance Report (UBPR), a new technical manual is produced by the FFIEC. The UBPR data is delivered as either "bulk data" downloads or the "webservice" data acquisition service.

Although the FFIEC provides a data dictionary to describe all available public data time series, this generalized data dictionary does not contain the metadata needed for useful analysis and review of UBPR data.

Because the "data" provided is in the technical manual is PDF format and not a machine-readable format (such as JSON or CSV). Data contained within a PDF file is, of course, not helpful when 

### Updates

UBPR technical data are updated typically once a quarter; as of the last update of this README file, the latest version is `v129`. 

__Important Note__: The script generating this file is in "pre-release" status, and may be updated before reaching release status. As a result of changes to the underlying code, the schema of the output code may also change.

### Source Code

The (python-based) source code utilized to generate the JSON file from the PDF is located in the [`call-report/scripts-toolkit`](https://github.com/call-report/ubpr_technical_manual_parser)

### Data Dictionary

The JSON file contains a list of dictionary-type objects. An example of one of these objects is provided here:

```
  {
    "page_name": "Derivative Analysis--Page 5B",
    "is_referenced_concepts": true,
    "mdrm": "UBPRD307",
    "description": "Loan and Lease Loss Allowance Plus Allocated Transfer Risk Reserve for Large Reporters",
    "formula": "IF(uc: UBPR9999 [P0] > '2001-01-01' AND uc: UBPRC752 [P0] = 31,uc: UBPRD661 [P0],IF(uc: UBPR9999 [P0] > '2001-01-01' AND uc: UBPRC752 [P0] = 41 AND IN(uc: UBPR9565 [P0],'2001','2002'),uc: UBPRD661 [P0],NULL))"
  },
```

- __`page_name`__ (string): The number and title of the printed page on which the respective data point may be found.
- __`is_referenced_concepts`__ (boolean): Boolean indicating if the data point is a component of another data point (`true`) or is the "top-level" data point published in the UBPR.
- __`mdrm`__ (string): The ID of the time series, referred to as as an "MDRM" by the Federal REserve
- __`description`__ (string): The description of the time series, as provided in the technical manual.
- __`formula`__: If applicable, the formula utilized to calculate the UBPR data point.
- __`narrative`__: The narrative accompanying the time series, as provided in the technical manual.