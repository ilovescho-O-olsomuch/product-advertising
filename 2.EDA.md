# 数据分析报告

## 描述性统计

### 代码
```python
import pandas as pd

# 读取清洗后的数据
cleaned_file_path = r"C:\Users\32165\Desktop\Advertising_Data_Cleaned.csv"
df = pd.read_csv(cleaned_file_path)

# 计算统计信息
stats = df.describe()

# 输出均值、标准差、最小值、最大值和中位数
print("广告投入和销量的统计信息：")
print(stats)
print("\n中位数：")
print(df.median())
```

### 结果截图
![描述性统计](https://github.com/ilovescho-O-olsomuch/product-advertising/blob/main/%E6%8F%8F%E8%BF%B0%E7%BB%9F%E8%AE%A1%E4%BF%A1%E6%81%AF.png)

### 结论
#### 广告投入分布情况
- **均值 (mean)** 和 **中位数 (50%)** 相对接近，数据分布较均匀。
- **标准差 (std)** 较大，说明广告投入波动较大。
- **最小值与最大值差距较大**，说明不同广告渠道存在极端投入情况。

#### 销量 (Product_Sold) 分布情况
- **均值和中位数接近**，表明销量数据接近正态分布。
- **标准差较大**，说明销量存在一定波动。
- **最小值与最大值范围适中**，表明销量数据没有明显极端值。

#### 广告投入对销量的影响可能性
由于广告投入的标准差较高，可能存在广告投放过高但销量一般的情况，需要进一步分析广告投入与销量的相关性。

---

## 相关性分析

### 代码
```python
import pandas as pd

# 读取清洗后的数据
df = pd.read_csv(cleaned_file_path)

# 计算皮尔逊相关系数
correlation_matrix = df.corr(method='pearson')

# 提取广告投入与产品销量的相关性
ad_columns = ["TV", "Billboards", "Google_Ads", "Social_Media", "Influencer_Marketing", "Affiliate_Marketing"]
correlation_with_sales = correlation_matrix.loc[ad_columns, "Product_Sold"]

# 输出相关系数
print("广告投入与产品销量的皮尔逊相关系数：")
print(correlation_with_sales)
```

### 结果截图
![相关系数](https://github.com/ilovescho-O-olsomuch/product-advertising/blob/main/%E7%9B%B8%E5%85%B3%E7%B3%BB%E6%95%B0.png)

### 结论
- **Affiliate_Marketing (0.6037)** 关联性最高，应重点优化。
- **Billboards (0.4604) 和 Social_Media (0.3785)** 相关性较高，可作为辅助投放。
- **TV (0.3645)** 相关性一般，可能需要优化广告策略。
- **Google_Ads (0.1996) 和 Influencer_Marketing (0.1215)** 相关性较低，需要优化营销内容。

---

## 数据可视化

### 代码
```python
import pandas as pd
import matplotlib.pyplot as plt
import seaborn as sns
import matplotlib

# 设置 Matplotlib 以支持中文显示
matplotlib.rc("font", family="SimHei")  # 使用黑体字体避免中文乱码
matplotlib.rcParams["axes.unicode_minus"] = False  # 解决负号显示问题

# 读取清洗后的数据
df = pd.read_csv(cleaned_file_path)

# 定义广告投入变量和目标变量
ad_columns = ["TV", "Billboards", "Google_Ads", "Social_Media", "Influencer_Marketing", "Affiliate_Marketing"]

# 创建 2x2 子图布局
fig, axes = plt.subplots(2, 2, figsize=(12, 10))
fig.suptitle("广告投入与销量分析")

# 散点图：广告支出 vs. 销量
sns.scatterplot(ax=axes[0, 0], x=df["TV"], y=df["Product_Sold"])
axes[0, 0].set_title("TV 广告支出 vs. 销量")
axes[0, 0].set_xlabel("TV 广告支出")
axes[0, 0].set_ylabel("销量")

# 箱线图：检查广告支出是否存在极端值
sns.boxplot(ax=axes[0, 1], data=df[ad_columns])
axes[0, 1].set_title("广告支出箱线图")
axes[0, 1].set_xticklabels(axes[0, 1].get_xticklabels(), rotation=45)

# 直方图：查看销量的分布情况
sns.histplot(ax=axes[1, 0], data=df["Product_Sold"], bins=20, kde=True)
axes[1, 0].set_title("销量分布直方图")
axes[1, 0].set_xlabel("销量")

# 热力图（Heatmap）：查看广告渠道之间的相关性
corr_matrix = df[ad_columns].corr()
sns.heatmap(ax=axes[1, 1], data=corr_matrix, annot=True, cmap="coolwarm", fmt=".2f")
axes[1, 1].set_title("广告渠道相关性热力图")

plt.tight_layout(rect=[0, 0, 1, 0.96])
plt.show()
```

### 结果截图
![数据可视化](https://github.com/ilovescho-O-olsomuch/product-advertising/blob/main/%E6%95%B0%E6%8D%AE%E5%8F%AF%E8%A7%86%E5%8C%96.png)

### 结论
- **散点图** 反映 TV 广告支出与销量的正相关趋势。
- **箱线图** 显示部分广告投入存在极端值，需要重点分析。
- **直方图** 说明销量整体呈正态分布，但可能存在高销量集中的现象。
- **热力图** 直观展示不同广告渠道之间的相关性，可用于优化广告组合策略。

---

## 总结
本次分析通过数据清洗、描述性统计、相关性分析和数据可视化，探讨了广告投入对销量的影响。

- Affiliate Marketing 是最有效的广告渠道，Billboards 和 Social Media 也值得投入。
- Google Ads 和 Influencer Marketing 相关性较低，可能需要优化策略。
- 未来可进行进一步的回归分析，以预测广告投入对销量的具体影响。

---

