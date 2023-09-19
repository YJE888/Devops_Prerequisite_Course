# Compiler와 Interpreter
### Compiler
- 컴파일러는 소스코드(개발자가 작성한 코드)를 기계어(01100000 10001100..) 또는 중간 언어로 변환하는 프로그램
- C, C++, Java, Rust 등이 있음
  |**순서**|1. 개발 코드| 2. 컴파일 | 3. 실행|
  |:---:|:---|:---|:---|
  |**실행 결과**|$ vi MyClass.java |$ javac MyClass.java </br> MyClass.class|$ java MyClass </br> Hello World|

### Interpreter
- 인터프리터는 소스 코드를 한 줄씩 읽고 해석하여 실행하는 프로그램으로 실행 시 소스코드를 해석함
- 실행 시간에 코드 수정이 가능하고, 유연한 프로그래밍 환경을 제공
- Python, Ruby, JavaScript, PHP 등이 있음
  |**순서**|1. 개발 코드 | 2. 실행|
  |:---:|:---|:---|
  |**실행 결과**|$ vi main.py |$ python main.py </br> Hello World|
