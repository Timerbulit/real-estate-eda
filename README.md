# USA Real Estate Pricing Analysis

An exploratory data analysis (EDA) project examining pricing patterns in the US real estate market.

## Overview

This project analyzes 2.2M+ real estate listings from Kaggle to uncover correlations between property attributes (bedrooms, bathrooms, square footage, location) and prices across different states and zip codes.

## Dataset

- **Source**: Kaggle USA Real Estate Data
- **Size**: 2.2M+ listings, 12 columns
- **Columns**: state, city, zip_code, street, bed, bath, acre_lot, house_size, price, status, prev_sold_date, brokered_by

## Project Structure

```
real_estate_project/
├── real_estate_eda.ipynb     # Main analysis notebook
├── data/
│   └── realtor-data.zip.csv  # Raw dataset (not included in repo)
├── models/                     # Reserved for trained models
├── requirements.txt            # Python dependencies
└── README.md                   # This file
```

## Setup

### Prerequisites
- Python 3.12+
- Jupyter Notebook

### Installation

1. Clone the repository:
```bash
git clone https://github.com/Timerbulit/real-estate-eda.git
cd real-estate-eda
```

2. Create and activate virtual environment:
```bash
python -m venv .venv
source .venv/bin/activate  # On Windows: .venv\Scripts\activate
```

3. Install dependencies:
```bash
pip install -r requirements.txt
```

4. Download the dataset from [Kaggle](https://www.kaggle.com/) and place `realtor-data.zip.csv` in the `data/` directory.

## Running the Analysis

Start Jupyter and open the notebook:
```bash
jupyter notebook real_estate_eda.ipynb
```

Or export to HTML/PDF:
```bash
jupyter nbconvert --to html real_estate_eda.ipynb
jupyter nbconvert --to pdf real_estate_eda.ipynb
```

## Analysis Highlights

- Missing value analysis with correlation patterns (bed↔bath: 0.9, bed/bath↔house_size: 0.8)
- State-median imputation strategy for missing numeric features
- Statistical summaries and visualizations of price distributions
- Geographic pricing patterns across states and regions

## Dependencies

- **pandas** - Data manipulation
- **numpy** - Numerical computing
- **matplotlib** - Plotting
- **seaborn** - Statistical visualization
- **missingno** - Missing data visualization
- **jupyter** - Notebook environment

See `requirements.txt` for complete list.

## Notes

- Dataset is large (~204 MB in memory) — processing may take time
- Contains outliers (e.g., house_size up to 1B+ sq ft) requiring filtering for analysis
- All data preprocessing and exploration is contained in the Jupyter notebook

## License

MIT License - feel free to use this for educational purposes.
