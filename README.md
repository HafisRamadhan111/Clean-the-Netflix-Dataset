# Clean-the-Netflix-Dataset

*Project Reference: [https://roadmap.sh/projects/cleaning-netflix-dataset](https://roadmap.sh/projects/cleaning-netflix-dataset)*

## Project Description
This project focuses on data cleaning and preprocessing using Python and Pandas. The goal is to take a messy, real-world dataset (Netflix titles from Kaggle) and transform it into a clean, structured format ready for Exploratory Data Analysis (EDA) and visualization. 

Instead of blindly dropping all missing values, this project emphasizes making logical data decisions to preserve as much valuable information as possible.

## Project Requirements Addressed
- Downloaded the Netflix dataset from Kaggle.
- Inspected the DataFrame using `.info()`, `.describe()`, and `.head()`.
- Identified and handled missing values column by column with specific strategies.
- Fixed mixed-type columns (e.g., extracting pure numbers from the `duration` column).
- Parsed date columns (`date_added`) into proper Pandas `datetime` objects.
- Exported the cleaned DataFrame to a new CSV file (`Clean the Netflix Dataset.csv`).

## Technologies Used
- **Python**
- **Pandas** (for Data Manipulation)
- **NumPy**
- **Jupyter Notebook / Google Colab**

## My Approach & Data Decisions
In real-world data science, simply using `.dropna()` on the whole dataset can lead to massive data loss. Here is how I handled the messy data strategically:

1. **Stripping Whitespaces:** Cleaned all column names first using `str.strip()` to prevent hidden bug/errors.
2. **Preserving Data (Imputation):** Columns with a large number of missing values (`director`, `cast`, `country`, and `rating`) were filled with `"unknown"`. This prevents the loss of thousands of rows of movies that are otherwise perfectly valid.
3. **Handling Mixed-Types Smartly:** The `duration` column contained text like `"90 min"`. 
   - I temporarily filled missing values with `"0 min"`.
   - I split the string to isolate the numbers and converted the column to a numeric format using `pd.to_numeric(errors="coerce")`.
4. **Datetime Conversion:** Standardized the `date_added` column by stripping whitespaces and converting it to proper `datetime` objects.
5. **Surgical Dropping:** I only used `.dropna()` to remove the very few rows (~10 rows) that were still missing their `date_added` values after conversion, ensuring maximum data retention (over 99% of the dataset preserved).

## How to Run

1. Clone this repository.
2. Ensure you have the dataset `netflix_titles.csv` in the same directory (or update the file path in the script).
3. Install Pandas if you haven't already:
   ```bash
   pip install pandas numpy
