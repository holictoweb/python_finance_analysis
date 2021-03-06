### 분석 프로세스

- ingest > preprocessing > analysis > backtrading 




#### 이동평균을 이용한 분석 방법 

1. SMA (Simple Moving Average)



2. MA (Exponential Moving Average)
SMA에 단점을 보완해서 나온 것이 EMA이다.
SMA가 과거부터 지금까지 가격을 모두 더해 평균을 낸 것이라면, EMA는 변수를 이용해 최근 값에 영향력을 높이고 과거 값의 영향력을 낮춰 이동평균선의 호라발한 움직음을 보여준다.
- 특징
SMA, EMA 둘다 과거 가격 변동을 기본으로 값을 구하지만 EMA는 최근 값에 가중 변수를 더해 빠르게 가격 반전을 예상하고 반전에 보다 민감하다. 따라서 단기 거래자가 선호한다.

- 계산법
SMA 산출 혹은 전일종가 확인
승수값계산
금일EMA계산
예) 14일 EMA 계산
sma(14) = $46.60, current close price = $46.75
승수 2/(1+n) = 2/(1+14) = 0.133
ema(14)= (current close price x 승수 ) + (yesterday EMA x (1-승수))
= (46.75x0.133)+(46.60x(1–0.133)) = $46.63
처음 EMA를 계산하는 날은 전일 종가 혹은 전일의 SMA로 부터 시작할 수 있다.
EMA계산을 위해 초기값을 필요로 한다.

