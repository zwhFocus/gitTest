---
title: 设计模式
excerpt: 比如Windows桌面上的回收站，当我们打开了回收站，回收站界面展示在我们面前时，我们再次点击回收站，会发现系统并没有再次打开一个回收站界面，那么这个系统的回收站就是典型的单例模式的运用。
---

## 单例模式
比如Windows桌面上的回收站，当我们打开了回收站，回收站界面展示在我们面前时，我们再次点击回收站，会发现系统并没有再次打开一个回收站界面，那么这个系统的回收站就是典型的单例模式的运用。

- 饿汉模式：单例实例在类加载的时候创建，是线程安全的,但可能造成不必要的资源浪费。
```java
    /**
    * @author zwh
    * @version 1.0.0
    * @description 
        饿汉模式，单例实例在类装载的时候进行创建，是线程安全的.
        (该类构造方法为私有，只能通过该类静态方法创建该类的实例)
    */
    public class SingletonExample {

        private SingletonExample(){}

        private static SingletonExample instance = new SingletonExample();

        public static SingletonExample getInstance(){
            return instance;
        }
    }
```

- 枚举方式：线程最安全的，可避免序列化以及反射
```java
/**
 * @author zwh
 * @version 1.0.0
 * @description 枚举方式进行实例化，是线程安全的，此种方式也是线程最安全的
 */
public class SingletonExample {

    private SingletonExample(){}

    public static SingletonExample getInstance(){
        return Singleton.INSTANCE.getInstance();
    }

    // Singleton是继承自Enum的特殊类
    private enum Singleton{
        // INSTANCE是Singleton的实例
        INSTANCE;
        private SingletonExample singleton;

        //JVM保证这个方法绝对只调用一次
        Singleton(){
            singleton = new SingletonExample();
        }
        public SingletonExample getInstance(){
            return singleton;
        }
    }
}
```