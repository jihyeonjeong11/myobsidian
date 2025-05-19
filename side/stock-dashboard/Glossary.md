---
created: 2025-05-02T14:15
updated: 2025-05-06T17:27
---
경제용어정리

basic financial 로는 차트 2개 만들 수 있음

```javascript
annual = ['bookValue', 'cashRatio', 'currentRatio', 'ebitPerShare', 'eps', 'ev', 'fcfMargin', 'grossMargin', 'inventoryTurnover', 'longtermDebtTotalAsset', 'longtermDebtTotalCapital', 'longtermDebtTotalEquity', 'netDebtToTotalCapital', 'netDebtToTotalEquity', 'netMargin', 'operatingMargin', 'payoutRatio', 'pb', 'pe', 'pfcf', 'pretaxMargin', 'ps', 'ptbv', 'quickRatio', 'receivablesTurnover', 'roa', 'roe', 'roic', 'rotc', 'salesPerShare', 'sgaToSale', 'tangibleBookValue', 'totalDebtToEquity', 'totalDebtToTotalAsset', 'totalDebtToTotalCapital', 'totalRatio']

['assetTurnoverTTM', 'bookValue', 'cashRatio', 'currentRatio', 'ebitPerShare', 'eps', 'ev', 'fcfMargin', 'fcfPerShareTTM', 'grossMargin', 'inventoryTurnoverTTM', 'longtermDebtTotalAsset', 'longtermDebtTotalCapital', 'longtermDebtTotalEquity', 'netDebtToTotalCapital', 'netDebtToTotalEquity', 'netMargin', 'operatingMargin', 'payoutRatioTTM', 'pb', 'peTTM', 'pfcfTTM', 'pretaxMargin', 'psTTM', 'ptbv', 'quickRatio', 'receivablesTurnoverTTM', 'roaTTM', 'roeTTM', 'roicTTM', 'rotcTTM', 'salesPerShare', 'sgaToSale', 'tangibleBookValue', 'totalDebtToEquity', 'totalDebtToTotalAsset', 'totalDebtToTotalCapital', 'totalRatio']


```


- intraday vps - 뭔지모름 없는듯
- Anlyst Grading - 뭔지모름 없는듯

Previous earning 차트 관련 밸류

|Key|Meaning|
|---|---|
|`eps`|**Earnings Per Share (Annual)** — usually the latest full-year EPS|
|`epsTTM`|EPS over **Trailing Twelve Months** — better for current performance|
|`ebitPerShare`|EBIT (Earnings Before Interest & Tax) per share|
|`epsGrowth3Y`, `epsGrowth5Y`|EPS growth over 3/5 years (compound annual)|
|`epsInclExtraItemsAnnual`|EPS including extraordinary items|
|`epsExclExtraItemsAnnual`|EPS excluding extraordinary items (more useful for comparison)|
|`epsNormalizedAnnual`|Adjusted/normalized EPS (non-GAAP)|
|`epsBasicExclExtraItemsAnnual`|Basic EPS excluding extras|

- previous earning 차트 eps로 만들 수 있음
- Scatter Plot

| Key                     | Meaning                                        |
| ----------------------- | ---------------------------------------------- |
| `salesPerShare`         | Revenue per share (usually annualized)         |
| `revenuePerShareAnnual` | Annual revenue per share                       |
| `revenuePerShareTTM`    | TTM (Trailing Twelve Months) revenue per share |
| `revenueShareGrowth5Y`  | Revenue per share growth over 5 years          |
- Financial metrics 위 값으로 만들 수 있음
- Line Chart


- Financial Estimates - 없는듯
- Peer 관련 - 없는듯
- seasonality = 없는듯
- 


https://finnhub.io/docs/api/insider-transactions 
- 이걸로 인사이드 트레이딩 테이블 만들 수 있음

https://finnhub.io/docs/api/company-news
- 이걸로 컴퍼니 뉴스란 만들 수 있음