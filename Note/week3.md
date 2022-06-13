# 老師講解語法(出自老師講義 https://gitlab.com/ccc110/sp/)
```
#include "rlib.h" #亂數函式庫

// === EBNF Grammar =====
// S = NP VP #S代表句子 
// NP = DET N #NP代表名詞子句
// VP = V NP #VP代表動詞子句
// N = dog | cat #N是名詞
// V = chase | eat #V是動詞
// DET = a | the #DET是定詞

char* n[] = {"dog", "cat"};
char* v[] = {"chase", "eat"};
char* det[] = {"a", "the"}; 

void N() {
  printf("%s", randSelect(n, 2));  #隨機選一個印出來2選1
}

void V() {
  printf("%s", randSelect(v, 2)); #隨機選一個印出來2選1
}

void DET() {
  printf("%s", randSelect(det, 2));  #隨機選一個印出來2選1
}

void NP() {
  DET();
  printf(" "); #中間空白防止連一起
  N();
}

void VP() {
  V();
  printf(" "); #中間空白防止連一起
  NP();
}

void S() {
  NP();
  printf(" "); #中間空白防止連一起
  VP();
  printf("\n");
}

int main() {
  timeSeed(); #用時間當亂數種子來隨機換避免一樣
  S();
}
```
![image](https://user-images.githubusercontent.com/81726807/173265715-7a58971e-07b7-43e2-ab49-108af1274a52.png)
![image](https://user-images.githubusercontent.com/81726807/173265769-91f9450a-a1fd-4b28-a71f-73695345d3ce.png)

查閱網路資料後，發現windows系統在gcc genEnglish.c rlib.c後會產生.exe檔而不是.out



