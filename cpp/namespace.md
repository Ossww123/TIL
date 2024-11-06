### namespace
std 는 C++ 표준 라이브러리의 모든 함수, 객체 등이 정의된 namespace

namespace는 어떤 정의된 객체에 대해 어디 소속인지 지정해주는 것

같은 이름을 가진 함수라도 namespace가 다르다면 다른 것으로 취급

**권장하는 방식**은 using namespace std; 는 사용하지 않고, std::를 직접 앞에 붙여서 std의 이름공간의 함수이다 라고 명시해 주는 것이 좋다.
- 코딩테스트는 사용하자


**cin**은 **istream** 클래스의 객체로 표준 입력 담당
**cout**은 **ostream** 클래스의 객체로 표준 출력 담당

C++에서는 이름 공간에 굳이 이름을 설정하지 않아도 된다.
이 경우 해당 이름 공간에 정의된 것들은 해당 파일 안에서만 접근할 수 있게 된다. **static**키워드를 사용한 것과 같은 효과.
```
#include <iostream>

namespace {
// 이 함수는 이 파일 안에서만 사용할 수 있습니다.
// 이는 마치 static int OnlyInThisFile() 과 동일합니다.
int OnlyInThisFile() {}

// 이 변수 역시 static int x 와 동일합니다.
int only_in_this_file = 0;
}  // namespace

int main() {
  OnlyInThisFile();
  only_in_this_file = 3;
}
```
