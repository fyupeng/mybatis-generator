## MyBatis逆向工程

### 实现方式

- 接口方式

接口方式需要将自己实现的`Mapper`接口去实现它
```java
import tk.mybatis.mapper.common.Mapper;
import tk.mybatis.mapper.common.MySqlMapper;

public interface MyMapper<T> extends Mapper<T>, MySqlMapper<T> {
    //TODO
    //FIXME 特别注意，该接口不能被扫描到，否则会出错
}
```
接口方式持久封装层实现的源码封装在了`Jar`包中，而且所有的方法实现都实现了`Mapper<T>, MySqlMapper<T>`这两个接口，所以我们才需要实现它继而可以使用。

具体实现方法的调用可以这样使用

例如：
```java
Example classficationExample = new Example(Classfication.class);
Criteria criteria = classficationExample.createCriteria();

List<Classfication> result = classficationMapper.selectAll();
```

- 配置方式

配置方式的使用与接口一致，只是不需要实现接口，因为本身`Mapper`就存在了许多方法的配置信息了。


