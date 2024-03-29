# class vs object vs instance
## 클래스 
    객체를 생성하기 위한 설계도이다.
    클래스는 객체가 가질 멤버변수(필드)와 메서드를 정의한다.
## 객체(오브젝트)
    객체는 클래스에 정의 된 멤버변수와 메서드를 가진 실체이다.
    모든 객체는 서로 독립적이다.
## 인스턴스
    객체와 같은 정의를 가지지만 클래스와의 관계가 부각된 개념이다.
    즉 student = new Student()에서 
    student 인스턴스는 Student클래스의 인스턴스이다.
    모든 인스턴스는 객체이다.

# Procedural vs object_oriented => oop1
## 절차 지향
    데이터와 데이터를 다루는 연산이 분리 되어있다.
    '어떻게' 실행 할 것인가에 더 초점이 맞추어 져있다.
## 객체 지향
    데이터와 데이터를 다루는 연산이 캡슐화 되어있다.
    '무엇'에 초점이 실려있고, 객체 간의 관계가 더 중요하다. 

# 생성자 && this
## 생성자가 필요한 이유
    필요한 필드가 null 값이 아님을 보장 할 수있다.
    불필요한 초기화 함수를 작성하는 비용을 아낄 수 있다.
## this와 오버로딩
    아무런 생성자를 작성하지 않으면 자바가 제공하는 기본 생성자를 사용한다.
    하지만 파라미터를 넘겨 받고 다른 생성자를 이용할때 
    필드의 값과 같을 수 있다. 그 경우 클래스의 필드와 구분하기 위하여 this를 사용한다.
    
    또한 this()를 통하여 미리 정의한 생성자를 재활용 할 수 있다.
    이때 this()는 반드시 생성자의 첫번쨰 줄에 와야한다.

# 접근 제한자
## private -> default(package-private) -> protected -> public 
    private: 같은 클래스 내에서만 접근할 수 있다. 
    default(pacakge private): 같은 클래스와 패키지 내에서만 접근할 수 있다. 
    protected:  같은 패키지이거나, 상속 받은 경우에만 접근할 수있다.
    public: 모든 외부 호출을 허용한다.
## class 접근 제한자 default -> public
    public class 는 파일 이름과 같아야하고 파일 하나에 단 하나만 생성가능하다.
    default class는 파일 이름과 무관하게 지을수 있으나, 다른 패키지에서 직접 호출할 수 없다.
    단 public class 내에서 default 클래스를 활용하는 메서드의 경우 외부에서 호출 가능하다.

# Static && java 메모리 구조
## java 메모리 구조 (stack, heap, 메서드 영역)
### stack
    함수 호출시 스레드 마다 생성되는 영역이다.
    함수의 파라미터와 지역변수가 담긴다.
    함수 종료후 바로 제거된다.
### heap
    new 연산자를 통하여 생성된 인스턴스를 담는 영역이다.
    자바는 레퍼런스 체크를 통하여 힙영역이외의 어떤 참조값을 가지지 않을때
    GC를 통하여 메모리에서 제거한다.
    힙의 인스턴스는 메서드를 가지지 않고 오직 멤버변수만 가진다.
    메서드는 모든 인스턴스에 거쳐 중복되기 때문이다.
### method
    정적영역, 클래스 영역, 상수풀로 구성된다.
    정적영역-> 클래스의 static 변수와 메서드를 저장한다.
    클래스 영역 -> 클래스의 메서드를 담는다.
    상수풀 -> 여러번에 거쳐 중복되는 String등의 값을 저장하여 사용한다.

## static
    앞서 살펴본 자바 메모리 구조에서 프로그램 실행에 필요한 공통의 데이터를 보관 하는 영역인
    메서드 영역의 static(정적 영역) 영역에는 인스턴스 생성을 할 필요 없이
    클래스로 부터 바로 참조할 수있는 멤버 변수와 메서드가 있다.
    
    스태틱 메서드의 경우 정적 변수와 정적 메서드만 참조가 가능하다.
    만일 하나의 자바 파일 내에서 다수의 정적 메서드 호출이 필요하다면 
    'import static Class.*'로 모든 메서드나 정적 변수 참조가 가능하다.

# 다형성
## 다형적 참조
    부모타입을 상속받은 인스턴스 내부의 부모 인스턴스 타입으로 상속받은 계통 아래의 모든 다양한 타입을
    참조할 수 있도록 하는 것이다.
## 캐스팅
### 다운캐스팅
    부모타입으로 자식 인스턴스를 참조하고 있는 경우 자식 클래스의 속성과 메서드를 참조하기 위해
    참조 타입을 자식타입으로 반환해주는 연산이다.
    
    자식 인스턴스의 메소드를 호출하기 위해 자식타입으로 변수할당을 하지 않고 연산만 적용하는 것을
    '일시적 다운 캐스팅'이라한다.
    
    다운캐스팅은 순수한 부모 인스턴스가 상속받은 하위 타입으로 다운캐스팅 하는 경우 
    'ClassCastException' 런타임 익셉션을 발생시킬 수 있다.
### instanceof && pattern mathing for instanceof
    instanceof 연산자를 통하여 자식타입의 인스턴스인지 검사하고 다운캐스팅을 진행하여 
    ClassCastException 런타임 익셉션을 방지할 수 있다.
### 업캐스팅
    자식 인스턴스는 생성될 때 항상 부모 인스턴스를 먼저 생성 완료한 후에 생성되므로
    참조할 부모타입 인스턴스가 있으므로 항상 안전하다.
## overriding && polymorphism
    객체지향은 캡슐화 / 상속 / 다형성의 특징을 가진다.
    다형성은 객체를 여러타입으로 참조할 수 있음을 의미하고
    다형성은 다형적 참조와 오버라이딩(최우선 메서드 참조)를 통하여 완성된다.