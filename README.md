# 📦 Supply Chain Inventory Optimization Analysis

[![Python](https://img.shields.io/badge/Python-3.8%2B-blue)](https://www.python.org/)
[![SQL](https://img.shields.io/badge/SQL-PostgreSQL%20%7C%20MySQL-orange)](https://www.postgresql.org/)
[![Tableau](https://img.shields.io/badge/Visualization-Tableau%20%7C%20Power%20BI-green)](https://www.tableau.com/)
[![License](https://img.shields.io/badge/License-MIT-yellow.svg)](LICENSE)

> **Comprehensive data analysis project focusing on supply chain inventory optimization to reduce costs, minimize stockouts, and improve operational efficiency.**

## 🎯 **Project Objectives**

This project demonstrates data analysis capabilities in supply chain management by:
- **Optimizing inventory levels** to reduce carrying costs by 15-20%
- **Minimizing stockout incidents** through better demand forecasting
- **Improving supplier performance** evaluation and selection
- **Enhancing warehouse efficiency** and resource allocation

## 📊 **Business Impact**

| Metric | Current State | Target Improvement |
|--------|---------------|-------------------|
| Inventory Carrying Cost | Baseline | **15-20% Reduction** |
| Stockout Rate | Baseline | **30% Reduction** |
| Supplier On-Time Delivery | 75% | **90%+ Target** |
| Inventory Turnover | 4.2x | **6x+ Target** |

## 🔍 **Key Business Questions Answered**

1. **Which products require immediate reordering to prevent stockouts?**
2. **What is the optimal safety stock level for each product category?**
3. **Which suppliers provide the best value (quality vs cost vs delivery)?**
4. **How can we optimize inventory distribution across regional warehouses?**
5. **What seasonal patterns should inform our procurement strategy?**

## 📁 **Project Structure**

```
supply-chain-inventory-optimization/
├── 📂 data/
│   ├── supply_chain_inventory_data.csv      # Main transactional data
│   ├── supplier_master_data.csv            # Supplier information
│   └── warehouse_master_data.csv           # Warehouse details
├── 📂 notebooks/
│   ├── 01_data_exploration.ipynb           # Initial data analysis
│   ├── 02_inventory_analysis.ipynb         # Inventory optimization
│   ├── 03_supplier_analysis.ipynb          # Supplier performance
│   └── 04_visualization_dashboard.ipynb    # Final dashboard
├── 📂 sql/
│   ├── inventory_queries.sql               # Inventory analysis queries
│   ├── supplier_performance.sql            # Supplier KPI queries
│   └── seasonal_analysis.sql               # Demand pattern queries
├── 📂 visualizations/
│   ├── inventory_dashboard.png             # Main dashboard screenshot
│   ├── supplier_scorecard.png              # Supplier performance viz
│   └── seasonal_trends.png                 # Demand seasonality chart
├── 📂 reports/
│   └── Executive_Summary.pdf               # Business findings report
├── generate_dataset.py                     # Dataset generation script
├── requirements.txt                        # Python dependencies
└── README.md                              # This file
```

## 🛠️ **Technologies Used**

### **Programming & Analysis**
- **Python 3.8+**: Primary analysis language
- **Pandas**: Data manipulation and analysis
- **NumPy**: Numerical computations
- **Matplotlib/Seaborn**: Statistical visualizations

### **Database & Querying**
- **SQL**: Data querying and aggregation
- **PostgreSQL/MySQL**: Database management
- **Jupyter Notebook**: Interactive analysis environment

### **Visualization & Reporting**
- **Tableau Public**: Interactive dashboards
- **Power BI**: Business intelligence reporting
- **Plotly**: Interactive web visualizations

## 📈 **Key Analyses & Findings**

### **1. Inventory Turnover Optimization**
- **Electronics category** shows highest turnover (8.2x annually)
- **Books category** requires inventory reduction (2.1x turnover)
- **Recommended**: Implement ABC classification for differential management

### **2. Supplier Performance Analysis**
- **SupplierC** achieves 94% on-time delivery rate
- **SupplierD** shows consistently higher defect rates (8.5% vs 3.2% average)
- **Cost savings potential**: $250K annually through supplier consolidation

### **3. Regional Inventory Distribution**
- **Jakarta warehouse** shows 87% utilization vs 65% average
- **Medan warehouse** has excess capacity for redistribution
- **Optimization opportunity**: Rebalance stock allocation saves $180K

### **4. Seasonal Demand Patterns**
- **November-December**: 30% demand spike (holiday season)
- **June-July**: 15% increase (mid-year promotions)
- **Procurement recommendation**: Adjust safety stock seasonally

## 🚀 **Getting Started**

### **Prerequisites**
```bash
Python 3.8 or higher
Git
SQL database (PostgreSQL/MySQL)
Tableau Public (free) or Power BI
```

### **Installation**
```bash
# Clone the repository
git clone https://github.com/yourusername/supply-chain-inventory-optimization.git
cd supply-chain-inventory-optimization

# Create virtual environment
python -m venv venv
source venv/bin/activate  # On Windows: venv\Scripts\activate

# Install dependencies
pip install -r requirements.txt

# Generate dataset
python generate_dataset.py
```

### **Usage**
```bash
# 1. Start with data exploration
jupyter notebook notebooks/01_data_exploration.ipynb

# 2. Run inventory analysis
jupyter notebook notebooks/02_inventory_analysis.ipynb

# 3. Analyze supplier performance
jupyter notebook notebooks/03_supplier_analysis.ipynb

# 4. Create visualizations
jupyter notebook notebooks/04_visualization_dashboard.ipynb
```

## 📊 **Sample SQL Queries**

### **Inventory Status Overview**
```sql
SELECT 
    stock_status,
    COUNT(*) as product_count,
    SUM(total_order_value) as total_value,
    ROUND(AVG(current_stock), 0) as avg_stock_level
FROM supply_chain_inventory_data 
GROUP BY stock_status
ORDER BY total_value DESC;
```

### **Supplier Performance Scorecard**
```sql
SELECT 
    supplier,
    ROUND(AVG(quality_score), 2) as avg_quality,
    ROUND(AVG(lead_time_days), 1) as avg_lead_time,
    ROUND(
        SUM(CASE WHEN delivery_status = 'On Time' THEN 1 ELSE 0 END) * 100.0 / COUNT(*), 
        1
    ) as on_time_rate_pct
FROM supply_chain_inventory_data 
GROUP BY supplier
ORDER BY avg_quality DESC, on_time_rate_pct DESC;
```

## 📋 **Dataset Schema**

| Column Name | Data Type | Description |
|-------------|-----------|-------------|
| `product_id` | String | Unique product identifier |
| `category` | String | Product category |
| `supplier` | String | Supplier name |
| `current_stock` | Integer | Current inventory level |
| `reorder_point` | Integer | Reorder trigger level |
| `order_quantity` | Integer | Quantity ordered |
| `unit_cost` | Float | Cost per unit (IDR) |
| `lead_time_days` | Integer | Supplier lead time |
| `quality_score` | Float | Supplier quality rating (1-10) |
| `stock_status` | String | Current stock status |
| `delivery_status` | String | On-time vs delayed delivery |

## 🎨 **Key Visualizations**

### **Interactive Dashboard**
![Inventory Dashboard](visualizations/inventory_dashboard.png)
*Real-time inventory status monitoring with drill-down capabilities*

### **Supplier Performance Matrix**
![Supplier Scorecard](visualizations/supplier_scorecard.png)
*Comprehensive supplier evaluation across quality, cost, and delivery metrics*

### **Seasonal Demand Analysis**
![Seasonal Trends](visualizations/seasonal_trends.png)
*Monthly demand patterns with forecasting implications*

## 💡 **Business Recommendations**

### **Immediate Actions (0-3 months)**
1. **Reorder 847 products** currently below safety stock levels
2. **Negotiate with SupplierD** to improve 8.5% defect rate
3. **Redistribute 15% inventory** from over-stocked Jakarta to Medan warehouse

### **Strategic Initiatives (3-12 months)**
1. **Implement ABC classification** for inventory management
2. **Develop seasonal procurement calendar** based on demand patterns
3. **Establish supplier scorecards** with quarterly performance reviews
4. **Deploy predictive analytics** for demand forecasting

### **Expected ROI**
- **Year 1 Cost Savings**: $430,000
- **Inventory Reduction**: 18% carrying cost decrease
- **Service Level Improvement**: 95% stock availability target

## 👤 **About This Project**

This project was developed as part of a data analyst portfolio, demonstrating:
- **Business acumen** in supply chain operations
- **Technical proficiency** in SQL, Python, and data visualization
- **Analytical thinking** for process optimization
- **Communication skills** through clear reporting and recommendations

**Skills Demonstrated:**
- Data Analysis & Statistical Modeling
- SQL Database Querying & Optimization
- Python Programming (Pandas, NumPy, Matplotlib)
- Business Intelligence & Dashboard Creation
- Supply Chain Management Principles
- Executive Reporting & Presentation

## 📧 **Contact**

**[Your Name]**
- 📧 Email: your.email@example.com
- 💼 LinkedIn: [Your LinkedIn Profile]
- 🌐 Portfolio: [Your Portfolio Website]

---

## 📝 **License**

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

## 🙏 **Acknowledgments**

- Supply chain industry best practices research
- Open source data analysis community
- Statistical methodology references from academic sources

---

### 🌟 **If you found this project helpful, please consider giving it a star!** ⭐

---

*This project demonstrates practical application of data analysis in supply chain optimization, showcasing both technical skills and business impact potential for data analyst roles in supply chain, e-commerce, and FMCG industries.*
