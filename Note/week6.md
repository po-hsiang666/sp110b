# X86的堆疊

![image](https://user-images.githubusercontent.com/81726807/174192317-306c6daa-623b-4572-8e1a-c2900040906c.png)

![image](https://user-images.githubusercontent.com/81726807/174192727-8c7a1d7d-0e04-4595-aa8b-bd16d75a153b.png)


```
是由高位置漲低位置SP指標往下減，有些電腦習慣從低到高要特別注意(少數。)
進去foo這個函數後會發生，它會將返回點放進去，但呼叫前已經把參數推進去了77 88 99
所以當我戶叫foo時已經推到a b c
RSP是64位元
ESP是32位元圖片上的這個就是
```
