# 上課後，根據老師上課內容，自己進行整理
# 環境設定
```
安裝 MSYS2
建議使用 MSYS2 MinGW X64
如果沒有安裝gcc也可以在裡面進行安裝
```
# 1-1系統軟體
## 何謂系統程式

### System Software(系統軟體)
```
軟體設計為了--->設計師--->系統軟體
軟體設計為了--->普羅大眾--->應用軟體
```
系統軟體                       |應用軟體     
-----------------------------|-----------------------------
組譯器 | 試算表 EXCEL
載入器 | 排版軟體 WORD
連結器 | 瀏覽器 IE Firefox Chrome
巨集處理器 | 
編譯器 | 
直譯器 | 
虛擬機 | 
### System Programming(系統程式設計)
```
負責處理作業系統或是電腦系統的程式設計技術
EX:linux系統程式、Windows系統程式
```
### 系統軟體 V.S. 系統程式
* 系統軟體主要指的是輔佐系統程式能夠在電腦上執行或執行特定工作 (例如除錯、行程排班) 等等的工具程式。
* 系統程式泛指與計算機系統相關的程式設計，例如嵌入式系統、組合語言程式設計、C 語言程式設計、Linux 核心程式設計等等。

# 1-2系統程式與系統軟體 

## 程式編譯、組譯、連結、載入流程
![image](https://user-images.githubusercontent.com/81726807/173243945-e3b4d814-efab-42c7-8cd6-7250d522a4ce.png)

```
我們在看主程式會發現有一個sum.h 
往下找會sum.h這是函式庫
但gcc會自動合併，所以主程式執行時能夠使用我們自創的函式庫
編譯加連結指令 gcc main.c sum.c -o run
執行指令 ./run
```
![image](https://user-images.githubusercontent.com/81726807/173248750-27144918-92dc-47ef-bcee-ebf9b695475f.png)
![image](https://user-images.githubusercontent.com/81726807/173248771-ecd9f369-2deb-4258-a5b6-38965b5e7a24.png)
## 使用GCC產生組合語言

```
gcc -S hello.c -o hello.s   # 會編譯成組合語言檔

gcc -S main.c -o main.s
```
* gcc指令集: https://gcc.gnu.org/onlinedocs/gcc-11.2.0/gcc/Option-Summary.html#Option-Summary
