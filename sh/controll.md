

## for loop  

There are lots of ways to run the code looply.  




#### 1. 기본 루프  

```
for i in 1 2 3 4
do
  echo "$i"
done
```


```
#! /bin/sh


echo "---------------------"
echo "| how many client ? |"
echo "---------------------"

echo -n "type >> "

read num

for i in `seq $num`
do
    echo "$i"
done
```
