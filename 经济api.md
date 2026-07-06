# Macro Dashboard API Guide

> Version: v1.0
> Author: ChatGPT
> Goal: 构建一个免费的全球宏观经济 Dashboard，重点关注能源、俄罗斯、中国及全球流动性。

---

# 一、整体架构

```
Dashboard
    │
    ▼
Python 数据处理
    │
    ▼
各种官方 API
    │
    ▼
SQLite / PostgreSQL
```

推荐技术栈：

- Python
- requests
- pandas
- sqlite
- plotly
- Dash / Streamlit

---

# 二、推荐 API（★★★★★）

## 1. FRED（圣路易斯联储）

推荐指数：★★★★★

官网：

https://fred.stlouisfed.org/

API：

https://fred.stlouisfed.org/docs/api/

特点：

- 免费
- API稳定
- Python库成熟

可获取：

- CPI
- PPI
- GDP
- M2
- 利率
- 美债收益率
- Brent
- WTI
- VIX
- 美元指数

Python：

```python
from fredapi import Fred

fred = Fred(api_key="YOUR_API_KEY")

oil = fred.get_series("DCOILBRENTEU")
```

更新：

Daily / Weekly / Monthly

---

## 2. World Bank API

★★★★★

官网：

https://data.worldbank.org/

API：

https://api.worldbank.org/

特点：

- 免费
- 不需要API Key

数据：

- GDP
- 人口
- 能源
- 出口
- 进口
- 教育

更新：

Quarterly / Yearly

---

## 3. IMF API

★★★★★

官网：

https://www.imf.org/

数据：

- 汇率
- CPI
- 财政
- 经常账户
- 国际收支
- 外债

特点：

全球国家覆盖。

---

## 4. OECD API

★★★★★

官网：

https://www.oecd.org/

数据：

- 工业
- 就业
- 通胀
- 生产率

---

# 三、能源数据

## EIA（美国能源署）

★★★★★

官网：

https://www.eia.gov/

API：

https://www.eia.gov/opendata/

数据：

- Brent
- WTI
- 天然气
- 原油库存
- 出口
- 页岩油

免费。

推荐研究：

- 中国神华
- 石油
- 天然气

---

## OPEC

★★★★★

官网：

https://www.opec.org/

重点：

Monthly Oil Market Report

主要关注：

- 全球供需
- OPEC产量
- 库存

---

# 四、金融市场

## Alpha Vantage

★★★★☆

官网：

https://www.alphavantage.co/

数据：

- 股票
- ETF
- 黄金
- 外汇
- 指数

免费额度：

每天500次左右。

---

## Finnhub

★★★★★

官网：

https://finnhub.io/

数据：

- 新闻
- 财报
- 宏观
- 股票

免费额度充足。

---

## Polygon

★★★★★

官网：

https://polygon.io/

适合：

美股

期权

实时行情

---

# 五、俄罗斯专属

## Russian Central Bank（CBR）

★★★★★

官网：

https://www.cbr.ru/

数据：

- 利率
- 卢布
- 银行贷款
- 外汇储备
- 货币供应

推荐指数：

★★★★★

---

## Rosstat

★★★★★

官网：

https://rosstat.gov.ru/

数据：

- CPI
- PPI
- 工业
- 工资
- 人口
- 建筑
- 房地产
- 农业

很多数据：

CSV

Excel

开放下载。

---

## Russian Ministry of Finance

官网：

https://minfin.gov.ru/

重点：

- 财政收入
- 财政支出
- 赤字
- 国家财富基金

---

# 六、另类数据（Alternative Data）

## Google Trends

用途：

观察：

- 失业
- 房价
- 移民
- 战争

---

## MarineTraffic

用途：

观察：

俄罗斯出口

油轮运输

港口吞吐

---

## AIS Ship Data

用途：

石油运输

煤炭运输

航运指数

---

## Flightradar24

用途：

观察：

国际航班恢复

航空需求

---

# 七、推荐的数据比例

```
30%
能源

- Brent
- WTI
- 天然气
- 黄金
- 煤炭

-------------------

25%
俄罗斯

- 财政
- 利率
- CPI
- PPI
- 卢布
- 财富基金

-------------------

20%
全球流动性

- 美联储
- ECB
- BOJ
- M2
- 美债收益率

-------------------

15%
中国

- PMI
- 社融
- 房地产
- 煤炭
- 航运

-------------------

10%
另类数据

- AIS
- Google Trends
- News
```

---

# 八、推荐数据库结构

```
macro-dashboard/

config/

fred.yaml

worldbank.yaml

imf.yaml

eia.yaml

oecd.yaml

tradingeconomics.yaml

cbr.yaml

rosstat.yaml

fetchers/

fred.py

worldbank.py

imf.py

eia.py

database/

sqlite.db

dashboard/

streamlit.py
```

---

# 九、推荐指标（Dashboard）

★★★★★

能源

- Brent
- WTI
- Urals
- 天然气
- 黄金
- 铜

★★★★★

俄罗斯

- 利率
- CPI
- PPI
- PMI
- 财政赤字
- 国家财富基金
- 卢布
- 工资
- 外汇储备

★★★★★

全球

- 美债收益率
- M2
- 美元指数
- VIX

★★★★★

中国

- PMI
- 社融
- M2
- 房地产销售
- 煤炭价格
- 航运指数

---

# 十、最终目标

建立一个属于自己的 Macro Dashboard，而不是仅关注俄罗斯。

建议长期维护约 30~50 个核心指标，覆盖：

- 全球流动性
- 能源
- 地缘政治
- 中国经济
- 美国经济
- 欧洲经济
- 俄罗斯经济
- 航运
- 商品
- 另类数据

最终形成一个类似 Bloomberg Terminal 的轻量版宏观分析系统。
