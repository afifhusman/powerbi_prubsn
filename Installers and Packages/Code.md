```python
import pandas as pd

# Replace with the raw URL of your .xlsx file
github_url = "https://github.com/afifhusman/powerbi_prubsn/raw/refs/heads/main/fin_sample.xlsx"

# Read the Excel file
df = pd.read_excel(github_url)

# Print the first 5 rows
print(df.head())
```