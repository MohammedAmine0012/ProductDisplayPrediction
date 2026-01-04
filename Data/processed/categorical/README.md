# Categorical Data - MDLPC Discretization

This folder contains the processed categorical data created using MDLPC (Minimum Description Length Principle for Discretization).

## Files

- **data_categorical_mdlpc.csv**: The processed dataset with all continuous variables converted to categorical
- **mdlpc_cut_points.txt**: Information about the cut points used for discretization
- **discretization_summary.csv**: Summary statistics of the discretization process

## How to Generate

Run the MDLPC discretization script:

```bash
# From project root
python src/scripts/mdlpc_discretization.py
```

Or use the notebook code in `src/scripts/mdlpc_notebook_code.py` to run it in Jupyter.

## Data Structure

The categorical dataset contains:
- **X1_cat, X2_cat, X3_cat, X4_cat, X6_cat**: Discretized versions of continuous variables
- **X5, X7**: Original nominal variables (unchanged)
- **Y**: Target variable (unchanged)

## Usage

This categorical data can be used for:
- Models that work with nominal features
- Creating a Datamart with only categorical variables
- Comparing model performance with categorical vs continuous features

