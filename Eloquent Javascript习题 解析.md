## 第二章
### 2.1 Looping a triangle

**标准答案**
```
for(var line = "#";line.length < 8;line+="#"){
    console.log(line);
}//字符串拼接 判断字符串长度来实现循环
```
经验：做这道题时没有弄清楚js中基本类型和引用类型的区别导致错误
```
错误代码：
    var line = "########";
    for(var i = 1;i <= 8;i++){
        console.log(line);
    }
//自以为能通过改变字符串的长度从而去改变字符串本体。实则没有弄清楚基本概念
```
放上理解的链接：
https://segmentfault.com/a/1190000008472264
https://segmentfault.com/a/1190000002789651

### 2.2 FizzBuzz
题干：输出1 - 100 之间的整数，能被3整除的输出Fizz
，能被5整除的输出Buzz，能同时被3和5整除的输出FizzBuzz

标准答案
```
for(var i = 1;i <= 100;i++){
   var z = "";
   if(i%3 == 0){
        z+="Fizz"
    }
    if(i%5 == 0){
        z+="Buzz"
    }
    console.log(z||i);
}//同时需要输出数字和字符串 运用的是或门的短路特性

/*
或门
a || b时 
当a为false时 无论b是什么类型直接输出b
当a为true时 直接输出a

与门
a && b时
当a为false b短路直接输出a
当a为true  直接输出b

即为：
条件1 && 条件2   条件1为假时不会执行条件2

条件1 || 条件2   条件1为真时不会执行条件2*/
```

### 2.3 Chess board
标准答案
```
var size = 8; 
var z = "";//没有空格
for(y = 0;y < size;y++){
    for(x = 0;x < size;x++){
        
        if((x+y)%2 == 0){
            z+="#";
        }
            z+=" ";//有空格
    }
   z+="\n"
}
console.log(z);
/*首先是找规律 然后分为x ，y来代替宽高 
```
## 第三章 函数
### *知识点*
1. 定义函数
    + 字面量定义
    + 函数声明
2. 作用域和参数
<hr/>

### 3.1 最小值
```
function min(a, b) {
  if (a < b)
    return a;
  else
    return b;
}
```
简单的if判断 没什么好说的

### 3.2 递归
```
function isEven(num){
    if(num == 0){return true;}
    else if(num == 1){return false;}
    else if(num < 0){return isEven(-num);}
    else {return isEven(num - 2);}
}
isEven(50);
```

### 3.3 字符计数
这是自己的答案
```
function countBs(Bstring){
    var n = 0;
    for(i=0;i<Bstring.length;i++){
        if(Bstring.charAt(i) == "B")
        n++
    }
    return n;
}
function countChar(Bstring,BChar){
    var x = 0;
    for(i=0;i<Bstring.length;i++){
        if(Bstring.charAt(i) == BChar)
        x++
    }
    return x;
}
```
标准答案如下
```
function countChar(string, ch) {
  var counted = 0;
  for (var i = 0; i < string.length; i++)
    if (string.charAt(i) == ch)
      counted += 1;
  return counted;
}

function countBs(string) {
  return countChar(string, "B");
}
```
相同作用的代码可以被整合成函数，这就是函数的意义所在。     

## 第四章 数据结构：对象和数组
### 知识点：
1. 数字Num、布尔值Boolean、字符串String构成了基本的数据结构


<hr>

#### 4.1 特定范围内数字求和
```
function range(start,end,step){
    if(step == null) step = 1;
    var Ran =[];
    if(step > 0)
    {
        for(i=start;i<=end;i+=step){
             Ran.push(i);//push()方法小括号
       }
    } else {
        for(i=start;i>=end;i+=step){
            Ran.push(i);
        }
    }
   return Ran; 
}
function sum(Ran){
    var plus = 0;
    for(i=0;i<Ran.length;i++){
        plus+=Ran[i];
    }
    return plus;
}
```
- 函数及其副作用
    将函数分为两类
    
1. 调用后产生副作用（例如`console.log`）
2. 调用后产生返回值

相比于直接产生副作用的函数，产生返回值的函数更容易被集成到新的编程环境中。

纯函数是一种只会产生值而不会影响他自己范围外任何事情的函数。

- 数组方法
  

添加删除 | 返回索引| 返回值 | 拼接字符串
---|---|---|---
pop（） | indexOf（） | slice（）不会修改数组| concat（）
push（） | lastIndexOf（） |  | join（）
shift（） |  |  |
unshift（） |  |  | 
splice()会修改原始数组 arrayObject.splice(index,howmany,item1,.....,itemX) | | | 

#### 4.2 逆转数组
```
11111111111111
```