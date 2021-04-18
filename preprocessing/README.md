#### finance data preprocessing


#### Ingest finance Data

1. raw data

```python
# install yfinance
pip install yfinance

import yfinance as yf

edate = datetime.datetime(2021, 3,31) 
amzn = yf.Ticker("AMZN")
amzn_df = yf.download('AMZN', start=sdate, end=edate)
```

2. 파생데이터 생성
  - price moving average
  - volume moving average
  -  
