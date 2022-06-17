# Unix家族的演變
![image](https://user-images.githubusercontent.com/81726807/174232713-f160bc51-9c0d-4b42-99ab-b973a73b3535.png)
# Unix
```
UNIX作業系統，是一個強大的多使用者、多工作業系統，支援多種處理器架構，按照作業系統的分類，屬於分時作業系統，
最早由肯·湯普遜、丹尼斯·里奇和道格拉斯·麥克羅伊於1969年在AT&T的貝爾實驗室開發。
目前它的商標權由國際開放標準組織所擁有，只有符合單一UNIX規範的UNIX系統才能使用UNIX這個名稱，否則只能稱為類UNIX（UNIX-like）

```
# 多工
```
多工系統利用中斷機制避免當機，在作業系統將CPU交給一個行程之前，先設定中段時間點，以便當行程霸佔CPU時，作業系統能透過中斷機制取回CPU控制權，如此就能避免行程佔據CPU不放的行為。

中斷點通常0.1秒就會一次，所以一秒就可以輪10個行程。
```
# POSIX (Portable Operating System Interface)(可移植作業系統介面)
```
1.IEEE為要在各種UNIX作業系統上執行軟體，而定義API的一系列互相關聯的標準的總稱。
2.正式稱呼為IEEE Std 1003，而國際標準名稱為ISO/IEC 9945。
```