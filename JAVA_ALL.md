## <strong>이지훈의 java 총 정리</strong>



#### 메모리 공간 활용을 위해 필요한 변수

1. 데이터의 저장과 참조를 위해 '할당된 메모리 공간'에 붙인 이름을 '변수'라 한다.


#### 음의 정수를 표현하는 방식

1. 정수에는 연산의 개념이 존재한다.
2. 양의 정수의 이진수 표현에 2의 보수를 취한 결과를 음의 정수로 표현한다.
```
1) 정수 +5 == 00000101 
              11111010 (1의 보수를 취함)
              11111011 (+1을 함)
              == 정수 -5  
```
3. 연산 과정에서 올림수를 버린다.


#### 실수의 표현 방식

1. 1과 2사이에는 무한개의 실수가 존재한다. 따라서 컴퓨터의 표현에는 한계가 존재한다.
2. 정밀도를 낮추고 근사치의 값(표현할 수 있는 값)의 범위를 넓힌다. (수식에 기반한)
3. 실수에는 최대한 가까운 수가 만들어 진다고 하더라도 상시 오차가 존재한다. (연산에서는 더 극명히 나타난다.)


#### 상수(Constants)

1. C++은 상수에 대한 문법이 const.
2. JAVA는 상수에 대한 문법이 final.
3. 상수의 이름은 모두 대문자로 하고,
4. 이름이 둘 이상의 단어로 이뤄질 경우 단어 사이에 언더바를 넣는다.


#### 자동 형 변환 (Implicit Conversion) 

1. 자료형의 크기가 큰 방향으로 형 변환이 일어난다.
2. 자료형의 크기에 상관없이 정수 자료형보다 실수 자료형이 우선한다.


#### 부호 연산자

```
class UnaryAddMin {
    public static void main(String[] args) {
        short num = 5;
        System.out.println(+num); // + 부호 연산
        System.out.println(-num); // - 부호 연산

        short num2 = 7;
        short num3 = (short)(+num2); // 형 변환 하지 않으면 오류 발생
        short num4 = (short)(-num2); // 형 변환 하지 않으면 오류 발생
    }
}
```

#### 비트 연산자

1. 비트를 대상으로 진행
2. 피연산자는 반드시 정수이어야 함
3. 실수를 대상으로 하는 비트 연산은 의미가 없기에 자바는 이를 지원하지 않는다
4. &, |, ^(xor), ~(not)

```
class BitOperator {
    public static void main(String[] args) {
        byte n1 = 5; //00000101
        byte n2 = 3; //00000011
        byte n3 = -1 //11111111

        byte r1 = (byte)(n1 & n2); //00000001
        byte r2 = (byte)(n1 | n2); //00000111
        byte r3 = (byte)(n1 ^ n2); //00000110
        byte r4 = (byte)(~n3); //00000000

        System.out.println(r1);
        System.out.println(r2);
        System.out.println(r3);
        System.out.println(r4);
    }
}
```


#### 비트 쉬프트(shift) 연산자: <<, >>, >>>

1. 비트 쉬프트 연산자는 피연사자의 비트 열을 왼쪽 또는 오른쪽으로 이동시킨 결과를 반환하는 연산자
2. 이 연산자도 두 개의 피연사작 필요한 이항 연산자이며 피연산자는 모두 정수이어야 한다.
3. 빈 공간을 모두 0으로 채운다.

```
class  BitShiftOp {
    public static void main(String[] args) {
        byte num;

        num = 2; // 00000010
        System.out.println((byte)(num << 1) + " "); //00000100
        System.out.println((byte)(num << 2) + " "); //00001000
        System.out.println((byte)(num << 3) + " " + '\n'); //00010000

        num = -8; // 11111000
        System.out.println((byte)(num >> 1) + " "); //11111100
        System.out.println((byte)(num >> 2) + " "); //11111110
        System.out.println((byte)(num >> 3) + " "); //11111111
    }
}
```


#### 상속의 기본 문법 이해

1. 객체지향 기반에서 상속은 연관된 일련의 클래스들에 대해 공통적인 규약을 정의하는 것이다.
2. 생성자는 객체 즉 개체에서 실행하여 멤버를 초기화 하는 것을 원칙으로 한다.

```
class SuperCLS {
    public SuperCLS() {
        System.out.println("I'm a Super Class");
    }
}

class SubCLS extends SuperCLS {
    public subCLS() {
        System.out.println("I'm Sub Class");
    }
}

class SuperSubCon {
    public static void main(String[] args) {
        new SubCLS();  // 상속한 상위 클래스의 생성자가 먼저 호출 된 이후에, 자신의 생성자가 호출
    }
}
```

```
class SuperCLS {
    public SuperCLS() {
        System.out.println("Super Class");
    }
    public SuperCLS(int i) {
        System.out.println("Super Class " + i);
    }
    public SuperCLS(int i, int j) {
        System.out.println("Super Class " + i + ", " + j);
    }
}

class SubCLS extends SuperCLS {
    public subCLS() {
        System.out.println("I'm Sub Class");
    }
    public SubCLS(int i) {
        super(i); // super 키워드(생성자 위치에서 사용하면 생성자를 호출 this와 유사하다)
        System.out.println("Sub Class " + i);
    }
    public SuperCLS(int i, int j) {
        super(i, j);
        System.out.println("Super Class " + i + ", " + j);
    }
}

class SuperSubCon2 {
    public static void main(String[] args) {
        new SubCLS();
        System.out.println();

        new SubCLS(1);
        System.out.prinltn();

        new SubCLS(1, 2);
        System.out.println();
    }
}
```


#### 메소드 오버라이딩

1. 메소드 오버라이딩은 상위 클래스에 정의된 메소드를 하위 클래스에서 다시 정의 하는 것을 뜻한다.
2. 상위 클래스의 참조변수는 하위 클래스의 인스턴스를 참조 할 수 있다.

```
class MobilePhone {
    protected String number;

    public MobilePhone(String num) {
        number = num;
    }
    public void answer() {
        System.out.println("Hi~ from " + number);
    }
}

class SmartPhone extends MobilePhone { // smartPhone은 MobilePhone의 특징을 모두 함유
    private String androidVer;

    public SmartPhone(String num, String ver) {
        super(num); //반드시 해야하는 약속
        androidVer = ver;
    }

    public void playApp() {
        //super.answer() 이렇게 가능

        System.out.println("App is Running in " + androidVer);
    }
}

class MovileSmartPhoneRef {
    public static void main(String[] args) {
        SmartPhone ph1 = new SmartPhone("010-555-777", "Nougat");
        MobilePhone ph2 = new SmartPhone("010-999-333", "Nougat"); //MobilePhone 으로 SmartPhone 개체 참조

        ph1.answer();
        ph1.playApp();
        System.out.println();

        ph2.anser(); //현재 오버로딩 안되있기에 자기 자신의 멤버를 접근해 호출
        //ph2.playApp(); 불가능
    }
}
```

3. 자바는 메소드 호출 시 '참조변수의 형(Type)을 참조'하여 그 메소드의 호출이 옳은 것인지 판단한다.
4. 이러한 형태의 판단은 그 속도가 빠르다. 또 코드를 단순하게 한다.
5. 자바는 참조변수의 형(Type) 정보를 기준으로 대입의 가능성을 판단한다.
6. 아래와 같이 두 클래스의 참조 관계는 배열까지 이어진다.

```
Cake[] cakes = new CheeseCake[10];
```

7. 오버라이딩은 가린다 혹은 무효화 시킨다는 뜻으로 해석된다.

```
class Cake {
    public void yummy() {
        System.out.println("Yummy Cake");
    }
}

class CheeseCake extends Cake {
    public void yummy() {
        System.out.println("Yummy Cheese Cake");
    }
}

class YummyCakeOverriding {
    public static void main(String[] args) {
        Cake c1 = new CheeseCake();
        CheeseCake c2 = new CheeseCake();

        c1.yummy(); //c1 인스턴스 멤버 접근
        c2.yummy(); //c2 인스턴스 멤버 접근
    }
}
```

8. 메소드의 이름, 메소드의 반환형, 메소드의 매개변수 선언 까지 같아야 메소드 오버라이딩이 성립한다.

```
class Cake {
    public void yummy() {
        System.out.println("Yummy Cake");
    }
}

class CheeseCake extends Cake {
    public void yummy() {
        super.yummy();
        System.out.println("Yummy Cheese Cake");
    }
    public void tasty() {
        super.yummy();
        System.out.println("Yummy Cheese Cake);
    }
}

class YummyCakeOverriding {
    public static void main(String[] args) {
        CheeseCake c1 = new CheeseCake();

        c1.yummy(); 
        c1.tasty();
    }
}
```

9. 상위 클래스의 생성자를 호출하거나, 오버라이딩 된 메소드의 호출을 목적으로도 super 키워드가 사용된다.
10. 변수는 오버라이딩 되지 않는다. 따라서 참조변수 형에 근거한다.
11. 클래스 변수와 클래스 메소드는 오버라이딩 대상이 아니다.


#### instanceof 연산자의 기본

1. if (참조변수 instanceof 자료형) // 참조변수가 참조하는 인스턴스 해당 클래스를 참조하거나 하위 클래스이면 true 아니면 false 반환한다.

```
class Cake { }

class CheeseCake extends Cake {  }

class StrawberryCake extends CheeseCake {  }

class YummyCakeOf {
    public static void main(String[] args) {
        Cake cake = new StrawberryCheeseCake();

        if (cake instanceof Cake) {
            System.out.println("케익 인스턴스 or");
            System.out.println("케익 상속하는 인스턴스");
        }
        if (cake instanceof CheeseCake) {
            System.out.println("치즈케익 인스턴스 or");
            System.out.println("치즈케익 상속하는 인스턴스");
        }
        if (cake instanceof StrawberryCheeseCake) {
            System.out.println("딸기치즈케익 인스턴스 or");
            System.out.println("딸기치즈케익 상속하는 인스턴스");
        }
    }
}
```

```
class Box {
    public void simpleWrap() { //단순 포장
        System.out.println("Simple Wrapping");
    }
}

class PaperBox extends Box {
    public void paperWrap() {
        System.out.println("Paper Wrapping");
    }
}

class GoldPaperBox extends PaperBox {
    public void goldWrap() {
        System.out.println("Gold Wrapping");
    }
}

class Wrapping { 
    public static void main(String[] args) {
        Box box1 = new Box();
        PaperBox box2 = new PaperBox();
        GoldPaperBox box3 = new GoldPaperBox();

        wrapBox(box1); 
        wrapBox(box2);
        wrapBox(box3); // 유연한 메소드 호출
    }

    public static void wrapBox(Box box) { //받아서
        if (box instanceof GoldPaperBox) { //검증
            ((GoldPaperBox)box).goldWrap(); //포장
        }
        else if (box instanceof PaperBox) {
            ((PaperBox)box).paperWrap(); //포장
        }
        else  
            box.simpleWrap(); //포장
    }
}
```


16

