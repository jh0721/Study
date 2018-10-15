**접근제어자 private**

Private 접근제어자는 클래스 안에서만 접근이 가능한 접근제어자 이다. 여기서 접근제어의 기준은 인스턴스 생성당시가 아니라 클래스를 기준으로 한다



~~~C++
#include <iostream>

using namespace std;

class Person
{
private:
	int m_age;
	const char* m_name;
public:
    // 생성자
	Person(int age,const char* name): m_age(age),m_name(name) {};
	// 복사 생성자
	Person(const Person &copy):m_age(copy.m_age),m_name(copy.m_name) {};

};

int main() {

	Person p1(13,"test");
	Person p2(p1);

	return 0;

}
~~~



이 코드의 복사생성자에서는,

~~~C++
// 복사 생성자
Person(const Person &copy):m_age(copy.m_age),m_name(copy.m_name) {};
~~~

Copy 인스턴스의 private으로된 멤버변수에 바로 접근하여 값의 복사가 가능하다. 접근제어자의 접근 제어 기준은 그때 그때 생성된 인스턴스의 기준이 아니라 클래스 기준이기 때문이다. 따라서 서로 다른 인스턴스이더라도 그 인스턴스가 동일한 클래스 타입이면 각 멤버는 서로의 private 멤버 변수에 접근이 가능하다. 만일 private 접근지정자가 클래스가 아닌 인스턴스 기준이라면 C++에서 기본적으로 제공해 주는(그래고 사용자 정의도 가능한) 복사생성자와 대부분의 연산자 오버로딩은 애초에 존재할 수가 없게 된다.

