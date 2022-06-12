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
4.美國太空總署和國防部禁止部分C語言使用malloc，寧可事先分配大一點也不願意，到最後發現不夠用
```
## 關於三大主流指令比較 (參考此網站的內容後統整心得 https://www.zhihu.com/question/325968121)
指令|ARM|RISC-V|MIPS    
-----------------------------|-----------------------------|-----------------|-------
營運公司|Acron公司 |RISC-V基金會|MIPS公司
特點|低功耗、低成本|完全開源、架構簡單|簡潔優化的同時，具備高擴展性
代表廠商|蘋果、Google|三星、Intel|龍芯中科


## 動態連結
```
定義:連結器將所有使用的函式庫連結到執行檔中
特點:
1.可以先不需要被連進來
2.而是執行到需要此函式庫才透過連結器尋找並連接函式庫
3.可以省記憶體，因為不用載入全部函式庫
缺點:
可能造成【動態連結地域(DLL hell)的困境】
```
## 關於兩個系統的比較表格如下
比較|Windows                  |Unix/Linux    
-----------------------------|-----------------------------|---------
動態連結檔|DLLs | Share Objects
附檔名|.dll| .so
引入檔|#include<windows.h>|#include<dlfcn.h>
函式庫檔|Kemel32.dll|libdl.so
載入功能|LoadLibrary、LoadLibraryEx|dlopen
取得函數|GetProcAddress|dlsym
關閉功能|FreeLibrary|dlclose
