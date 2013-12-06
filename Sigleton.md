创建模式之Singleton单例
========================

一个class只有一个实例存在。在很多操作，比如建立目录，数据库连接都需要这样的单线程操作，类装载器（class lodaer）也采用单态模式。

<pre>
public class Singleton(){

     private Singleton(){}

     private static Singleton instance = new Singleton();

     public static Singleton getInstance(){
          
          return instance;
     }
}
</pre>

第二种形式， lazy initialization：

<pre>
public class Singleton(){

     private static Singleton instance = null;

     public static synchronized Singleton getInstance(){
          if (instance == null)
               instance = new Singleton();
          return instance;
     }
}
</pre>

注意：如果应用基于容器，那么Singleton模式少用或者不用。
