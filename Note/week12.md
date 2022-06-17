# FileSystem
```
下面的程式碼都要在Linux環境下執行

Linux 標準輸入: 0、標準輸出: 1、標準錯誤: 2
```
# IO
## io1.c
```
#include <stdio.h>
#include <unistd.h>
#include <sys/types.h>
#include <sys/stat.h>
#include <fcntl.h>
#define SMAX 128

int main() {
  // unix 預設系統函數: open read write
  // O_CREAT檔案不存在就創造，檔案存在就開啟，O_RDWR代表檔案可讀可寫
  int a = open("a.txt", O_RDWR);  // C 語言標準函式庫 fopen()，傳回file*
  int b = open("b.txt", O_CREAT|O_RDWR, 0644); // 後面的數字代表權限 rw-r--r--
  char text[SMAX];
  int n = read(a, text, SMAX);  // 代表讀了幾個bytes // C 語言標準函式庫 fread()
  printf("n=%d\n", n);  
  write(b, text, n);
  printf("a=%d, b=%d\n", a, b);  // a=3, b=4 (0~2被IO占掉了)
}
```
