# [Java]자바의 정석 벼락치기


### 자바의 정석 벼락치기

정보처리기사 실기 2일인지 3일인지 잘 기억은 안 나는데<br>
이번에 이틀의 전사? 3일의 전사 기념으로<br>
자바의 정석도 벼락치기 해도 될 것 같다!<br>

#### ch2 변수

1. 명명규칙

   - 대소문자 구분. 길이에 제한 X
   - 예약어 사용해선 X
     예약어란? 자바에서 자체적으로 사용하는 단어 - true는 예약어. 하지만 True는 가능
   - 숫자로 시작해선 X
   - 특수문자는 '\_'와 '%' 허용
   - 클래스 첫글자 대문자
   - 여러 단어 첫글자는 대문자 ex) lastIndexOf
   - 상수 이름은 대문자. 단어는 '\_'로 구분

2. 변수, 상수, 리터럴

   - 변수: 하나의 값을 저장하기 위한 공간
   - 상수: 한 번만 값을 저장할 수 있는 공간
   - 리터럴: 그 자체로 값을 의미하는 것

3. 변수의 기본값과 초기화

   bolean의 기본값 = false<br>
   char -> '\u0000'<br>
   byte, short, int -> 0<br>
   long -> 0L<br>
   float -> 0.0f<br>
   double -> 0.0d or 0.0<br>
   참조현변수 -> null<br>

4. 정수의 오버플로우

   byte를 예로 들면,<br>
   최대값 127, 최소값 -128이다. 그래서 -128에서 1이 감소하면 최대값127이다.<br>

5. 형변환

   값의 타입을 다른 타입으로 변환하는 것<br>
   boolean을 제외한 7개의 기본형은 서로 형변환이 가능<br>

#### ch3 연산자

1. 연산자?

   - 연산자: 어떠한 기능을 수행하는 기호
   - 피연산자: 연산자의 작업 대상(변수,상수,리터럴,수식)

2. 연산자의 우선순위

<img src="https://user-images.githubusercontent.com/46602874/130643181-08450463-7b0d-469c-805d-1e1650fb4da1.png">

3. 쉬프트 연산자

   - x << n 은 x \* 2^n
   - x >> n 은 x / 2^n
   - 8 << 2 는 8 \* 2^2
   - 8 >> 2 는 8 / 2^2

### ch4 조건문과 반복문

    1. 조건문 - if, switch

    <img src="https://user-images.githubusercontent.com/46602874/130646982-26091697-95eb-4d4e-9cda-7a7de60711f5.png">

