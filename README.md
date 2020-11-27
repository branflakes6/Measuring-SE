# Measuring-Software Engineering
A report written for my Software Engineering Class

### Introduction
The idea of measuring software engineering has existed pretty much since Software Engineering began It is an idea that has evolved into an entire field with hundreds of methods and dozens of companies working on the problem.<sup>[1]</sup> Modern software companies place a lot of importance on being able to measure the quality of work being done by their employees, companies are paying a lot of money for their engineers and want to make sure they are getting the best out of them. Many companies exist to create new ways of measuring software engineering that they can sell to larger companies. The techniques and technologies produced by these companies have a lot of potential in making the process easier and could lead to better engineering standards and practices. However, there are many ethical questions and concerns that need to be answered.  

In this report I will look at many ways to measure engineering, some of the original methods and ways of quantifying software as well as some new ideas. Some tools used to measure the engineers themselves who are working on the code base, how productive they are, what do they contribute to the company. Then lastly, I will discuss the ethics of all of this and give my opinions on whether I think these ideas should be embraced by the industry.


### Algorithmic Approaches

Lines of Code (LOC)

One of the most basic approaches to measuring Software Engineering is source lines of code. There are two different ways of doing this, the first is physical source lines of code which is simply counting the number of lines of code in the code base. [1]  The second is logical lines of code which attempts to count the number of executable statements. [1]

This method of measuring software has been around since the 1960’s[1] and while it has remained a popular metric to assist in measuring software engineering it quickly became apparent that SLOC on its own is an ineffective and misleading measurement. When measuring software by its lines of code you do not account for several important factors, such as the differences and diversity in programming languages and how each one does a task and the simple truth that a long program is not necessarily a complex program. 

Examples: Code can be written in many ways

A simple example is two ways of summing two numbers in Java	
``` 
Public int add (int a, int b) {Return a + b;}
```

Vs

```
Public int add (int a, int b) 
{
	int sum;
	sum = a + b;
 	Return sum;
}
```

If we are to count physical lines of code the first implementation of this function is done in one line that simply just returns a + b, the second implementation returns the exact same answer but does so in six lines and uses an extra variable to add a and b. Both functions do the exact same thing, but the second version has many more lines of code while also being less efficient. If we use logical lines of code and define a logical SLOC as an executable line with a semicolon (ignoring function definitions and curly brackets) we get one logical SLOC for the first function and three for the second. While this is a better measurement as the two functions are now closer in magnitude there is still the obvious flaw that the less efficient function still appears to be the better one by our measurement. Additionally, our measurement of logical lines of code is based on simply counting the number of semicolons, which is a problematic approach as it only works for some languages. There are many languages such as python which do not use semicolons and thus creating a definition that works for all languages is extremely difficult.

This highlights a key issue with counting lines of code, it is very difficult to tell the difference between complex code and long code. A system of measurement that uses only source lines of code can be detrimental to the code base as it can encourage programmers to write worse code. If you are basing your metrics of which developers are working hardest or doing the best work on SLOC then you are creating an environment that encourages your engineers to find the longest possible way to write their code. This can lead to deliberately inefficient methods that require a large amount of code. 

Another example is the difference between a simple Object Orientated Java class and a complex but compact algorithm. When writing Object Orientated programs you can end up with a long piece of software with a lot of basic getter and setter methods that simply just changes one or two values of the object. Writing such a class could take only an hour or two but have hundreds of lines of code, conversely a complicated algorithm that could be crucial to the software system may only be 20-30 lines long but could take several days to develop as it requires the engineer to spend a lot of time figuring out the logic of what they are trying to create rather than just mindlessly writing code.


*"Measuring programming progress by lines of code is like measuring aircraft building progress by weight" - Bill Gates*


Source lines of code as a metric is only useful when combined with other measurements, if you impose strict coding practices on your engineers and ensure that everyone is writing the highest quality and most line efficient code they can then it can provide some insight into the complexity of your code base. For example, Windows NT 3.1 has about 5 million source lines of code while windows XP had about 45 million [3], this provides some meaningful information on the scale of these projects and the number of engineers required to create and maintain them.


ABC Method

The ABC software metric was developed as an answer to issues with SLOC, it attempts to solve the problem with a more algorithmic approach that is much less simplistic.[4]

ABC values are calculated by counting the number of assignments(A), branches (B) and conditionals (C) and then creating a triplet of these values.[4]

The following equation is used to calucalte ABC values


```
<ABCvector> = \sqrt{(a2 + b2 + c2)}
```

ABC evaluation has different rules depending on the programming language used, this is aimed at creating consistent scores across a range of languages. The goal of ABC is to measure the size of the software in a meaningful by evaluating all parts of the system rather than just lines of code. ABC accounts for things such as conditional operators, assignment operators and important keywords. This means it can tell the difference between the complexity of single lines of code. [4]

An example of using ABC to measure software:

```
System.out.println(x);
```

Vs

```
If ( x >= 0 && y != 1) { System.out.println(x + y);} 
```
In a basic SLOC system these would both have a value of one as there is one line of code and one semi colon. In ABC however the first snippet has a single class method call that prints x so its value for A = 0, B = 1 and C = 0.  

The second snippet has a condition, two conditional operators, a class method call and an assignment so its values will be A = 1, B = 1, C = 3. 

This demonstrates the clear difference in complexity between these lines and allows for a much greater evaluation of the code base. 

While ABC is a better metric for measuring software than simple SLOC it still has many of the same drawbacks. Like SLOC if not used correctly it can encourage bad programming as it still rewards you for writing longer less efficient code, however the rewards are not as great with ABC so there is less incentive. Like SLOC, ABC is most valuable when used in combination with other methods and systems. If engineers are following good programming practice and their code is being monitored to ensure they are not trying to game the system, it can be a useful metric for determining its complexity.






