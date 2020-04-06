


## 1. 준비  

#### 1. 파일의 확장자는 .sh  

```
command_list.sh  
```

#### 2. 실행 시 bash 스크립트파일.sh  

```
bash run.sh
sh run.sh
zsh run.sh
```


#### 3. 작성 시 맨 위는 샤뱅  
```
#! /bin/bash

```

#### 4. shell script로 프로그램 실행 시  
 아래와 같이 app을 세 개 실행 시키면 3개의 출력은 sh가 실행된 하나의 terminal을 공유하여 출력  
 
```
#! /bin/bash

java app
java app
java app
```


## 작성  


#### 1. 화면 출력은 echo  

```
#! /bin/bash

echo "Hello World"
```

output  
```
Hello World
```



#### 2. 변수는 "변수명=변수값"  

* 이때 공백이 있으면 안됨  
* 변수 사용 시에는 $변수명  

```
#! /bin/bash

name="horoyoii"
age=123

echo "Hello? your name is $name and age is $age"
```

```shell
Hello? your name is horoyoii and age is 123
```

#### 3. 입력 받기  
 * **read 변수명** 사용  
 * 변수명에 바로 대입  
 
```
#! /bin/bash

echo "what is your name?"
read input

echo "Hello, $input"
```

```
what is your name?
horoyoii
Hello, horoyoii
```

#### 3.1. 개행없이 입력받기  
 * **-n** 은 echo 후에 개행을 하지 않는다는 의미  
 
 
```
#! /bin/bash

echo -n "what is your name? : "
read input

echo "Hello, $input"
```

 아래와 같이 echo 출력문 바로 뒤에 입력가능  
```
what is your name? : horoyoii
Hello, horoyoii
```



## 연산  

* 1. expr 을 사용한다.  
* 2. 이 때 쿼터네이션(')이 아닌 역쿼터네이션(`)으로 묶는다.  
* 3. 모든 연산자 사이에는 공백  
* 4. 곱셈 시 \* 라는 기호 사용  


```
#! /bin/sh

echo "-------------------"
echo "| type two var    |"
echo "-------------------"

read a
read b

echo "your inputs are $a and $b!"

res1=`expr $a + $b`
echo "$a + $b = $res1"

res2=`expr $a - $b`
echo "$a - $b = $res2"

res3=`expr $a \* $b`
echo "$a * $b = $res3"

res4=`expr $a / $b`
echo "$a / $b = $res4"
```




## 참고  

[here](https://kangsecu.tistory.com/54)  







