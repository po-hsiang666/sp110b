# lexer
```
#include <stdio.h>
#include <string.h>
#include <ctype.h>

#define TMAX 10000000  
#define SMAX 100000

enum { Id, Int, Keyword, Literal, Char };

char *typeName[5] = {"Id", "Int", "Keyword", "Literal", "Char"};

char code[TMAX];
char strTable[TMAX], *strTableEnd=strTable; // 創建一個字符列表，後面的pointer代表迭代位置
char *tokens[TMAX];
int tokenTop=0;
int types[TMAX];

// define 函數會加上誇號()，函數的值會直接return到前面
#define isDigit(ch) ((ch) >= '0' && (ch) <='9')  

#define isAlpha(ch) (((ch) >= 'a' && (ch) <='z') || ((ch) >= 'A' && (ch) <= 'Z'))

int readText(char *fileName, char *text, int size) {  // 使用C語言讀檔案
  FILE *file = fopen(fileName, "r");
  int len = fread(text, 1, size, file);
  text[len] = '\0';
  fclose(file);
  return len;
}

/* strTable =
#\0include\0"sum.h"\0int\0main\0.....
*/
char *next(char *p) {
  while (isspace(*p)) p++;

  char *start = p; //         include "sum.h"
                   //         ^      ^
                   //  start= p      p
  int type;
  if (*p == '\0') return NULL;
  if (*p == '"') {
    p++;
    while (*p != '"') p++;
    p++;
    type = Literal;
  } else if (*p >='0' && *p <='9') { // 數字
    while (*p >='0' && *p <='9') p++;
    type = Int;
  } else if (isAlpha(*p) || *p == '_') { // 變數名稱或關鍵字
    while (isAlpha(*p) || isDigit(*p) || *p == '_') p++;
    type = Id;
  } else { // 單一字元
    p++;
    type = Char;
  }
  int len = p-start;
  char *token = strTableEnd;  // token紀錄開始位置
  // strncpy 可以把start的位置往後len存到前面的 starTableEnd(pointer) 裡面
  strncpy(strTableEnd, start, len);  
  strTableEnd[len] = '\0';  // printf遇到這個會自動停止
  strTableEnd += (len+1);  // 迭代到下一個位置
  types[tokenTop] = type;
  tokens[tokenTop++] = token;
  printf("token=%s\n", token);
  return p;
}

void lex(char *code) {  // 程式主要運行的地方
  char *p = code;
  while (1) {
    p = next(p);
    if (p == NULL) break;
  }
}

void dump(char *strTable[], int top) {
  for (int i=0; i<top; i++) {
    printf("%d:%s\n", i, strTable[i]);
  }
}

int main(int argc, char * argv[]) {
  readText(argv[1], code, sizeof(code)-1);
  puts(code);  // 打印一次，看到程式長怎樣
  lex(code);
  dump(tokens, tokenTop);
}
```
利用字元指標陣列將檔案中的字串一個一個讀出

利用空白當做字串分割的基準
# result
```
PS C:\Users\rick2\sp\03-compiler\02-lexer> gcc lexer.c -o lexer
PS C:\Users\rick2\sp\03-compiler\02-lexer> ./lexer sum.c
#include "sum.h"

int main() {
  int t = sum(10);
  printf("sum(10)=%d\n", t);
}
token=#
token=include
token="sum.h"
token=int
token=main
token=(
token=)
token={
token=int
token=t
token==
token=sum
token=(
token=10
token=)
token=;
token=printf
token=(
token="sum(10)=%d\n"
token=,
token=t
token=)
token=;
token=}
0:#
1:include
2:"sum.h"
3:int
4:main
5:(
6:)
7:{
8:int
9:t
10:=
11:sum
12:(
13:10
14:)
15:;
16:printf
17:(
18:"sum(10)=%d\n"
19:,
20:t
21:)
22:;
23:}
```
