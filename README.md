# **Data Distribution Task - Simulating & Evaluating Data**  

## **Project Overview**  
This project focuses on **generating and evaluating synthetic datasets** from `supermarket.csv` using two approaches:  
1. **Independent Feature Simulation** – Generating data without considering correlations.  
2. **Correlation-Preserved Simulation** – Generating data while maintaining feature relationships using a copula-based approach.  

The goal is to compare both datasets in terms of **data quality, distribution, and statistical evaluation** to determine which approach is more reliable.  

---

## **Approaches Used**  

### **1️⃣ Independent Feature Simulation (Column-wise Distribution Generation)**  
- Each feature is simulated separately using its detected distribution (e.g., **Uniform, Gamma, Binomial**).  
- Ignores dependencies between features.  
- Provides a **better match for individual feature distributions** but fails to capture feature relationships.  

### **2️⃣ Correlation-Preserved Simulation (Copula-Based Generation)**  
- Uses a **copula model** to generate data while preserving correlations.  
- Captures both **numerical and categorical dependencies** effectively.  
- More **realistic for business metrics** like *Sales, COGS, and Gross Income*, which depend on other features.  

---

## **Statistical Evaluation & Findings**  

### **📊 1. Data Quality Assessment**
- **KL Divergence for Continuous Features**  
  - **Column-wise Generation**: Lower KL divergence for some features (*Unit Price, Quantity*), but failed to maintain correlations.  
  - **Copula-Based Generation**: Preserved correlations but had slightly higher KL divergence for *Sales, Gross Income, and Tax 5%*.  

- **Chi-Square Test for Categorical Features**  
  - Both approaches **preserved categorical distributions well**.  
  - Some deviations were found in *Branch, City, and Product Line* under the copula model.  

- **Statistical Tests (Mean & Standard Deviation Comparison)**  
  - **Column-wise Generation**: Overestimated *Sales, COGS, Tax 5%*.  
  - **Copula-Based Generation**: Maintained general distribution but showed **slight variations in correlation strength**.  

### **📈 2. Which Approach is Better?**
| **Criteria**            | **Column-wise Generation** | **Copula-Based Generation** |
|-------------------------|--------------------------|---------------------------|
| **Captures Feature Correlation?** | ❌ No | ✅ Yes |
| **Maintains Individual Feature Distributions?** | ✅ Yes | 🔸 Mostly |
| **Preserves Business Logic?** | ❌ No | ✅ Yes |
| **Computational Complexity** | ✅ Low | 🔸 Moderate |
| **Best For** | Simple, Univariate Analysis | Multivariate & Business Data |

**Conclusion:**  
✔ **Use Column-wise Generation** if you only need to match individual distributions.  
✔ **Use Copula-Based Generation** if maintaining feature relationships is essential.  

---

## **Project Files**  
- 📊 **`supermarket.csv`** – Original dataset used for data simulation.  
- 📄 **`Data_Distribution.ipynb`** – Jupyter Notebook for data generation and analysis.  
- 📊 **`simulated_first.csv`** – Data simulated without correlation.  
- 📊 **`simulated_second.csv`** – Data simulated with correlation.  
- 📝 **`Report.docx`** – Detailed analysis and comparison of both approaches.  
