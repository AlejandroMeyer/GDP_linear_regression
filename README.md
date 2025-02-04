# Germany GDP Analysis 📈  

This project analyzes Germany's Gross Domestic Product (GDP) over time using Python and various data processing and machine learning techniques. The data was downloaded from the **World Bank** and is contained in the file:  

**Source Data:**  
- `API_NY.GDP.MKTP.CD_DS2_es_csv_v2_5998674.csv` – Raw GDP data from the World Bank.  

**Project Files:**  
- `main.py` – Python script containing the code for data processing, visualization, and model training.  
- `Metadata_Country_API.csv` – Metadata with country information.  
- `Metadata_Indicator_API.csv` – Metadata with indicator details.  
- `linearRegresion_Germany.xlsx` – Output file containing the processed GDP data and predictions.  

## Features  

- **Data Preparation:**  
  - Reads GDP data from the World Bank CSV file.  
  - Filters data for Germany and processes it for analysis.  
  - Transposes and renames columns for better readability.  

- **Data Visualization:**  
  - Scatter plot of GDP over the years.  
  - Linear regression visualization with an estimated trend line.  

- **Modeling and Prediction:**  
  - Calculates GDP predictions using a predefined regression formula.  
  - Computes error metrics to evaluate the model’s accuracy.  
  - Implements linear regression using `sklearn` to determine optimal parameters.  

- **File Management:**  
  - Generates an Excel file (`linearRegresion_Germany.xlsx`) containing the processed GDP data.  
  - Ensures the output file is updated without duplication.  

## Project Structure  

```
📂 Project Directory  
│-- API_NY.GDP.MKTP.CD_DS2_es_csv_v2_5998674.csv  # GDP data file  
│-- Metadata_Country_API.csv                      # Country metadata  
│-- Metadata_Indicator_API.csv                    # Indicator metadata  
│-- main.py                                       # Main Python script  
│-- requirements.txt                              # Required dependencies  
│-- README.md                                     # Project documentation  
│-- linearRegresion_Germany.xlsx                  # Processed GDP output  
```

## Installation  

1. Clone the repository:  
   ```shell
   [git clone https://github.com/AlejandroMeyer/GDP_linear_regression.git]
   ```

2. Install dependencies:  
   ```shell
   pip install -r requirements.txt
   ```

## Usage  

Run the script to analyze Germany's GDP:  
```shell
python main.py
```

## Key Code Sections  

### 1. Data Processing  
The script loads and processes Germany's GDP data from the World Bank CSV file:  
```python
df = gdp_df[gdp_df['Country Name'] == 'Alemania']
df = df.drop(columns=['Country Name','Country Code', 'Indicator Name', 'Indicator Code'])
df = df.transpose().reset_index().rename(columns={'index': 'YEAR', 55: 'GDP'})
df = df[(df['YEAR'] > '1969') & (df['YEAR'] < '2022')]
```

### 2. Visualization  
Scatter plot to visualize GDP trends:  
```python
graph = germany_gdp_df.plot.scatter(x='YEAR', y='GDP')
graph.set_xticks(germany_gdp_df['YEAR'][::2])
graph.set_xticklabels(germany_gdp_df['YEAR'][::2], rotation=90)
plt.show()
```

### 3. Linear Regression Model  
Fitting a linear regression model to the data:  
```python
model = LinearRegression(fit_intercept=False)
model.fit(X_train, Y_train)
print(f"Intercept (b): {model.intercept_}")
print(f"Slope (w): {model.coef_}")
```

### 4. Exporting Results  
The processed GDP data is saved to an Excel file:  
```python
germany_gdp_df.to_excel('linearRegresion_Germany.xlsx', index=False, engine='openpyxl')
```

## Requirements  

Ensure you have the following dependencies installed:  
- `pandas`  
- `numpy`  
- `matplotlib`  
- `scikit-learn`  
- `openpyxl`  

Install them using:  
```shell
pip install -r requirements.txt
```

## Benefits of This Project  

- **Privacy-focused:** All processing is done locally, avoiding the need to upload sensitive economic data online.  
- **Easy to Use:** Simple scripts to analyze GDP trends without extensive setup.  
- **Customizable:** Modify and extend the project to analyze other countries' GDP.  

## License  

This project is licensed under the MIT License.  

---

Feel free to contribute and improve this project!
