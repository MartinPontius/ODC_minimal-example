## General:

This repository provides a minimal example for testing [Open Data Cube (ODC)](https://www.opendatacube.org/), specifically indexing products/datasets and loading them in a Jupyter Notebook via [datacube](https://github.com/opendatacube/datacube-core).

It should help, e.g., to
- check how nodata values are handled
- check how scaling/offset is applied when unpacking netCDF
- check dimensions of the loaded netCDF
- ...

## Preparation

To use this minimal example, Open Data Cube has to be installed. This includes installing the necessary Python libraries and setting up the (PostgreSQL) database. For details check the official documentation: https://opendatacube.readthedocs.io/en/latest/installation/index.html

Note: Steps are documented for Ubuntu 22.04.2 LTS. Different steps might be necessary on different systems.

### Python environment

Install required system libraries (needed to install the Python package `psycopg2` which is a dependency of `datacube`):
```
sudo apt-get install libpq-dev
```

Create virtual environment:
```
python3 -m venv venv-odc-minimal-example
```

Activate virtual environment:
```
. venv-odc-minimal-example/bin/activate
```

Install Python packages:
```
python -m pip install -r requirements.txt
```

### Database

Reference: https://opendatacube.readthedocs.io/en/latest/installation/database/setup.html

Create database configuration file, `~/.datacube.conf`
```
[datacube]

db_database: opendatacube
db_hostname: localhost
db_port: 5432
db_username: opendatacube
db_password: opendatacube
```

Start database using Docker:
```
docker compose up -d
```

Create database schema:
```
datacube -v system init
```

Check system:
```
datacube system check
```

## How to use

(Be sure the conda environment or virtual environement is active if you use any.)

1. Start Jupyter and open the notebook `ODC_minimal-example.ipynb`
2. Run the sections "Create dataset" and "Save dataset to disk"
3. Run the section "Load dataset from disk" to check if the file was created correctly
4. Add products/datasets to the ODC index (metadata is inserted in the database). Run the following commands in the terminal:
   - for eo metadata type:
      - `datacube product add metadata/ODC_eo-product_minimal-example.yaml`
      - `datacube dataset add metadata/ODC_eo-dataset_minimal-example.yaml`
   - for eo3 metadata type:
      - `datacube product add metadata/ODC_eo3-product_minimal-example.yaml`
      - `datacube dataset add metadata/ODC_eo3-dataset_minimal-example.yaml`
5. Run the section "Load dataset from Open Data Cube" to load the added data from the datacube

