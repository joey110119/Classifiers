# Classifiers

## 資料前處理
### x 項目整理 
* 將母 data 的 closeprice 以 list 型態取出，並刪除不必要的欄位，如: 'Close Price', 'Date'。
* 將最後一天的資料刪除，因為若有 n 天，則漲跌數目必只有 n-1 天

### y 項目處理
* 宣告一個 boolean type 的 List，紀錄漲跌
* 將母 data 取出的 closeprice List 逐一 run 過一遍，若後一天大於當天，則 boolean = 1，反之則，boolean = 0

## 使用的 Classifiers 模型
### Logistic Regression
* 使用套件: 
```python=
from sklearn import preprocessing, linear_model
```
### SVM
```python=
from sklearn import svm
```
### NN
```python=
from keras.models import Sequential
from keras.layers import Dense
```

## 討論
### How did you preprocess this dataset ?
如上述

### Which classifier reaches the highest classification accuracy in this dataset ? Why ?
三個模型的套入結果，幾乎是一樣的準確率(50多％)，印出預測結果發現也都是一樣的預測。我想可能會是跟資料量的大小不夠多，或是 feature 不夠多有關。

### Can this result remain if the dataset is different ?
不一定，不同的 dataset 必定會有不一樣適用的模型，自己初次練習時適用過的 iris data 或是網路上常見的鐵答尼號 data，就會有較佳的準確率，推測應該跟資料較完美有關。

### How did you improve your classifiers ?
* 母資料的範圍需要增加
  * 可以使用的 feature
  * 操作的資料年份增加
 
* 資料前處理方式改變
  * 因為漲跌是跟時間有關的現象，所以如果要進行資料前處理的優化，我認為我會優化 x 項目的部份。
  * 某一天的漲跌，我認為一定不會只跟前一天的狀態有關，而是會是一段連續的關係，所以我會使用前10,20天或5天(恰好是一週的股市開盤時間(上班日))的 data 為x，去預測下一次的漲跌(y)，並分析哪樣的 x 可以得到最佳的準確度。如此一來 x 的 feature 必定也會有較多項目可以去建立模型，也能實現隨著時間變化的股市問題。畢竟我認為股市不會是一個點的問題，而會是一段趨勢的問題，所以加入"時間"的性質會是我會想要去做的資料前處理改進。
