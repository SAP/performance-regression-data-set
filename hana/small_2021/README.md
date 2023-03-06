# Performance Regression Data Set (small)

A data set on performance measurements to allow research on performance regression detection.

This is a small data set that contains a mix of different types of time series that are found in practice at SAP HANA.
The data set is also annotated with change points as determined in practice at SAP.

1. [data](data) contains the data, 25 time series, each represented by a csv file 0000.csv to 0024.csv.
   The time series have different lengths, from 117 to 2462 entries.
1. [metadata](metadata) contains metadata that describe the time series.

Each time series csv file contains 3 columns:

- Index: A unique and increasing number. Just what you expect from an index.
- GHC: An internal term that represents a build number.
  That means rows with the same GHC number represent measurements for the same build.
  In general, a higher GHC number represents a "later" build.
  However, the terms "later" may not be well-defined in this context as the underlying git does not represent a linear workflow.
- Measurement: A (floating point) number without a unit that represents a time duration measurement.

In addition, there is a dataset_details.csv file that contains the human judgement for the time series.
The file contains 3 columns:

- Type: A categorization of the corresponding time series. The value is one of:
  - Stable: No regression and no issues
  - Regression: The series contains a performance regression
  - all other: It looks like there might be a regression but there is a different explanation indicated by the value.
- Dataset: the "foreign" key to link the details to the time series
- Change Point: The last index before the regression was introduced.
  The measurement where index == change_point has no regression, but the measurement where index == (change_point + 1) shows the regression.

The license for this data set is CC-BY-4.0 as indicated by the LICENSE file.

Contact: Thomas Bach / SAP (see contributing authors)
