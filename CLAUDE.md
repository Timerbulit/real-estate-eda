# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project Overview

This is a data science exploratory data analysis (EDA) project focused on USA real estate pricing patterns. The primary work is conducted in a Jupyter notebook that analyzes real estate listings across states and zip codes, examining correlations between property attributes and prices.

## Project Structure

- **`real_estate_eda.ipynb`** - Main exploratory data analysis notebook. Contains data preprocessing, cleaning, and visualization of USA real estate data from Kaggle.
- **`data/`** - Directory containing the raw dataset:
  - `realtor-data.zip.csv` - USA real estate listings (2.2M+ entries with 12 columns)
- **`models/`** - Reserved for trained ML models (currently empty)
- **`.venv/`** - Python virtual environment (Python 3.12)

## Development Setup

### Activate Virtual Environment

```bash
source .venv/bin/activate
```

### Running the Notebook

Start Jupyter notebook server:
```bash
jupyter notebook
```

Then open `real_estate_eda.ipynb` in the browser interface.

Alternatively, convert to HTML/PDF:
```bash
jupyter nbconvert --to html real_estate_eda.ipynb
jupyter nbconvert --to pdf real_estate_eda.ipynb
```

## Key Dependencies

Core data science stack (installed in `.venv`):
- **pandas** - Data manipulation and analysis
- **numpy** - Numerical computing
- **matplotlib** - Static plotting
- **seaborn** - Statistical data visualization
- **missingno** - Missing data visualization
- **jupyter/ipykernel** - Notebook infrastructure
- **ipython** - Interactive shell

## Data Architecture

The real estate dataset contains 2.2M listings with:
- **Location attributes**: state, city, zip_code, street (categorically encoded)
- **Property attributes**: bed, bath, acre_lot, house_size
- **Market attributes**: price, status (for_sale/sold), prev_sold_date
- **Broker info**: brokered_by (categorically encoded)

### Data Preprocessing Pattern

The notebook follows a standard EDA workflow:
1. **Load and inspect** - Check dtypes, sample data, data info
2. **Type conversion** - bed, bath, zip_code → Int64; prev_sold_date → datetime
3. **Missing value analysis** - Use missingno visualization; identify correlations between missing values
4. **Imputation strategy** - Fill correlated missing values (bed/bath/house_size) with state medians; drop rows with critical missing price/state/zip_code
5. **Deduplication** - Remove duplicate records
6. **Exploration** - Statistical summaries and visualizations

## Important Notes

- The notebook uses a large dataset (203.8 MB in memory). Cell execution may take time.
- Missing values have strong correlations: bed↔bath (0.9), bed/bath↔house_size (0.8). These are handled via state-median imputation.
- Outliers exist in numeric columns (e.g., house_size max: 1,040,400,400 sq ft) which may need filtering for analysis.
- The notebook contains extensive visualization cells that display matplotlib/seaborn outputs inline.

## Requirements Management

The `requirements.txt` is currently empty. To update it with active dependencies:
```bash
pip freeze > requirements.txt
```

Note: The venv already contains all necessary packages; this ensures reproducibility.
