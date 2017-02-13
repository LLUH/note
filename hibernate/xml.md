```
<?xml version="1.0" encoding="UTF-8"?>
<!DOCTYPE hibernate-configuration PUBLIC
    "-//Hibernate/Hibernate Configuration DTD 3.0//EN"
    "http://www.hibernate.org/dtd/hibernate-configuration-3.0.dtd">
<hibernate-configuration>
    <session-factory>
```

```
    <!-- 第一部分：数据库基本配置 -->
```

```
        <property name="hibernate.connection.driver_class">
            com.mysql.jdbc.Driver
        </property>
        <property name="hibernate.connection.url">
                jdbc:mysql://localhost:3306/crm_hibernate_test
        </property>
        <property name="hibernate.connection.username">root</property>
        <property name="hibernate.connection.password">1234</property>
```

```
    <!-- 配置数据库方言 -->
```

```
        <property name="hibernate.dialect">
            org.hibernate.dialect.MySQLDialect
        </property>
```

```
    <!--第二部分： hibernate基本配置 -->
```

```
        <property name="hibernate.show_sql">true</property>
        <property name="hibernate.format_sql">true</property>
```

```
    <!-- 自动生成DDL 
            根据映射产生表结构的类型:
            create-drop:没有表结构创建，下次启动时删除重新创建。适合学习阶段
            create：只做创建
            update：探测表结构够的变化，对于数据库没有的，进行更新操作。适合学习阶段
            validate：对比与数据库的结构
            none:什么都不会做
    数据库必须自己手动创建，hibernate不会创建 -->
```

```
        <property name="hibernate.hbm2ddl.auto">none</property>
```

```
    <!--第三部分：映射配置 -->
```

```
        <mapping resource="com/itheima/domain/CstCustomer.hbm.xml"/>
    </session-factory>
</hibernate-configuration>
```

【属性文件的方式】

\* hibernate.properties

\*没有办法加载映射文件:

\*必须手动编码的方式加载映射文件:

\* configuration.addResource\("cn/itcast/vo/Customer.hbm.xml"\);

\* configuration.addClass\(Customer.class\);



【XML配置文件的方式】

**在Hiernate的核心配置文件中有三块内容配置：**

**\*1**必须的内容:连接数据库的基本信息及方言.

hibernate.dialect操作数据库方言

hibernate.connection.driver\_class连接数据库驱动程序

hibernate.connection.url连接数据库URL

hibernate.connection.username数据库用户名

hibernate.connection.password数据库密码



**\*2**Hibernate的基本配置：可选属性（显示SQL/格式SQL/hbm2ddl）

hibernate.show\_sql true在控制台上输出SQL语句

hibernate.format\_sql true格式化控制台输出的SQL语句

**hibernate.hbm2ddl.auto create/create-drop/update/validate生成DDL的策略.**

**\* create :每次都会创建一个新的表.\(测试的时候\)**

**\* create-drop :每次都会创建一个新的表,每次执行结束后,将这个表删除.\(测试的时候\)**

**\* update :如果没有表可以创建一个表,如果有表了更新表结构.**

**\* validate :校验映射和表中的字段的值是否一致,如果不一致就会报错.**

**\*\*\*\*\*实际开发中一般使用update、validate.**

**\*3**映射文件的加载:

&lt;mapping resource="cn/itcast/vo/Customer.hbm.xml" /&gt;

