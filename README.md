# Java Basic Learning

## 1. Why should you have minimum scope for variables?

* 代码可读性更高，不会造成变量太多、别人看不懂那些变量都是干什么用的情况出现。对于类中的局部变量而言，最好是在使用的时候再去声明，比如一个方法里会用到一个变量，那就应该在这个方法内部去定义一个变量

## 2. Why should you understand performance of String Concatenation?

* Java 中的 String 是不可变对象，在对字符串进行修改时，其实是生成了新的 String 对象，当动态拼接很多时，过多的 String 对象势必会对性能造成影响，因此这种情况应尽可能使用 StringBuilder 或者 StringBuffer

## 3. What are the best practices with Exception Handling?

* 只在异常的情况下才对异常进行处理，正常的执行逻辑中不要去加没必要的异常捕获语句

## 4. When is it recommended to prefer Unchecked Exceptions?

* 当我们不清楚程序会出现什么样的错误时
* 当出现这种异常后程序无法恢复正常时

## 5. When do you use a Marker Interface?

* 使用标记接口时，我们的意图是为实现类做上一个标记，以便在要使用标记接口的某些特性时，可以判断这些实现类是否属于我们的标记接口，再进行下一步操作，因此当我们需要对某个特性进行抽象时，可以使用标记接口

## 6. Why are ENUMS important for Readable Code?

* 枚举类本身就是可读性非常高的，从枚举的命名就可以看出常量的含义
* 当类被定义为枚举类时，使用者马上就知道这个类中的成员都是固定的常量
* 使用枚举时的代码非常简洁，更加易读

## 7. Why should you minimize mutability?

* 可变性小可以确保对象在创建后不会出现太复杂的状态变化，更易于维护
* 当一个类是不可变时，这个类的实例对象是线程安全的

## 8. What is functional programming?

* 函数式编程不同于传统的指令式编程，它将繁琐复杂的指令集统一封装在函数中，外部调用时不必关注函数内部的状态变化，同时这种编程范式也更符合人类解决问题的思维。这种编程范式在 Java 8 中尤其突出，如典型的 Stream api

* 下面的示例代码就很好的说明了函数式编程的特点，首先对集合中的元素进行去重，再筛选出大于 5 的元素，最后统计一共有多少个，这种方式与我们正常处理问题的逻辑思路是一致的:  
  
    ````java
    List<Integer> list = new ArrayList<>(Arrays.asList(1, 6, 6, 3, 8, 10, 10));
    integerList.stream().distinct().filter(item -> item > 5).count();
    ````

## 9. Why should you prefer Builder Pattern to build complex objects?

* 可读性更高，阅读代码时可以很容易看出构造对象时设置了哪些属性
* 更节省代码，当构造一个复杂的对象时，不使用 builder 则需要写很多行代码
* 下面的代码展示了使用 builder 模式和不使用之间的区别：  
  
    ````java
    // use builder pattern
    Message.builder().subject("Hello!").content("Hello, dear Cherrow").build();
    ````

    ````java
    // dont use builder pattern
    Message message = new Message();
    message.setSubject("Hello!");
    message.setContent("Hello, dear Cherrow");
    ````

## 10. Why should you avoid floats for Calculations?

* 浮点型（即 float）数值进行计算时会造成精度的损失

## 11. Why should you build the riskiest high priority features first?

* 在项目初期阶段对风险性较高的功能先 spike 一下，可以有效降低项目的风险，如果在项目进行到后期才发现功能开发难度太大导致项目阻塞，则会成为较大的问题
