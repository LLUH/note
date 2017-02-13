```
＜?xml version="1.0"?＞ 
```
＜!--  
所有的XML映射文件都需要定义如下所示的DOCTYPE。  
Hibernate会先在它的类路径（classptah）中搜索DTD文件。  
--＞  
```
＜!DOCTYPE hibernate-mapping PUBLIC "-//Hibernate/Hibernate Mapping DTD 3.0//EN" 
"http：//hibernate.sourceforge.net/hibernate-mapping-3.0.dtd"＞
```
＜!-- hibernate-mapping有几个可选的属性： 
schema属性指明了这个映射的表所在的schema名称。 
default-cascade属性指定了默认的级联风格 
可取值有 none、save、update。 
auto-import属性默认让我们在查询语言中可以使用非全限定名的类名 
可取值有 true、false。 package属性指定一个包前缀。 --＞ 
```
＜hibernate-mapping schema="schemaName" default-cascade="none" auto-import="true" package="test"＞ 
```
＜!--用class元素来定义一个持久化类 --＞ 
```
＜class name="People" table="person"＞ 
```
＜!-- id元素定义了属性到数据库表主键字段的映射。--＞ 
```
＜id name="id"＞ 

＜!-- 用来为该持久化类的实例生成唯一的标识 --＞ 

＜generator class="native"/＞ 
＜/id＞ 
```
＜!-- discriminator识别器 是一种定义继承关系的映射方法--＞ 
```
＜discriminator column="subclass" type="character"/＞ 
```
＜!-- property元素为类声明了一个持久化的，JavaBean风格的属性--＞ 
```
＜property name="name" type="string"＞ 
    ＜column name="name" length="64" not-null="true" /＞ 
＜/property＞ 
＜property name="sex" not-null="true" update="false"/＞ 
```
＜!--多对一映射关系--＞
```
＜many-to-one name="friend" column="friend_id" update="false"/＞ 
```
＜!--设置关联关系--＞ 
```
＜set name="friends" inverse="true" order-by="id"＞ 
    ＜key column="friend_id"/＞ 
    ＜!--一对多映射--＞ 
    ＜one-to-many class="Cat"/＞ 
＜/set＞ 
```
＜!--多对多映射--＞ 
```
<bag name="orderdetails" cascade="save-update">
      <key column="ordersuuid" ></key>
      <one-to-many class="cn.itcast.erp.entity.Orderdetail"/>
</bag>

＜/class＞ 
＜/hibernate-mapping＞
```



