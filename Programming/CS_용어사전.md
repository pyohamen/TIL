### Compiler vs Interprter

```python
소스코드를 목적코드(다른 프로그램이나 하드웨어가 처리하기 용이한 형태)로 변환시키는 과정
소스 프로그램을 읽어서 즉시 결과를 출력
*현대에 들어서 JIT(Just-in-time)컴파일, 동적번역(dynamic translation) 으로 두 방식의 간격이 사라지는 추 세
```

### Process (=task)

```python
연속적으로 실행되고 있는 컴퓨터 프로그램
```

- 프로그램 vs 프로세스

  ```python
  프로그램은 하드에 저장되는 실행코드 / 프로세스는 프로그램이 메모리 상에서 실행되는 작업 단위
  ```

- Thread

  ```python
  어떠한 프로그램 내에서, 특히 프로세스 내에서 실행되는 흐름의 단위
  ```

  - 프로세스 vs 스레드

    ```
    멀티프로세스는 별개의 메모리를 차지하지만, 멀티스레드는 프로세스 내의 메모리를 공유한다.
    또한, 그렇기 때문에 같은 스레드의 수행순서를 알 수 없다.
    
    >공유 데이터(임계구역)에 접근하는 스레드개수를 제한하는 방법이 있음 
    
    Program > Process > thread
    ```

  - Browser

    ```python
    JS 의 환경 한 Tab,document는 싱글스레드
    ```

### Parsing / Parser

```
어떤 data를 원하는 form으로 만들어 내는 것 /.
일련의 문자열을 의미있는 token(어휘 분석 단위)로 분석하고
그것들로 이루어진 Parse tree를 만드는 과정 -> 이를 통해 자료구조 가 된다.
인터프리터나 컴파일러의 구성 요소 가운데 하나이다.
```

### Mount

```
마운트(mount)는 컴퓨터 과학에서
저장 장치에 접근할 수 있는 경로를 디렉터리 구조에 편입시키는 작업을 말한다.
좁은 의미로는 유닉스 계열의 운영 체제에서의 mount 명령어 또는 그 명령어를 사용하는 것을 말한다.
```

### Firmware

```python
특정 하드웨어 안에 있는 소프트웨어
```

### Middleware

```
운영 체제와 응용 소프트웨어의 중간에서 조정과 중개의 역할을 수행하는 소프트웨어

응용 소프트웨어 ( applicatino software ) 는 os 위에 있는
모든 소프트웨어로 개발자가 다른 기종간 구축할 때 별 다른 ( db / query )
것을 구축할 필요가 없어야 한다.
```

### Shell (Kernel)

리눅스의 셸은 명령어와 프로그램을 실행할 때 사용하는 인터페이스로 커널과 사용자간의 다리 역할

- 인터페이스

  서로 다른 두 개의 시스템, 장치 사이에서 정보나 신호를 주고받는 접점,경계면

- 커널

  (시스템의 모든 것을 완전히 통제하는 핵심)

  https://ko.wikipedia.org/wiki/커널_(%EC%BB%B4%ED%93%A8%ED%8C%85

### cmd vs powershell

```
cmd와 다르게 powershell은 객체지향언어
```



## Case naming convention

1. lowerCamelCase
2. UpperCamelCase
3. snake_case
4. Hungarian notation

이름 앞에 변수 타입을 넣어줌 ex) ch, db, str, b