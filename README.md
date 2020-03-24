# aia_fxprice
AIA RNN Kaggle 

透過training data預測最後30筆收盤價

## 資料包括之欄位如下:
- Time : 日期與時間 string 第幾天與幾點 ex. "100 17:30:00" 第 100 天的下午五點半之資料
         日期已去識別化但仍保有大小關係，如第 100 天若為 2019/6/1 星期六，則第 107 天為 2019/6/8 星期六
- Weekday: 星期幾 0 ~ 6 分別為星期一 ~ 星期天
- Open : 開盤價
- High : 高點
- Low : 低點
- Close : 收盤價
- Volume : 成交量

training_set 中為第 170 天到 895 天之間每 10 分鐘一筆之資訊
目標為預測第 895 天 19:00 ~ 24:00 之間每 10 分鐘一筆之收盤價 (共 30 筆)

Metrics：MAE
Baseline:0.00194

## 實作說明

- GRU_X.ipynb 
使用GRU Model: 0.0074
Window產生一筆預測值後，帶入新的Window再產生下一筆預測值
