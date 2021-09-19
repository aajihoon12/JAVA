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