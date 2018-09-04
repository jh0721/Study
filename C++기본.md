**C++ 입출력 방식**

> #include <iostream> 헤더파일을 통해 입출력 함수 호출

- cout

- cin

- <<,>> 연산자

.

~~~c++
#include <iostream>

using namespace std;

int main() {

	cout << "test" << endl;

	int value;

	cin >> value;

	cout << "value:" << value << endl;

	return 0;
}

~~~

.

**함수 오버로딩 ( name mangling)**

> 함수이름은 같으나 매개변수타입 또는 개수가 다른경우 name mangling을 통해 다른함수로 선언이 가능하다

.

~~~c++
#include <iostream>

using namespace std;

void overloading(int n)
{
	cout << "n:" << n << endl;
}

void overloading(double d)
{
	cout << "d:" << d << endl;
}

int main() {

	overloading(2);

	overloading(1.2);

	return 0;
}
~~~

.

**매개변수 default**

- 함수의 매개변수를 주지 않을 경우 자동으로 설정되는 값이다

- 매개변수 default 는 함수 선언에만 위치해야한다

- 매개변수 default 값은 매개변수 순서의 뒤쪽부터 채워진다


~~~c++
#include <iostream>

using namespace std;

void func1(int n=2);

void func2(double d1,double d2 , int n2 = 1)
{
	cout << "nd1:" << d1 << endl;
	cout << "d2:" << d2 << endl;
	cout << "n2:" << n2 << endl;
}

//func1함수와 겹치므로 에러가 난다
//void func3()
//{
//    return;
//}

int main() {

    // 함수의 매개변수를 주지 않으므로 default 값이 매개변수로 주어진다
	func1();
    
    func2(1.2,2.1);

	return 0;
}

void func1(int n = 2)
{
	cout << "n:" << n << endl;
}
~~~

.

**Inline 함수**

- 전처리기에서 실행됨 ( 매크로를 함수처럼 사용 가능 )
- 자료형에 대해 제약이 있다 ( 템플릿으로 해결 가능 )

.

~~~c++
#include <iostream>

using namespace std;

inline int SQUARE(int x)
{
	return x*x;
}

void func(int n = 2)
{
	cout << "n:" << n << endl;
}

int main() {

	overloading(SQUARE(23));

	return 0;
}
~~~

.

**Namespace**

- 범위지정연산자(::)를 통해 namespace 범위의 함수 호출가능
- namespace 안에 namespace를 만드는 중첩 가능
- using을 통해 namespace를 명시 가능

.

~~~c++
#include <iostream>

// using 을 통해 namespace 명시
using namespace std;

namespace name1
{
	void func()
	{
		cout << "name1 func" << endl;
	}
}

namespace name2
{
	void func()
	{
		cout << "name2 func" << endl;
	}
}

int main() {

    // 범위지정연산자 :: 를 통해 namespace의 함수 호출
	name1::func();

	name2::func();

	return 0;
}
~~~

.

**자료형 bool ** 

> c++의 참과 거짓을 나타내는 데이터 형이다

~~~c++
bool t = true; 
bool f = false;
~~~

- 크기는 1byte

.

**Reference(참조자)**

> 할당된 변수 메모리 공간에 붙여진 다른 이름을 의미한다

- 참조자 선언

  ~~~C++
  int num1 = 1;
  int &ref = num1;
  ~~~

- 참조하는 값과 항상 같은 값을 갖는다

- 참조자의 수에는 제한이 없으며, 참조자를 대상으로도 참조자를 선언가능

- 참조자 선언과 동시에 초기화가 진행되어야 하며, 반드시 변수를 참조해야 한다 ( NULL초기화도 불가능하다 )

- 참조의 대상 변경이 불가능하다

  ~~~c++
  int num = 2;
  int &ref = num;
  int num2 = 1;
  
  ref = num2; // num = num2 와 동일한 문장
  ~~~

- Call by Reference 



  ~~~c++
  void swap(int &ref1,int &ref2)
  {
      int temp = ref1;
      ref1 = ref2;
      ref2 = temp;
  }
  ~~~





**new 와 delete**

: C++ 에서 객체의 동적할당

