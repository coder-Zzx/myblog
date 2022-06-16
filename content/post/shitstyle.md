---
title: "Shitstyle--readablecodesgotohell"
date: 2022-06-16T16:55:23+08:00
draft: false
categories: ["发疯了"]
tags: ["无意义瞎想"]
---

# ShitStyle--降低代码可读性,维护只属于你自己的代码

今天刚考完c++,这是我入校以来第四次笔试计算机相关专业课,也是第四次在卷子上手写代码.我实在是受不了这种落后老旧的方法,在考场上突发奇想,运用了一些奇技淫巧极尽可能的降低了代码可读性,向老师还以颜色.在此也对这些奇技淫巧加以总结,形成独特的代码风格--ShitStyle,大家以后遇到这种老旧落后的教考方式时也可以加以利用以表达自己的不满.

## ShitStyle参考手册

1. 善用#define预编译
   
   由于c++#define的易用性,我们可以利用#define将任意你想替换的字符串代替为任意字符串,比如
   
   ```cpp
   #define true false
   #define false true
   ```
   
   那么在以后的代码中,所有的true实际上为逻辑真,所有false实际上为逻辑假.依此来进行混淆,降低可读性.灵活运用这个技巧,就能写出一些让人**叹为观止**的代码,比如:
   
   ```cpp
   #define int 喵
   #define main 喵喵
   #define std 喵喵喵
   #define return 喵喵喵喵
   #define cout 喵喵喵喵喵
   
   #include<iostream>
   喵 喵喵
   {
       喵喵喵::喵喵喵喵喵<<"hello world";
       喵喵喵喵 0;    
   }
   ```
   
   > 聪明的你一定知道上述代码的含义吧
   
   #define还有很多关于宏的应用,由于本篇专注于ShitStyle,这里就不再赘述.

2. 利用typedef自定义类型名
   
   利用typedef能够对c++中的类型类名自定义,利用此方法也能对代码进行混淆降低可读性,比如
   
   ```cpp
   typedef int a;
   typedef float b;
   typedef char c;
   a aa=1;
   b bbb=1.9;
   c cccc='a';
   ```

3. 使用~~生僻深奥~~意义不明的命名风格
   
   最常见的当然就是仅使用abcd等一个字母作为变量名,但是对于ShitStyle来说还是太可读了.
   
   - 可以在变量名的任意位置加下划线_~~(这种方法在手写代码时尤其省事,多个下划线在手写时可以直接一笔写过)~~
   
   - 大小写混用,大驼峰小驼峰匈牙利写法混用
   
   - 拼音音序命名
   
   - 无意义但遵循一定规律的字符串
   
   比如:
   
   ```cpp
   int ___th_3_f1l_stVar=1;
   ```

4. 使用混乱的缩进甚至不缩进
   
   这条无需多言,哪怕只遵守这条也能让一份代码可读性骤降,属于至尊邪术,除非对老师深恶痛绝不然不建议使用.

5. 重载运算符使其文不对题
   
   比如首先封装自己的int类然后将+运算符重载成/运算符
   
   ```cpp
   class Myint{
       private:
           int i;
       public:
           Myint& operator+(Myint a){
               i=i/a;
               return *this;
           }
   };
   ```

除了以上,还有很多方式降低可读性,比如自己封装自己的工具类,类不断抽象嵌套等,一般在代码功能逻辑更加复杂时会用到,这里就不再赘述.

## 课后作业

这里给出一份代码,是对以上各方法的集合运用,相信大家可以依照上述方式还原出一份可读性更高的代码,这也是这次考试最后一道编程题的答案.

```cpp
#include<iostream>
#define aaa class
#define bbb private
#define ccc public
#define eee new
#define fff for
#define ggg return
using namespace std;typedef int ddd;typedef void hhh;
aaa Tea{bbb:Stu* array;ddd __th_III_if_aR_ray;ccc:Tea(ddd n){__th_III_if_aR_ray=n;array=eee 
Stu[n];fff (ddd i=0;i<n;i++){array[i]=NULL;}}~Tea(){delete [] array;    }hhh display();};
hhh Tea::display(){fff (ddd i=0,j=0;j<__th_III_if_aR_ray;i++){cout<<array[i].score;if 
(j!=__th_III_if_aR_ray-1){cout<<",";}}}
aaa Stu{bbb:ddd score;ccc:Stu(ddd n){score=n;}Stu(){ggg;}friend hhh Tea::display();};
```

***

## 附录

### 版权信息

本文原载于xiaozhatecpp.fun，转载请注明出处。
