# Data Resources for Analyzing US Bank Regulatory Data

## Federal Reserve Attribute Transaction File (until 2019)
Location: [`attributes/all_attributes_until_20191231.tar.xz`](https://github.com/call-report/data-resources/raw/main/attributes/all_attributes_until_20191231.tar.xz)

### How to extract

Using MacOS or Linux, the file, which is a compress CSV, may be extracted via the terminal command: `tar xvJf all_attributes_until_20191231.tar.xz`

### About

This file was obtained via a FOIA request to the Federal Reserve; data contained therein comprise a CSV file with all structural "transactions" received by the Federal Reserve from regulated institutions. 

#### Data Dictionary

The official data dictionary for the attributess file is located in PDF format [here](https://www.ffiec.gov/nicpubweb/content/DataDownload/NPW%20Data%20Dictionary.pdf).

An edited CSV-version of the data contained in the above PDF is provded as a resource in this repository: [`attributes/attributes_file_data_dictionary.csv`](https://github.com/call-report/data-resources/raw/main/attributes/attributes_file_data_dictionary.csv)

An edited CSV-version that expands the enumerated values contained within the data dictionary is also provided as a resource in within this respository: [`attributes/attribute_value_expansion.csv`](https://github.com/call-report/data-resources/raw/main/attributes/attribute_value_expansion.csv)

