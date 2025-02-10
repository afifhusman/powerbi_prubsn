```python
# Import necessary libraries
import pandas as pd
import matplotlib.pyplot as plt

# Load dataset (Power BI automatically provides 'dataset')
df = dataset

# Rename columns to remove any extra spaces
df.columns = df.columns.str.strip()

# Aggregate sales by country
sales_by_country = df.groupby("Country", as_index=False)["Sales"].sum()

# Sort values for better visualization
sales_by_country = sales_by_country.sort_values(by="Sales", ascending=False)

# Create a bar chart
plt.figure(figsize=(10, 6))
plt.bar(sales_by_country["Country"], sales_by_country["Sales"])

# Customize chart
plt.xlabel("Country")
plt.ylabel("Total Sales")
plt.title("Total Sales by Country")
plt.xticks(rotation=45)

# Show the plot
plt.show()
```


### **1. Importing Necessary Libraries**
```python
import pandas as pd
import matplotlib.pyplot as plt
```
- `pandas` is a Python library used for handling data in **tables (DataFrames)**.
- `matplotlib.pyplot` is used for **creating visualizations** (charts, graphs).

---

### **2. Load the Dataset from Power BI**
```python
df = dataset
```
- **In Power BI**, the data you select for the Python visual is automatically assigned to the variable `dataset`.
- This loads the selected data (columns) into a **Pandas DataFrame** (`df`).

---

### **3. Fixing Column Name Issues (Removing Spaces)**
```python
df.columns = df.columns.str.strip()
```
- **Why?** In Power BI, column names might have **leading or trailing spaces**, causing **KeyErrors** when accessing them.
- `str.strip()` removes spaces from all column names.

---

### **4. Aggregating Sales by Country**
```python
sales_by_country = df.groupby("Country", as_index=False)["Sales"].sum()
```
- **`groupby("Country")`**: Groups the dataset **by country**.
- **`["Sales"].sum()`**: Sums up the `Sales` values for each country.
- **`as_index=False`**: Keeps **Country** as a column instead of making it an index.

💡 **Example Before Grouping:**
| Country | Sales  |
|---------|-------|
| Canada  | 1000  |
| Canada  | 2000  |
| Germany | 1500  |

💡 **After Grouping:**
| Country | Sales |
|---------|-------|
| Canada  | 3000  |
| Germany | 1500  |

---

### **5. Sorting Data for Better Visualization**
```python
sales_by_country = sales_by_country.sort_values(by="Sales", ascending=False)
```
- **Sorts the table** by `Sales` in **descending** order (highest to lowest).
- This makes the bar chart easier to read.

---

### **6. Creating the Bar Chart**
```python
plt.figure(figsize=(10, 6))
plt.bar(sales_by_country["Country"], sales_by_country["Sales"])
```
- `plt.figure(figsize=(10, 6))` → Sets the **chart size** (width=10, height=6).
- `plt.bar(x, y)` → Creates a **bar chart**:
  - **x-axis**: `Country`
  - **y-axis**: `Sales`

---

### **7. Customizing the Chart**
```python
plt.xlabel("Country")
plt.ylabel("Total Sales")
plt.title("Total Sales by Country")
plt.xticks(rotation=45)
```
- `plt.xlabel("Country")` → Labels the **x-axis** as "Country".
- `plt.ylabel("Total Sales")` → Labels the **y-axis** as "Total Sales".
- `plt.title("Total Sales by Country")` → Adds a **title** to the chart.
- `plt.xticks(rotation=45)` → Rotates country names **45 degrees** to prevent overlap.

---

### **8. Displaying the Chart**
```python
plt.show()
```
- **Displays the bar chart** inside Power BI.

---

### **Final Output**
- A **bar chart** showing **total sales per country**.