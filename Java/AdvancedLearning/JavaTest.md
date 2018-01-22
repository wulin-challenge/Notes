# 有关Java的测试
## 单元测试
> 单元测试(unit testing)，是指对软件中的最小可测试单元进行检查和验证。
### 什么是TDD
> [百度百科词条](http://baike.baidu.com/item/TDD/9064369)  
> TDD是测试驱动开发（Test-Driven Development）的英文简称，是敏捷开发中的一项核心实践和技术，也是一种设计方法论。  
> TDD的原理是在开发功能代码之前，先编写单元测试用例代码，测试代码确定需要编写什么产品代码。TDD虽是敏捷方法的核心实践，但不只适用于XP（Extreme Programming），同样可以适用于其他开发方法和过程。

- 个人理解：引用Mockito框架中的 "when thenReturn" and "when thenThrow“ 由预定输入，运行方法或模块后，需要返回预定的数据或者抛出预定的异常，这就是已经写好了测试
- 然后根据测试原型，去思考真正的功能代码的实现，当代码实现后，能够通过之前写的测试就代表着一个方法或模块的开发成功，然后开发下一个
- 要想做到这样的地步，首先基础的环境要思考好，耦合的问题要明确，确定公共模块之后，再一个个的TDD进行开发。一个很好的思想，不用担心你之后的改动会让代码变得丑陋不堪

> 优点：在任意一个开发节点都可以拿出一个可以使用，含少量bug并具一定功能和能够发布的产品。  
> 缺点：增加代码量。测试代码是系统代码的两倍或更多，但是同时节省了调试程序及挑错时间。

    单元测试是用来对一个模块、一个函数或者一个类来进行正确性检验的测试工作。
    比如对函数abs()，我们可以编写出以下几个测试用例：
    输入正数，比如1、1.2、0.99，期待返回值与输入相同；
    输入负数，比如-1、-1.2、-0.99，期待返回值与输入相反；
    输入0，期待返回0；
    输入非数值类型，比如None、[]、{}，期待抛出TypeError。
    把上面的测试用例放到一个测试模块里，就是一个完整的单元测试。

****************
## 实现方案
### 使用JunitTest
- idea中装好插件，直接Alt Insert 然后选Test生成
- Before Test 执行顺序：
    - Before在Test之前执行是毋庸置疑的，但是如果有多个Before的话，按定义的先后逆序执行，也就是说AB顺序定义，BA顺序执行
    - `注意` Before的执行顺序不是平常想的那样，如果你有一个共享的对象，需要在两个Before中完成初始化，是办不到的，必然空指针
#### Assert
> 断言是程序员假定程序在某种情况下的状态情况，如果不是预期断言的情况就会抛出异常

- Assert.assertEquals(a,b) 断言两个对象是相等的
- assert(expression) 断言表达式为真

**************
### Mock框架
> 2017-06-21 14:36:54 对mock的使用很迷，还是需要稳定心态慢慢看文档才能理解
> [JMockit官方文档](http://www.vogella.com/tutorials/Mockito/article.html#testing-with-mock-objects)
- [入门博客](http://blog.csdn.net/chjttony/article/details/17838693)


## 感悟

 