# 如何避免寫出悲劇的C語言(範例出自老師WEEK2影片教材中)

![image](https://user-images.githubusercontent.com/81726807/173249886-a7d2ce19-bb3f-419c-b087-45fe0862bd14.png)
![image](https://user-images.githubusercontent.com/81726807/173250217-b162f8b9-568f-4265-91d8-054ca3eaad29.png)

## 關於錯誤額外補充
```
錯誤1 是沒有給C的大小
錯誤2 是邊議會過，但不會得到我們想要的陣列大小，而是得到指標大小
錯誤3 不能使用中括號[]要用大括號{}
錯誤4 不能印出陣列只會印出指標
```
## malloc
```
1.malloc的問題是過度使用，會造成記憶體縫隙過多
2.且分配過多會造成執行速度慢，容易造成malloc失敗
3.因為每次都要檢查malloc是否有成功，會耗費大量時間
```
