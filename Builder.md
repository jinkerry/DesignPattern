Builder

将一个复杂对象的构建与它的表示分离 ,使得同样的构建过程可以创建不同的表示。 
<pre>
public interface Builder{
     void buildPartA();
     void buildPartB();
     void buildPartC();
     
     Product getResult();
}

public class Director{
     private Builder builder;
     public Director(Builder builder){
          this.builder = builder;
     }
     public void construct(){
          builder.buildPartA();
          builder.buildPartB();
          builder.buildPartC();
     }
}

public class ConcretBuilder implements Builder{
     Part partA, partB, partC;
     public void buildPartA(){
          //TODO
     }
     public void buildPartB(){
          //TODO
     } 
      public void buildPartC(){
          //TODO
     }
      public Product getResult(){
          //TODO
     }
}

public interface Product{}

public interface Part{}
</pre>

调用Builder
<pre>
ConcreteBuilder builder = new ConcreteBuilder();
Director director = new Director(builder);
director.construct();
Product product = builder.getResult();
</pre>
实际应用中，池pool会用到。
