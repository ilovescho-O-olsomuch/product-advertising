# 广告投入与产品销量分析

本项目通过数据清洗、统计分析、机器学习和时间序列模型，评估不同广告渠道对产品销量的影响，并提供优化建议。

## 数据预处理
1. **缺失值处理**  
   - 广告投入字段使用中位数填充  
   - 删除无效销售记录（空值或销量=0）
2. **异常值检测**  
   - 使用IQR方法剔除异常值

## 分析方法
### 1. 描述性统计与相关性分析
- 计算均值、标准差、极值等统计指标  
- 皮尔逊相关系数评估广告渠道与销量的线性关系  
- 多元线性回归分析渠道贡献度

### 2. 数据可视化
- 散点图展示广告支出与销量关系  
- 箱线图检测广告投入分布  
- 热力图分析渠道间相关性

### 3. 渠道效果评估
- **SHAP值分析**：量化各广告渠道对销量的非线性影响  
- **回归模型**：Affiliate Marketing贡献最高（系数=3.9989）

### 4. 时间序列预测
- ADF检验验证数据平稳性  
- SARIMA模型预测未来30天销量  
- 发现7天周期性销售规律（季节性系数=0.2764, p=0.000）

## 主要结论
✅ **高效渠道**  
- Affiliate Marketing（相关系数0.60，SHAP贡献960）  
- Billboards（相关系数0.46，SHAP贡献705）  
- Social Media（SHAP贡献580）

⚠️ **低效渠道**  
- Google Ads（相关系数0.20）  
- Influencer Marketing（相关系数0.12）

📈 **预测趋势**  
- 未来30天销量预计平稳增长

## 优化建议
1. 增加Affiliate Marketing预算至少20%  
2. 在周末周期性高峰时段加强Social Media投放  
3. 对Google Ads进行A/B测试优化关键词策略  
4. 建立UTM渠道跟踪机制，精准计算ROI

---

### 数据可视化-PYTHON/POWERBI

![数据可视化](https://github.com/ilovescho-O-olsomuch/product-advertising/blob/main/%E6%95%B0%E6%8D%AE%E5%8F%AF%E8%A7%86%E5%8C%96.png)
![数据可视化](https://github.com/ilovescho-O-olsomuch/product-advertising/blob/main/powerbiadvertise.png)

**技术栈**：Python/Pandas/Statsmodels/Matplotlib/SHAP  






