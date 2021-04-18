##### backtrader를 통한 backtesting

|type|detail|source file|
|-----|------------|----|
|basic|기본사용 방법 |[link](https://github.com/holictoweb/python_finance_analysis/blob/master/backtrader/backtrader_basic_01.ipynb)|
|smastretagy||[link](https://github.com/holictoweb/python_finance_analysis/blob/master/backtrader/backtrader_SmaStrategy.ipynb)|
|볼린저밴드||[link]()|



#### Cerebro

- add_signal / addstrategy 메소드를 사용해 신호/전략을 추가 한다. 
  - cerebro.addstrategy()를 사용하는 대신 optstrategy()를 써어 전략 이름과 매개 변수 값을 제공 가능
  ```
  cerebro.optstrategy(SmaStrategy, ma_period=range(10, 31))
  ```
- 코어 개수 지정 가능
  ```
  cerebro.run(maxcpu=4) 
  ```
- addobserver 를 사용해 관찰자 추가. 
  - BuySell - 매수/매도 (파란 빨간 삼각형으로 표시) 
  - Value - 시간에 따른 포트폴리오 가치의 변화를 추적
- 


|type|detail|
|----|----------|
|bt.signal|신호는 숫자로 표시 되며 특정 신호 ( 현재 데이터와 이동평균의 차이 ) 를 지정하고 표시 할 수 있음 |
|bt.Strategy|여러 신호를 결합하여 동작을 지정 할 수 있음. |
