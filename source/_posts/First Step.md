---
layout: post
title: First Step
date: 2017-11-05
categories: blog
tags: [C语言,总结]
description: Hello,World是每个程序员向世界的第一声呐喊
---
我在准备考试的同一时间也在跟着<明解C语言>学习c语言的应用.有很多的课后练习,在学到第四章循环控制的时候,课后练习要求为
>编写一段程序,为九九乘法表增加横纵标题

然后我开始尝试在没有参考别人的解法的情况下,思考如何实现这一目标.
基于自己数学的学习,我首先想到了在for循环语句下,根据对`i`和`j`取值的限定,用类似分段函数的办法用if语句实现左上角的空白以及分别在第二行和第二列实现"--"和"|"以将标题和九九乘法表区分开来.
```
int main(void)
{
	int i=1;   
	int t = 1;

	for (i = 1; i <= 11; i++) {
		for (t = 1; t <= 11; t++) {
			if (i == 1 && t == 1)
				printf("   |");
			if (i > 2 && t == 2)
				printf("|");
			if (i == 2 && t >= 3)
				printf("----");

			if (i >= 3&&t==1)
				printf("%3d", i - 2);
			if (i == 1 && t >= 3)
				printf("%3d", t - 2);
			if (i >= 3 && t >= 3)
				printf("%3d", (t - 2)*(i - 2));
		}
		printf("\n");

	}
	putchar('\n');
```

最终实现的效果如下图

![算法1][1]

在完成之后,我去网上搜索这一题,去看看别人的解法
之后找到一个解法看起来比我的好很多
```
int a, b;
	printf("  |");
	for (a = 1; a <= 9; a++) 
		printf("%3d", a);
	putchar('\n');/*first line*/
	for (a = 1; a <= 10; a++)
		printf("---");
	putchar('\n');/*sec line*/
	for (b = 1; b <= 9; b++) {
		printf("%d", b);
		printf(" |");
		for (a = 1; a <= 9; a++) {
			printf("%3d", b*a);
		}
	putchar('\n');
	}/*the form*/
	return 0;
```

![算法2][2]

这两种算法比较之下,发现我在构建循环的时候,思维还是偏数学而非编程.
从第二种算法的注释中可以看出,它将这一编程目的分为三部分.

 1. 首先构建第一行,将1-1位置的空格以及横向标题呈现出来.
 2. 然后是第二行,以for循环将"---"呈现出来并且在构建过程中体现出了格式控制的思想.为了保证两位数和前面的数字间仍有空隙,在构建九九乘法表时将输出`printf"%3d"`来保证每个数字占三位.因此整个表格加上纵向标题以及"|"应为30位.这一点也是在我自行构建的过程中没有想到的,在完成代码后根据运行的结果进行了多次调整仍然有些偏差.
 3. 最后才是九九乘法表的输出.
 
在这一次的练习中,最后的结果以及代码的逻辑再次让我意识到了编程之美,也是我想构建个人Blog来记录自己学习生活的原因之一.这样的过程值得自己留些纪念.


  [1]: https://github.com/AsherQAQ/AsherQAQ.github.io/blob/master/img/post1-1.png
  [2]: https://github.com/AsherQAQ/AsherQAQ.github.io/blob/master/img/post1-2.png