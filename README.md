import pandas as pd

# Load dataset
df = pd.read_csv('Mall_Customers.csv')

# 1. Check for missing values
print(df.isnull().sum())

# Fill missing Annual Income with median
df['Annual Income ($)'] = df['Annual Income ($)'].fillna(df['Annual Income ($)'].median())

# 2. Remove duplicate rows
df = df.drop_duplicates()

# 3. Standardize gender values (e.g., lowercase)
df['Gender'] = df['Gender'].str.lower()

# 4. Rename columns
df.columns = df.columns.str.strip().str.lower().str.replace(' ', '_')

# 5. Check and correct data types
df['customerid'] = df['customerid'].astype(int)
df['age'] = df['age'].astype(int)
df['annual_income_($)'] = df['annual_income_($)'].astype(float)

# Save cleaned dataset
df.to_csv('Mall_Customers_Cleaned.csv', index=False)
