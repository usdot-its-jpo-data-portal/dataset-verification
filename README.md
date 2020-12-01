# Dataset Verification

Compares available datasets against a list of expected datasets and display the findings/differences in the standard output.

The main target of this tool are developers and administrators who require data validation.

# Prerequisites
This is a python 3+ application and requires that requirements are installed  to be executed.

Once the repository is cloned then create a python virtual environment

```bash
virtualenv --python=python3 ./venv
```

Activate the virtual environment using the following command:
```bash
source ./venv/bin activate
```

Once the virtual environment is active, install the application prerequisites
```bash
pip install -r requirements.txt
```

# Usage
The application uses a set of inputs that can be passed as command line arguments or environment variables. 

- **DHDV_CONFIG**: Configuration file in JSON format that contains the connection information to the datasources.
    - Required: Mandatory
    ```bash
    export DHDV_CONFIG=config.json
    ```

- **DHDV_DATASET**: Dataset name.
    - Options: all, dtg, ntl, scgc
    - Required: Mandatory
    ```bash
    export DHDV_DATASET=all
    ```


- **DHDV_LIST**: Option to display the dataset
    - Default: False
    - Required: Optional
    ```bash
    export DHDV_LIST=False
    ```

- **DHDV_JSON**: Format the display of the dataset into JSON
    - This option needs to be used together with DHDV_LIST=True
    - Default: False
    - Required: Optional
    ```bash
    export DHDV_JSON=False
    ```

- **DHDV_SAVE**: Saves the return of the list or the comparison into a text file.
    - Default: False
    - Required: Optional
    ```bash
    export DHDV_SAVE=False
    ```

- **DHDV_EXPECTED**: Document in JSON format that contains the expected return of the datasets
    - This document can be generated using:
      - DHDV_LIST=True
      - DHDV_JSON=True
      - DHDV_SAVE=True
    ```bash
    export DHDV_EXPECTED=expected-datasets-api.json
    ```
    - Couple of JSON documents were provided as example of the expected document format.
        - expected-datasets-api.json
        - expected-datasets-doc.json

- **DHDV_S3_BUCKET_NAME**: S3 Bucket Name
    - This will be used in case that the application is running in AWS-Lambda
    ```bash
    export DHDV_S3_BUCKET_NAME=usdot-its-datahub-dataset-verification
    ```

- **DHDV_S3_PATH**: S3 Path Name
    - Path/folder under the Bucket name
    ```bash
    export DHDV_S3_PATH=logs/
    ```

## Building
The application is using Python and doesn't required build, however the requirements should be installed previous to be executed.

## Execution
In case the application is execute in a non AWS lambda function environment it is recommended to update the file **dh-verification.sh** with the required values for the different configuration attributes and then execute the following command.
```bash
sh dh-verification.sh
```

If the environment variables are already set then execute

```bash
python dh-verification.py
```

To execute this application in AWS-Lambda environment, then deploy the application and set the environment variables previous to the lambda execution.

# Version History and Retention
Initial version: 1.0

**Status:** This project is in the release phase.

**Release Frequency:** This project is updated on demand

**Retention:** This project will remain publicly accessible for a minimum of five years (until at least 06/15/2025).

# License
This project is licensed under the Apache License 2.0 License - see the [License.MD](https://github.com/usdot-its-jpo-data-portal/dataset-verification/blob/main/LICENSE) for more details. 

# Contact Information

Contact Name: ITS JPO

Contact Information: data.itsjpo@dot.gov

# Acknowledgements

To track how this government-funded code is used, we request that if you decide to build additional software using this code please acknowledge its Digital Object Identifier in your software's README/documentation.

Digital Object Identifier: 
