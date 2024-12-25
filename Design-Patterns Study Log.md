# 【设计模式学习笔记】Design-Patterns
​
### 学习声明：

        本笔记仅供博主个人学习记录。

参考课程来自： 【【狂神说Java】通俗易懂的23种设计模式教学（停更）】

# 一、设计模式概述：

## 1. 设计模式：

        - 前辈对代码开发经验的总结，用于解决特定问题的一系列套路。

        -> 用于提高代码可复用性，可维护性，稳健性，安全性，灵活性。

## 2. 意义：

        是一种针对面向对象编程OOP的实质应用。（三大特性：封装、继承、多态）

        -> 面向对象编程：核心概念为（类和对象），通过对象封装数据和方法，以组织代码。       

        - 面向过程编程用不到设计模式：

                面向过程编程：核心概念为函数和过程，通过函数划分代码模块，按照步骤一步步实现功能；（应用场景例如算法实现，和小型程序等）

## 3. 基本要素：

        （1）模式名称

        （2）解决的问题：使用场景

        （3）解决方案

        （4）效果：优缺点，时间/空间复杂度

e.g. 单例模式 ——> 系统开销

## 4. GoF23 （Group Of Four，四人帮写的书）：共23种设计模式

设计模式分类：

        ### 1. 创建型模式：

                单例模式，工厂模式，抽象工厂模式，建造者模式，原型模式。

                —— 对对象的创建和使用进行分离。

        ### 2. 结构模式：

                适配器模式，桥接模式，装饰模式，组合模式。

                —— 描述如何将类或者对象组成一种更大的结构。

        ### 3. 行为型模式：

                模版方法模式，命令模式，迭代器模式，观察模式，中介模式，备忘录模式，解释器模式，状态模式，策略模式，责任链模式，访问者模式。

                —— 描述类或对象之间如何相互协作共同完成单个对象无法完成的任务。【分配职责】  

  
  ****
  
  
# 二、OOP七大原则：  
## 1. 开闭原则：【总纲：最重要】
对扩展开发，对修改关闭。  
**总结**：当应用需求发生改变，尽量不要修改原有代码，想办法通过扩展独立实现，不会影响原有代码功能块。
## 2. 里氏替换原则：
继承必须确保 **超类/父类** 所拥有的性质在子类中仍然成立。  
—— 子类可以扩展功能，但尽量通过添加新的方法实现新功能，尽量不要修改父类功能（重写-多态）。  
—— 多态运用过多，可能降低可复用性，导致程序容易出错。  
## 3. 依赖倒置原则：
要面向接口编程，不要面向实现编程。  
—— 高层不应该依赖底层；细节依赖抽象，抽象不依赖细节；  
（抽象：就是所谓的面向接口编程。  
    - 使用接口或抽象类制度规范/契约，而不涉及具体实现，具体实现细节由各个类完成。）  
**总结**：面向接口编程，降低耦合性。  
## 4. 单一职责/功能原则：
**强调【封装】**  
控制类的粒度，解耦对象，提高内聚性。  
一个对象不能承担太多职责，否则形成代码冗余 —> 粗力度/事情做的太多。  
—— 一个方法尽可能干好一件事情，也就是所说的原子性。  
## 5. 接口隔离原则：
**强调【封装】**
要为各个类建立它们需要的专用接口。  
用于约束接口。  
不要强迫类实现它们用不到的接口。
## 6. 迪米特法则：
只与直接朋友/关系交谈，不跟“陌生人”说话，不越级通信，可以通过第三方转发。
—— 降低耦合性，提高模块独立性，保持架构清晰性。
## 7. 合成复用原则
在面向对象编程（OOP）中，继承和组合是两种常用的类之间的关系。   
在设计模式时，应优先使用组合/聚合等关联方式来实现，其次才考虑继承实现。    
### 举例：e.g., 
1. 【**组合**：是 **has-a** 关系】A 的对象是 B 的成员变量；人类由头部组成，has - a 关系。
举例：
- class head: ...
- class person: Head h = new Head(); h...
3. 【**继承**：是 **is-a** 关系】狗不是由动物组成，狗 is a 动物;  
举例：
- class animal: color; Eat()...
- class dog extends animal: color, Eat()...
- 如果使用 **继承** 方式，需要遵守**原则2**尽量不重写父类方法。  
  
**** 


# 三、工厂模式：【Factory】
## 1. 作用：实现了创建者和调用者的分离。
## 2. 详细分类：
- **简单工厂模式** ：
  - 用来生产同一等级结构的**任意**产品。
  - 对于增加新的产品，需要球盖已有代码
- **工厂方法** ：
  - 生产同一等级结构的**固定**产品。
  - 支持增加任意产品
- **抽象工厂**：
  - 围绕一个超级工厂创建其他工厂。该超级工厂又称为其他工厂的工厂。
## 3. 遵循的OOP七大原则：
- **开闭原则** ：开发扩展，关闭修改
- **依赖倒转** ：针对接口编程，而不针对实现编程
- **迪米特法则** ：直接与朋友通信，避免越级；若不能直接交流则增加中间类。
## 4. 核心本质：
- 实例化对象不使用new，用工厂代替
- 将选择实现类，创建对象统一管理和控制。从而将调用者与实现类解耦。
## 5. 代码示例：
### 5.1 简单工厂模式：【静态工厂】
1. **接口实现**：Car **Interface**  
```Java
public interface Car {
  void name();
}
```

2. **实现类**：
- Wuling Car **Class**  
```Java
public class Wuling implement Car {
  public void name(){
    system.out.println("五菱宏光");
  }
}
```

​- Tesla **Class**:
```Java
public class Tesla implement Car{
  public void name(){
    system.out.println("特斯拉");
  }
}
```

3. **工厂类**：Factory **Class**  
```Java
// 简单工厂 —— 也叫【静态工厂】
// 增加一个新产品，不修改code做不到
// 但大多数情况仍然很多使用 简单工厂，因为开闭原则的满足可能需要很大的代价

// 不满足-开闭原则
public class CarFactory {
  // 方法1：但**简单工厂模式**这样有个缺点不符合OOP原则1：开闭原则，当新的对象出现时，仍然需要修改该方法的逻辑
  public static Car getCar(String car){ // 这里的第一个**Car**代表返回的是一个一个**Car()对象**
    if (car.equals("五菱"){
      return new Wuling();
    }else if (car.equal("特斯拉")){
      return new Tesla();
    }else{
      return null;
    }
  }

  // 方法2: 虽然不需要改变方法代码逻辑，但仍然需要修改工厂类；这是简单工厂模式的缺陷，所以他也叫静态工厂模式；(都是静态方法Static)
  public Car getWuling(){
    return new Wuling()
  }
  public Car getTesla(){
    return new Tesla()
  }
}
```
4. **测试类**：Consumer **Class**
```Java
public class Consumer {
  public static void main(String args[]){
    //// 1. NEW：这是原有的对象示例化方式：**new** 关键字; 这不仅要求我们了解接口，还要了解已知所有的实现类。
    // 此时：相当于是**自己造**出来的汽车，然而我们并不要求**消费者**进行生产，只需要从**工厂购买**即可。
    Car c1 = new Wuling();
    Car c2 = new Tesla();

    //// 2. 使用工厂创建：
    Car cf1 = CarFactory.getCar("五菱");
    Car cf2 = CarFactory.getCar("特斯拉");

    //// **工厂模式**实现了不去用**new**，而用工厂方法替代
    // 对象实现了方法：
    c1.name();
    c2.name();
    cf1.name();
  }
}
```  






### 5.2 工厂方法模式：
1. **接口实现**：
- Car **Interface**  
```Java
public interface Car {
  void name();
}
```
**为了完全满足开闭原则，此处将再实现一个车工厂的接口**
- CarFactory **Interface**  
```Java
public interface Car {
  Car getCar();
}
```

2. **实现类**：
- Wuling Car **Class**  
```Java
public class Wuling implement Car {
  public void name(){
    system.out.println("五菱宏光");
  }
}
```
​- Tesla **Class**:
```Java
public class Tesla implement Car{
  public void name(){
    system.out.println("特斯拉");
  }
}
```
**此时将为每个汽车再单独添加一个自己的工厂**，满足了开闭原则，但是代码量将大大上升。  
- WulingFactory **Class**:
```Java
public class WulingFactory implement CarFactory{
  @Override
  public Car getCar(){
    return new Wuling();
  }
}
```

- TeslaFactory **Class**:
```Java
public class TeslaFactory implement CarFactory{
  @Override
  public Car getCar(){
    return new Tesla();
  }
}
```

4. **测试类**：Consumer **Class**
```Java
public class Consumer {
  public static void main(String args[]){
    Car c1 = new TeslaFactory().getCar();

    cf1.name();
  }
}
```  


