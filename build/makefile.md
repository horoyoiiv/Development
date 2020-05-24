

# makefile   

# 1. Header File  

## 1. 헤더 파일이란?  
```c++
// math.h
#ifndef MATH_H  <- 헤더 가드
#define MATH_H

int add(int x, int y);

#endif
```
* **헤더 파일** : `함수`나 `클래스`의 `선언`이 저장된 파일.  
* **유지보수 및 개발**의 편리함을 위하여, **모듈화**를 위해 사용된다.  
* 헤더 파일은 **전처리기**에 의해 사용되는 소스코드에 **복사붙여넣기**된다.  

## 2. -E 옵션을 통한 전처리  
* 전처리 단계에서는 **주석 제거**와 **#**으로 시작하는 구문을 처리한다.  
* 헤더 파일은 전처리 단계에서 **타겟 소스코드**로 단지 **복사 붙여넣기**되어, `전방 선언`이 된다.  

```
g++ -E -o main.i main.cpp
```
* 전처리 후의 소스코드(main.i)  
* 헤더 파일에 정의된 함수가 소스코드로 삽입된다.  
```c++
// main.i
# 1 "main.cpp"
# 1 "<built-in>"
# 1 "<command-line>"
# 1 "/usr/include/stdc-predef.h" 1 3 4
# 1 "<command-line>" 2
# 1 "main.cpp"

# 1 "math.h" 1

int add(int x, int y);      <-- 전방선언된 모습
# 3 "main.cpp" 2

int main(void){
    return 0;
}
```

## 3.-c 옵션을 통한 오브젝트 파일 생성  

```c++
g++ -c -o main.o main.cpp
g++ -c -o math.o math.cpp
```
* 생성된 두 개의 오브젝트 파일을 **링킹**하여 **실행가능한 오브젝트 파일로 생성**한다.  

```
g++ -o main main.o math.o
```

# Makefile  

## 1. 기본 구조  
* 타겟 : 만들고자 하는 파일  
* 디펜던시 : 타겟을 만들 때 필요한 파일  
* 커캔드 : 실제 생성을 위한 커맨드  
```
TARGET : DEPENDENCY
  COMMAND
```
* Makefile내에서의 위와 같은 구조가 반복된다.  

## 1. 변수  
* 다음과 같은 문법을 통하여 **변수**로서 사용  
* 사용할 때는 $(변수명) 으로 사용  
```
CC = g++
TARGET = main
```


## 2. 작성  

```
CC = g++        // 변수
TARGET = main   // 변수

all : $(TARGET)

main.o : main.cpp       // main.o 를 생성
	$(CC) -c main.cpp

math.o : math.cpp       // math.o 를 생성
	$(CC) -c math.cpp

$(TARGET) : main.o math.o     // main 을 생성
	$(CC) -o $(TARGET) main.o math.o
```

## 3. 컴파일 옵션 변수  

```
CC = g++
TARGET = main
CFLAGS = -Wall      // 컴파일 시 부여할 옵션을 변수로 선언 | 모든 warning을 출력

all : $(TARGET)

main.o : main.cpp
	$(CC) $(CFLAGS) -c main.cpp   // 해당 옵션을 부여

math.o : math.cpp
	$(CC) $(CFLAGS) -c math.cpp   // 해당 옵션을 부여

$(TARGET) : main.o math.o
	$(CC) -o $(TARGET) main.o math.o
```
