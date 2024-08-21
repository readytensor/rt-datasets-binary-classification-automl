# AutoML Project Datasets

This repository contains files related to the datasets used for the AutoML project. There are a total of 15 benchmarking datasets used in this project. It creates 5-fold cross-validation sets for each of the 30 included datasets under the Binary Classification category.

## Datasets

The list of datasets is as follows:
| Dataset                                           | Industry                       | Observations | Features | Has Categorical Features? | Has Missing Values? |
| ------------------------------------------------- | ------------------------------ | :----------: | :------: | :-----------------------: | :-----------------: |
| Breast Cancer - Wisconsin                         | Biosciences / Healthcare       |     569      |    32    |            no             |         no          |
| Concentric Spheres Dataset                        | None (synthetic)               |    3,000     |    9     |            no             |         yes         |
| Credit Approval                                   | Financial services             |     690      |    15    |            yes            |         yes         |
| Electrical Grid Stability Simulated Data Data Set | Energy                         |    10,000    |    13    |            no             |         no          |
| Employee Attrition dataset from PyCaret           | Miscellaneous / Human Resource |    14,999    |    9     |            yes            |         no          |
| Exclusive-Or dataset                              | None (synthetic)               |    6,000     |    5     |            no             |         no          |
| Image Segmentation                                | Computer Vision                |    2,310     |    20    |            no             |         no          |
| In-vehicle coupon recommendation                  | E-commerce                     |    12,684    |    25    |            yes            |         yes         |
| Mushroom Data Set                                 | Biosciences                    |    8,124     |    22    |            yes            |         yes         |
| NBA binary classification dataset from Pycaret    | Sports                         |    1,294     |    21    |            no             |         no          |
| Online Shoppers Purchasing Intention              | E-commerce                     |    12,330    |    17    |            yes            |         no          |
| Spambase Data Set                                 | Technology / Internet Services |    4,601     |    57    |            no             |         no          |
| Spiral Dataset                                    | None (synthetic)               |     250      |    2     |            no             |         no          |
| Telco customer churn                              | Telecom                        |    7,043     |    20    |            no             |         yes         |
| Titanic Passenger Survival dataset                | Tourism / Transportation       |    1,309     |    10    |            yes            |         yes         |

## Usage

1. Clone the repository:

   ```bash
   git clone https://github.com/readytensor/rt-datasets-binary-classification.git
   cd rt-datasets-binary-classification-automl
   ```

2. Create a virtual environment and install dependencies:

   ```bash
   python3 -m venv venv
   source venv/bin/activate  # On Windows use `venv\Scripts\activate`
   pip install -r requirements.txt
   ```

3. Run the following command to generate the processed files:

   ```bash
   python src/run_all.py
   ```

   This will create the processed files in the `datasets/processed` folder. There are 5-folds created for each of the 15 datasets, resulting in 75 folders in total. Each folder contains the train, test, and test-key files (which are CSVs) along with the schema file (JSON).

## Project Structure

The project is organized as follows:

- `datasets/`: Contains the main data files and schema files for all benchmark datasets under the Binary Classification category.

  - `processed/`: Contains the processed files used in algorithm evaluations.
    - Files with suffix "\_train.csv" are used for training.
    - Files with suffix "\_test.csv" are used for testing (without the targets).
    - Files with suffix "\_test_key.csv" contain the ids and targets for the test data, used to generate scores by comparing with predictions.
    - Files with suffix "\_schema.json" are the schema files for the corresponding datasets.
  - `raw/`: Contains the original data files from the source.

- `src/`: Contains the source code for processing the datasets.
  - `config/`: Contains two CSV files:
    - `binary_classification_datasets_metadata.csv`: Contains dataset-level attribute information.
    - `binary_classification_datasets_fields.csv`: Contains information about all fields in each dataset.
  - `raw_datasets_processing.py`: Code to read and preprocess the original source data into the required pandas dataframe format.
  - `schema_gen.py`: Code to generate the schema files for each dataset.
  - `train_test_key_files_gen.py`: Code to save the train, test, and test-key files for each dataset.
  - `run_all.py`: Main script that uses functions in the above three scripts to generate processed dataset files.

Note that the main files for all datasets are located in the `./datasets/processed` folder.

## License

The code in this repository is licensed under the MIT License. See the LICENSE file for details.

The datasets included in this repository are provided for convenience and are subject to their respective licenses as provided by the original authors and distributors. For more details on the licenses and to access the original datasets, please refer to the original sources listed in the table above.

Please ensure compliance with the respective licenses when using these datasets.
