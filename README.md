# Position Completion Based on 

## Data Description

In China, mutual fund reports are published seasonally. However, complete position would not be reported except annual report and semi annual report. In the first and third season, top 10 heavyweight stocks and industry distribution is the information you can get. In the position chasing, invisible trading ability estimation, a complete position is must.

- IndValueToFundNAV:每期报告行业占基金净值比
- ChinaMutualFundStockPortfolio:组合持仓的报告期数据
- StkValuetToFundNAV:基金股票资产占比
- IndustryValueToNAV:每期报告行业占基金净值比
- StkActualPublishDate:股票公告实际发布日期
- FundActualPublishDate:基金公告实际发布日期
- MonthBeginEnd:月初月末表
- StkIndustry:股票行业归属
- FundType:基金类型
- PctStkTotalNAV:基金股票投资总净值
- FundFullName:基金简称和基金全称
- StkBondFundList:偏股混合型基金列表
- StkFundList:普通股票型基金列表
- AShareEODPricesPivot:A股所有股票的收盘价
- LeftStkPricePivot:补充的股票收盘价
- IncomeTTM:用作自下而上的单因子策略的因子，未必是有效的因子
- BaseIndex:偏股混合型基金指数，基准

## Method

- For 1st or 3rd season,  $\omega_{i,t}$ is the simulated proportion of each stock (for $i$ = 1...10, the exact proportion is know), and $E_{t}$ is the holding information. 
- For $t-1$, complete position can be obtained ($E_{t-1}$ is known), and we have those in $E_{t-1}$ but not in $E_t$(for $t$ from 1 to 10), denotes $e_t$. This is the stocks we need to allocate proportion to.
- Denotes $I_{t,j}$ is the net value of industry $j$ divided by the net value of portfolio in $t-1$
- According to 
- 
- 

## Compare the Real and Simulated NAV

Although some results are not satisfactory, most simulated NAVs are so similar to that of the real.

![000083](./Output/NavBiasPlot/000083.png)

![001039](C:\Users\93973\Desktop\工作文件\中信证券\18.持仓补全\Output\NavBiasPlot\001039.png)

## Defects and Improvements

- We complete the position based on stocks only, which means other asset types are excluded (bonds, etc).  There might be a huge gap between the real net-value and the net-value derived from the simulated weights of stock in the portfolio occasionally, but they have a high spearman correlation most of the time. 
- Buys and sells of portfolio manager should be chased. However, I suppose the $w_{i,t}$ is constant. 

