# 老師講解語法(出自老師講義 genEnglish.c)
```
#include "rlib.h"

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
  printf("%s", randSelect(n, 2));
}

void V() {
  printf("%s", randSelect(v, 2));
}

void DET() {
  printf("%s", randSelect(det, 2));
}

void NP() {
  DET();
  printf(" ");
  N();
}

void VP() {
  V();
  printf(" ");
  NP();
}

void S() {
  NP();
  printf(" ");
  VP();
  printf("\n");
}

int main() {
  timeSeed();
  S();
}
```


