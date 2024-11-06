포인터 : 메모리 상에 위치한 특정한 데이터의 (시작)주소값을 보관하는 변수

정의 방법
(포인터에 주소값이 저장되는 데이터의 형)* (포인터의 이름);
(포인터에 주소값이 저장되는 데이터의 형) *(포인트의 이름);
```
int* p;
int *p;
```

단항 **&**연산자는 피연산자의 주소값을 불러 온다.
```
#include <stdio.h>
int main() {
  int a;
  a = 2;

  printf("%p \n", &a); # 0x00007ffe37d03104
}
```

```
/* 포인터의 시작 */
#include <stdio.h>
int main() {
  int *p;
  int a;

  p = &a;

  printf("포인터 p 에 들어 있는 값 : %p \n", p);
  printf("int 변수 a 가 저장된 주소 : %p \n", &a);

  return 0;
}
```
