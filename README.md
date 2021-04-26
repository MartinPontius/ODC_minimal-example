General:

This gist provides a minimal example for testing Open Data Cube (ODC), specifically indexing products/datasets and loading them in a Jupyter Notebook via datacube.

It should help to
- check how nodata values are handled
- check how scaling/offset is applied when unpacking netCDF
- check dimensions of the loaded netCDF
- ...

Requirements:

To use this minimal example, Open Data Cube has to be installed. This includes installing the necessary Python libraries and setting up the (PostgreSQL) database.

- libraries: https://opendatacube.readthedocs.io/en/latest/ops/install.html
- database: https://opendatacube.readthedocs.io/en/latest/ops/db_setup.html

How to use:

(Be sure the conda environment or virtual environement is active if you use any.)

After preparations are made, products/datasets have to be added to the index:

- for eo metadata type:
   - datacube product add ODC_eo-product_minimal-example.yaml
   - datacube dataset add ODC_eo-dataset_minimal-example.yaml
- for eo3 metadata type:
   - datacube product add ODC_eo3-product_minimal-example.yaml
   - datacube dataset add ODC_eo3-dataset_minimal-example.yaml

Afterwards, run the Jupyter Notebook.
