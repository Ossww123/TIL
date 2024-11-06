포인터 : 메모리 상에 위치한 특정한 데이터의 (시작)주소값을 보관하는 변수

정의 방법
(포인터에 주소값이 저장되는 데이터의 형)_ (포인터의 이름);
(포인터에 주소값이 저장되는 데이터의 형) _(포인트의 이름);

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

**\*연산자**는 주소에 해당하는 데이터를 의미

### 포인터에는 왜 타입이 있을까

64비트 시스템에서는 포인터는 8바이트인데 왜 타입이 있을까
-> 값을 할당하려 할 때 컴퓨터 메모리에서 얼마만큼을 읽어들어야 할 지 알 수 없기 때문

### 상수 포인터

```
/* 상수 포인터? */
#include <stdio.h>
int main() {
  int a;
  int b;
  const int* const pa = &a;

  *pa = 3;  // 올바르지 않은 문장
  pa = &b;  // 올바르지 않은 문장

  return 0;
}

# const int *pa => pa가 가리키는 값이 변하면 안 됨!
# int* const pa => pa가 저장하고 있는 주소값이 변하면 안 됨!
```

### 포인터의 덧셈

포인터의 값에 +1을 하면?
타입에 따라서 주소값에 더해짐 (ex- int라면 +4)

포인터끼리 더하기는 안 됨. 하는 의미도 없음
뺄셈은 됨. Why? 다음시간에..

```
/* 과연? */
#include <stdio.h>
int main() {
  int arr[10] = {1, 2, 3, 4, 5, 6, 7, 8, 9, 10};
  int* parr;
  int i;
  parr = &arr[0];

  for (i = 0; i < 10; i++) {
    printf("arr[%d] 의 주소값 : %p ", i, &arr[i]);
    printf("(parr + %d) 의 값 : %p ", i, (parr + i));

    if (&arr[i] == (parr + i)) {
      /* 만일 (parr + i) 가 성공적으로 arr[i] 를 가리킨다면 */
      printf(" --> 일치 \n");
    } else {
      printf("--> 불일치\n");
    }
  }
  return 0;
}

# 결과로는 모두 일치가 나온다.
```

```
#include <stdio.h>
int main() {
  int arr[3] = {1, 2, 3};

  printf("arr 의 정체 : %p \n", arr);
  printf("arr[0] 의 주소값 : %p \n", &arr[0]);

  return 0;
}

# 두 개가 같은 값이 나온다.
# 그렇다고 arr == &arr[0] 인 것은 아님!
```
