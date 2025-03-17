## **GitHub 项目分析步骤与字段对应关系**  

在你的 **Sales and Advertising Data** 项目中，每个分析步骤都会涉及特定的数据字段。以下是**完整的分析流程**，并指出**每个步骤所涉及的字段**，方便你整理到 GitHub。

---

## **1. 数据清洗（Python + SQL）**
### **1.1 缺失值处理**  
**涉及字段**：  
- `TV`
- `Billboards`
- `Google Ads`
- `Social Media`
- `Influencer Marketing`
- `Affiliate Marketing`
- `Product_Sold`  

**处理方式**：  
- 检查广告投入 (`TV`、`Billboards` 等) 是否有空值。
- **填充方式**：  
  - **中位数填充**（适用于数值数据，如广告费用）。
  - **剔除无效记录**（如果 `Product_Sold` 为空或为 0，可以进一步检查是否为异常情况）。

---

### **1.2 异常值检测**  
**涉及字段**：  
- `TV`
- `Billboards`
- `Google Ads`
- `Social Media`
- `Influencer Marketing`
- `Affiliate Marketing`
- `Product_Sold`

**异常值处理**：  
- **Z-score 方法** 或 **箱线图（IQR）** 检测异常值：  
  - 例如：广告投入异常高，但 `Product_Sold` = 0，可能是**无效投放**。
  - 另一种情况：`Product_Sold` 远高于其他值，可能是异常数据。

---

## **2. 探索性数据分析（EDA）**
### **2.1 描述性统计**  
**涉及字段**：  
- `TV`
- `Billboards`
- `Google Ads`
- `Social Media`
- `Influencer Marketing`
- `Affiliate Marketing`
- `Product_Sold`

**分析内容**：  
- 计算**均值、标准差、最小值、最大值、中位数**，了解广告投入和销量的分布情况。

---

### **2.2 相关性分析**  
**涉及字段**：  
- `TV`
- `Billboards`
- `Google Ads`
- `Social Media`
- `Influencer Marketing`
- `Affiliate Marketing`
- `Product_Sold`

**分析方法**：  
- 计算 **皮尔逊相关系数（Pearson Correlation）**：  
  - **目标**：找出 **广告投入 vs. 产品销量** 的相关性，确定哪些广告渠道最有效。
  - 示例：  
    - `TV` 与 `Product_Sold` 的相关性 = **0.7**（较高相关）
    - `Affiliate Marketing` 与 `Product_Sold` 的相关性 = **0.2**（相关性较低）

---

### **2.3 数据可视化**  
**涉及字段**：  
- `TV`
- `Billboards`
- `Google Ads`
- `Social Media`
- `Influencer Marketing`
- `Affiliate Marketing`
- `Product_Sold`

**可视化方法**：  
- **散点图**：展示 **广告支出 vs. 销量** 的关系。
- **箱线图**：检查广告支出是否存在极端值。
- **直方图**：查看销量的分布情况。
- **热力图（Heatmap）**：查看广告渠道之间的相关性。

---

## **3. 归因模型（Python）**
### **3.1 渠道贡献分析**  
**涉及字段**：  
- `TV`
- `Billboards`
- `Google Ads`
- `Social Media`
- `Influencer Marketing`
- `Affiliate Marketing`
- `Product_Sold`

**分析方法**：  
- **多元回归模型**：
  - 目标：量化各广告渠道对 `Product_Sold` 的贡献。
  - 公式示例：
    \[
    Product\_Sold = β_0 + β_1(TV) + β_2(Billboards) + β_3(Google Ads) + \dots + ε
    \]
- **Shapley 值法（SHAP）** 或 **马尔可夫链模型**：
  - 计算各广告渠道的边际贡献，找到最具影响力的渠道。

---

### **3.2 策略优化**  
**涉及字段**：  
- `TV`
- `Billboards`
- `Google Ads`
- `Social Media`
- `Influencer Marketing`
- `Affiliate Marketing`
- `Product_Sold`

**分析方法**：  
- **ROI 计算（广告投入回报率）**：  
  \[
  ROI = \frac{\text{Product_Sold}}{\text{广告成本}}
  \]
- **优化建议**：  
  - 如果某渠道 ROI **较低**，则减少预算。
  - 如果某渠道 ROI **较高**，则增加预算。

---

## **4. 销售预测（Python）**
### **4.1 构建预测模型**  
**涉及字段**：  
- `TV`
- `Billboards`
- `Google Ads`
- `Social Media`
- `Influencer Marketing`
- `Affiliate Marketing`
- `Product_Sold`

**模型选择**：  
- **时间序列模型（ARIMA/Prophet）**
- **回归模型（XGBoost/Random Forest）**

---

## **5. 可视化与报告**
### **5.1 动态仪表板（Power BI/Tableau）**
### **5.2 总结报告**

---

