# BIHS Data Analysis Project

This repository contains R scripts for processing and analyzing Bangladesh Integrated Household Survey (BIHS) data across multiple years (2011, 2015, 2019).

## Project Structure

```
project/
├── datasets/                      # Place your data files here (not tracked by git)
│   ├── administrative-data/
│   │   └── bgd_adminboundaries_tabulardata.xlsx
│   ├── 2011-bihs/
│   │   ├── a1_2011.tab
│   │   ├── b1_2011.tab
│   │   └── ... (other module files)
│   ├── 2015-bihs/
│   │   └── ... (module files)
│   └── 2019-bihs/
│       └── ... (module files)
├── output/                        # Generated output files (not tracked by git)
│   └── bihs_merged.csv
├── bihs_data_generalized.R       # Main processing script
├── README.md
└── .gitignore
```

## Setup Instructions

### 1. Clone this repository

```bash
git clone https://github.com/yourusername/your-repo-name.git
cd your-repo-name
```

### 2. Install Required R Packages

The script uses the `pacman` package manager to automatically install and load required packages. Run this in R:

```r
if (!require("pacman")) install.packages("pacman")
pacman::p_load(dplyr, tidyverse, stringr, openxlsx, here)
```

### 3. Set Up Data Directory

Create a `datasets` folder in the project root and organize your BIHS data files according to the structure shown above:

- Place administrative boundary data in `datasets/administrative-data/`
- Create separate folders for each survey year: `datasets/2011-bihs/`, `datasets/2015-bihs/`, `datasets/2019-bihs/`
- Place the corresponding `.tab` module files in each year folder

### 4. Run the Script

Open R/RStudio, set your working directory to the project root, and run:

```r
source("bihs_data_generalized.R")
```

The script will:
- Load and process administrative boundary data
- Create urban/rural and flood-prone indicators
- Merge individual-level and household-level BIHS modules across all years
- Export the merged dataset to `output/bihs_merged.csv`

## Data Requirements

### Administrative Data
- `bgd_adminboundaries_tabulardata.xlsx` - Must contain an "ADM3" sheet with administrative boundary information

### BIHS Survey Modules

**Individual-level modules:**
- b1 (Demographics)
- b2 (Education)
- c (Health)
- e (Employment)
- v1 (Migration) - excluded from 2011

**Household-level modules:**
- g, k1, n, q, z1, j1, j2, s, t1

All `.tab` files should be tab-delimited with consistent identifier variables (`a01` for household, `mid` for individual).

## Key Features

- **Cross-platform compatibility:** Uses the `here` package for portable file paths
- **Multi-year integration:** Automatically processes and merges data from 2011, 2015, and 2019
- **Data cleaning:** Removes duplicates and handles missing values
- **Geographic indicators:** Creates urban/rural and flood-prone location variables

## Notes

- The `datasets/` and `output/` folders are not tracked by git (see `.gitignore`)
- Data files must be obtained separately and placed in the appropriate directories
- The script expects specific column names in the raw data files

## License

[Add your license information here]

## Contact

[Add your contact information here]
