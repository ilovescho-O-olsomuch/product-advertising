## 数据分析报告

### 描述性统计

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

#### 结论：广告投入分布情况：

各广告渠道（TV、Billboards、Google Ads、Social Media、Influencer Marketing、Affiliate Marketing）的 **均值 (mean)** 和 **中位数 (50%)** 相对接近，说明数据的对称性较好，分布较均匀。

**标准差 (std)** 较大，例如 TV 约为 287.57，Google Ads 约为 284.06，表明不同广告支出之间的波动较大，可能存在极端值。

**最小值** 和 **最大值** 差距较大，例如 Influencer Marketing 的最小值仅 0.77，而最大值达 999.83，说明有一些广告投入非常少或非常多的情况。

#### 销量 (Product_Sold) 分布情况：

**均值 (7045.85)** 和 **中位数 (7054.00)** 接近，表明销量数据接近正态分布。

**标准差 (1639.95)** 相对较大，说明销量数据存在一定的波动。

**最小值 (3141)** 和 **最大值 (11210)** 显示销量在 3000 到 11000 之间变动，存在一定的差异，但没有明显的极端值。

#### 广告投入对销量的影响可能性：

由于广告投入的标准差较高，可能存在一些广告投放过高但销量一般的情况，需要进一步分析相关性。

可能需要分析广告投入与销量的相关性，以确定哪些广告渠道对销量贡献最大。

### 相关性分析

```python
import pandas as pd

# 读取清洗后的数据
cleaned_file_path = r"C:\Users\32165\Desktop\Advertising_Data_Cleaned.csv"
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

#### 结论

* **Affiliate_Marketing (0.603713)**：
    * 关联性最高，说明该渠道的广告投入与产品销量之间存在较强的正相关关系。
    * 可能是因为该渠道能精准触达目标消费者，带来直接的转化。

* **Billboards (0.460435)** 和 **Social_Media (0.378546)**：
    * 这两个渠道的相关性较高，说明它们的广告投入对销量也有一定的推动作用。
    * 传统的户外广告（Billboards）和社交媒体广告（Social Media）都能影响消费者的购买决策。

* **TV (0.364474)**：
    * 电视广告的相关性略低于户外广告和社交媒体，可能是因为电视广告的受众广泛，但转化率不如精准营销方式。

* **Google_Ads (0.199640)** 和 **Influencer_Marketing (0.121457)**：
    * 相关性较低，可能是由于广告策略不够精准，或者消费者在这些平台上的购买路径较长，难以直接转化为销量。

**总结：**

* Affiliate Marketing 是最有效的广告渠道，投入较多时销量也显著增加，应重点优化该渠道的策略。
* Billboards 和 Social Media 也值得投入，可以结合其他广告形式增强影响力。
* Google Ads 和 Influencer Marketing 效果较弱，可能需要优化广告内容、目标受众或营销策略，以提高转化率。
```
