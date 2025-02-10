

### **1. Discount Impact on Sales & Profit**
**Objective:** Analyze how discounts affect sales revenue and profit.

**Visuals:**
- **Python**: A scatter plot showing the correlation between **discounts and sales/profit**.
- **Power BI**: A **line or bar chart** showing total **sales and profit** at different discount levels.

---

### **2. Discounts by Segment & Country**
**Objective:** Identify which business segments and countries give the highest discounts.

**Visuals:**
- **Python**: A **boxplot** comparing discounts across different segments/countries.
- **Power BI**: A **stacked bar chart** breaking down discounts per **segment and country**.

---

### **3. Discounts vs. Units Sold**
**Objective:** Determine if higher discounts lead to higher unit sales.

**Visuals:**
- **Python**: A **scatter plot** with a regression line (trend analysis).
- **Power BI**: A **bubble chart** with discounts, units sold, and sales as bubble size.

---

### **4. Monthly Discount Trends**
**Objective:** Examine how discounts vary over time.

**Visuals:**
- **Python**: A **time-series line chart** showing monthly discount trends.
- **Power BI**: A **trendline visualization** with filters for **year, segment, and product**.

---

### **5. Discount Efficiency Analysis**
**Objective:** Find the optimal discount range that maximizes profit without excessive losses.

**Visuals:**
- **Python**: A **histogram or density plot** showing profit distribution across discount bands.
- **Power BI**: A **heatmap** comparing discount bands and profit margins.

---


## **6. ANOVA: Discounts vs. Sales (Grouped by Discount Bands)**
**📌 Objective:**  
Test if there is a **significant difference in Sales** across different **Discount Bands**.

**📌 Why it’s interesting?**  
If sales differ significantly across discount bands, it suggests that certain discount levels are more effective at driving sales.

**🔍 Hypothesis:**
- **Null (H₀):** No significant difference in **Sales** across different **Discount Bands**.
- **Alternative (H₁):** At least one discount band has a significantly different sales mean.

**🛠️ ANOVA Model:**
- **Dependent Variable:** Sales
- **Independent Variable:** Discount Band (Categorical)

---

## **7. ANOVA: Discounts vs. Profit (Grouped by Country)**
**📌 Objective:**  
Test if the **impact of discounts on profit** varies **across different countries**.

**📌 Why it’s interesting?**  
If some countries respond better to discounts than others, businesses can optimize pricing strategies.

**🔍 Hypothesis:**
- **H₀:** No significant difference in **Profit** across different **countries**.
- **H₁:** At least one country shows a significantly different **profit** when discounts are applied.

**🛠️ ANOVA Model:**
- **Dependent Variable:** Profit
- **Independent Variable:** Country (Categorical)

---

## **8. ANOVA: Discounts vs. COGS (Grouped by Product Category)**
**📌 Objective:**  
Test whether **discount levels impact the cost of goods sold (COGS)** differently across **product categories**.

**📌 Why it’s interesting?**  
If some products have **higher costs associated with discounts**, it could indicate inefficiencies in pricing.

**🔍 Hypothesis:**
- **H₀:** No significant difference in **COGS** across different **product categories**.
- **H₁:** At least one product category has significantly different **COGS** when discounts are applied.

**🛠️ ANOVA Model:**
- **Dependent Variable:** COGS
- **Independent Variable:** Product Category (Categorical)

---