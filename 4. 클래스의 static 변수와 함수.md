**클래스 static 변수와 함수 **

일반 static 변수처럼 메모리 구조의 데이터 영역에 저장된다. 딱 한번 초기화 되며, 클래스를 통해 접근 가능하다. 인스턴스가 생성될때 마다 독립적으로 생기는 멤버변수와 다르게 한번만 생성되며 모든 인스턴스에서 하나의 변수에 대해 접근한다. Static 키워드를 붙여 사용한다 const static 멤버의 경우 선언과 동시에 초기화가 가능하다



~~~c++
#include<iostream>

using namespace std;

void print(const char* text)
{
	cout << text << endl;
}

void print(int value)
{
	cout << value << endl;
}

class Person
{
private:
	int m_value;
    // static 변수 선언
	static int static_value;
    // const의 경우 선언과 동시에 초기화 가능
    const static int static_value2 = 1;

public:

	Person() :m_value(0) 
	{
        // 객체 생성시 마다 1씩 증가
		static_value++;
	};

	Person(int value) :m_value(value) {} ;

    // 함수안에서 클래스의 멤버변수를 사용할 수 없다
	static int getStatic_value()
	{
		return static_value;
	}

	~ Person() {} ;
	
};

// static 변수 초기화
int Person::static_value = 0;

int main(int argc, char const *argv[])
{
    // 인스턴스 2개 생성
	Person p1;
	Person p2;

    // 클래스의 static 변수 출력
	print(Person::getStatic_value());

	return 0;
}

~~~

