Factoy工厂模式
================

工厂方法
<pre>
public class Facotory{

     public static Sample creator(int which){
          if (which ==1)
               return new SampleA();
          else if (which ==2)
               return new SampleB();

     }

}
</pre>

实例化时使用：
Sample simpleA = Factory.creator(1);

这样实例化就不涉及Sample的具体子类，达到了封装的效果。
使用工厂方法，要注意几个角色，首先你要定义产品接口，如上面的Sample，产品接口下面有Sample接口的实现类，如SampleA，其次还有一个factory类，用来生成Sample。

工厂模式中有：工厂方法（Factory Method）抽象工厂（Abstract Factory）
两个模式的区别在于需要创建对象的复杂程度上。

<pre>
public abstract class ForumFactory{
     private static Object initLock = new Object();
     private static String className = "com.jivesoftware.forumdatabase.DbForumFactory";
     private static ForumFactory factory = null;

     public static ForumFactory getInstance(Authorization authorization){
          if (authorization == null){
               return null;
          }
          if (factory == null){
               synchronized(initLock){
                    if (factory == null){
                         ... ...
                         try{
                              Class c = Class.forName(className);
                              factory = (ForumFactory)c.newInstance();
                         }
                         catch(Exception e){
                              return null;
                         }
                    }
               }
          }
          
          return new ForumFactoryProxy(authorization, factory, factory.getPermission(authorization))
          
     }
     
     //真正创建forum的方法由继承forumFactory的子类完成。
     public abstract Forum createForum（String name, String description) throws UnauthorizedException, ForumAlreadyExistsException;
     ... ...

}

</pre>

由此可见，工厂方法确实为系统结构提供了非常灵活强大的动态扩展机制，只要我们更换一下具体的工厂方法，
系统其它地方无需一点变换，就有可能将系统功能进行改头换面的变化。

