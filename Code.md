## Install required packages
```python
!pip install matplotlib pandas statsmodels scipy openpyxl
```

## Open Excel Files
```python
import pandas as pd

# Replace with the raw URL of your .xlsx file
github_url = "https://github.com/afifhusman/powerbi_prubsn/raw/refs/heads/main/fin_sample.xlsx"

# Read the Excel file
df = pd.read_excel(github_url)

# Print the first 5 rows
print(df.head())
```

## Run ANOVA and Diplay p-value

```python
import matplotlib.pyplot as plt
import matplotlib.patheffects as path_effects
import pandas as pd
import scipy.stats as stats

# Read the data
github_url = "https://github.com/afifhusman/powerbi_prubsn/raw/refs/heads/main/fin_sample.xlsx"

# Read the Excel file
df = pd.read_excel(github_url)

# Drop rows where 'Discount Band' or 'Profit' is missing
df_clean = df.dropna(subset=['Discount Band', 'Profit'])

# Group data by 'Discount Band'
groups = [group['Profit'].values for name, group in df_clean.groupby('Discount Band')]

# Perform one-way ANOVA
anova_result = stats.f_oneway(*groups)

fig = plt.figure(figsize=(10, 1.5))
text = fig.text(0.0, 0.5, 'ANOVA Test Results:\n\nP-value= ' + str(anova_result.pvalue),
                ha='left', va='center', size=15)
text.set_path_effects([path_effects.Normal()])

plt.show()
```

## Run Tukey's Posthoc

```python
import pandas as pd
import matplotlib.pyplot as plt
import numpy as np
import scipy.stats as stats
from statsmodels.stats.multicomp import pairwise_tukeyhsd

# Read the data
github_url = "https://github.com/afifhusman/powerbi_prubsn/raw/refs/heads/main/fin_sample.xlsx"

# Read the Excel file
df = pd.read_excel(github_url)

# Drop NaN values for Discount Band and Profit
df = df.dropna(subset=["Discount Band", "Profit"])

# --- ANOVA Test ---
profit_groups = [df[df["Discount Band"] == band]["Profit"] for band in df["Discount Band"].unique()]
anova_result = stats.f_oneway(*profit_groups)

# --- Tukey Post Hoc Test ---
tukey = pairwise_tukeyhsd(df["Profit"], df["Discount Band"], alpha=0.05)

# Convert Tukey test results to DataFrame
tukey_df = pd.DataFrame(data=tukey.summary().data[1:], columns=tukey.summary().data[0])

# --- Visualization: Tukey Post Hoc Test Results ---
groups1 = tukey_df["group1"]
groups2 = tukey_df["group2"]
mean_diff = tukey_df["meandiff"]
p_values = tukey_df["p-adj"]
significant = tukey_df["reject"]

# Convert significance to color (red for significant, blue for not significant)
colors = ["red" if sig else "blue" for sig in significant]

# Create figure
fig, ax = plt.subplots(figsize=(10, 2))

# Plot mean differences as bars
y_pos = np.arange(len(groups1))
ax.barh(y_pos, mean_diff, color=colors, alpha=0.7)

# Add labels
ax.set_yticks(y_pos)
ax.set_yticklabels([f"{g1} vs {g2}" for g1, g2 in zip(groups1, groups2)])
ax.set_xlabel("Mean Difference")
ax.set_title("Tukey Post Hoc Test Results")

# Add p-values as text on bars
for i, (diff, p) in enumerate(zip(mean_diff, p_values)):
    ax.text(diff, i, f"p={p:.3f}", va='center', ha='left', fontsize=10, color="black")

# Show plot
plt.show()
```