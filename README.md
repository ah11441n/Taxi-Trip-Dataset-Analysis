<<<<<<< HEAD
# Taxi Trip Dataset Analysis

## Overview
This repository contains a comprehensive analysis and preprocessing of a large taxi trip dataset, originally comprising 3,007,687 rows and 20 columns. The dataset includes detailed information about each taxi trip, such as vendor ID, pickup and dropoff times, passenger count, trip distance, location IDs, rate codes, payment types, and various charges.

## Dataset Details

### Initial Dataset
- **Number of Rows**: 3,007,687
- **Number of Columns**: 20

### Columns
- `VendorID`: TPEP provider code (1: Creative Mobile Technologies, LLC; 2: VeriFone Inc.)
- `tpep_pickup_datetime`: Meter engagement time
- `tpep_dropoff_datetime`: Meter disengagement time
- `passenger_count`: Number of passengers (driver-entered)
- `trip_distance`: Distance traveled (miles)
- `PULocationID`: Pickup location ID
- `DOLocationID`: Dropoff location ID
- `RatecodeID`: Final rate code (e.g., Standard rate, JFK, Newark, etc.)
- `store_and_fwd_flag`: Indicates if the trip record was stored due to server connection issues (Y/N)
- `payment_type`: Payment method (e.g., Credit card, Cash, etc.)
- `fare_amount`: Time-and-distance fare calculated by the meter
- `extra`: Miscellaneous extras and surcharges
- `mta_tax`: MTA tax ($0.50)
- `improvement_surcharge`: Improvement surcharge ($0.30)
- `tip_amount`: Tip amount
- `tolls_amount`: Total tolls amount
- `total_amount`: Total amount charged (excluding cash tips)
- `congestion_surcharge`: Congestion surcharge
- `airport_fee`: Airport fee (only at LaGuardia and JFK Airports)

### Preprocessing Steps

1. **Null Values Handling**:
   - Dropped rows with null values in `passenger_count`, `RatecodeID`, `store_and_fwd_flag`, and `congestion_surcharge`.
   - Dropped `airport_fee` column as it contained only null values.

2. **Datetime Columns**:
   - Split `tpep_pickup_datetime` and `tpep_dropoff_datetime` into `year`, `month`, `day`, `hour`, `minute`, and `second`.
   - Removed original datetime columns.

3. **Categorical Conversion**:
   - Converted `store_and_fwd_flag` values from 'yes' to 1 and 'no' to 0.

4. **Negative Values**:
   - Converted negative values in financial columns (`fare_amount`, `extra`, `mta_tax`, `tip_amount`, `tolls_amount`, `improvement_surcharge`, `congestion_surcharge`) to positive.
   - Recalculated the `total_amount` based on the corrected charges.

### Data Analysis Insights

- **Passenger Count**:
  - Boxplot analysis indicates trips with a single passenger are most common. Trips with 2 to 8 passengers are considered anomalies.

- **Trip Distance**:
  - Most trips are within 20 miles. Fewer trips exceed 100 miles.

- **Pandemic Impact**:
  - Observed abnormal patterns in charges starting from March 2020 due to the pandemic. Decided to retain outliers to preserve original data.

### Final Processed Dataset

- **Number of Rows**: 271,044
- **Number of Columns**: 28 (including split datetime columns)

### TensorFlow Data Validation

- **Purpose**: Statistical analysis and comparison of feature distributions between training (March 2020) and evaluation (May 2020) datasets.
- **Observations**: Similar distribution patterns with differences attributed to pandemic-related anomalies.

## Usage

The preprocessed dataset is available for analysis and model training. For more details on how to use this dataset or replicate the analysis, please refer to the Jupyter notebooks and scripts provided in this repository.

