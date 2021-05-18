仅为SpringBoot启动类入口依赖

依赖添加步骤如下：

git clone  https://github.com/lucknhb/api-spring-boot-autoconfigure.git     入口依赖此自动配置

mvn  clean  install

git clone https://github.com/lucknhb/api-spring-boot-starter.git

mvn  clean  install

在新建项目中maven依赖

```xml
<dependency>
  <groupId>com.nhb</groupId>
  <artifactId>api-spring-boot-starter</artifactId>
  <version>1.0.0</version>
</dependency>
```

功能使用步骤如下：

在SringBoot配置文件中开启

```properties
com.nhb.api.scan-package=需要扫描的控制层
#是否开启 默认为true
com.nhb.api.enable=true  
```

```wiki
@ApiLabel全局统一 API 注解  可作用于 类 方法 参数 属性字段
```

使用示例：

```java
//控制层
@ApiLabel("测试用例")
@RestController
public class IndexController {
    @ApiLabel(value = "测试方法",description = "仅用于测试使用")
    @GetMapping("/index")
    public String index(@ApiLabel("用户数据") User user){

        return "Hello World";
    }
}

//自定义类
@ApiLabel("用户")
public class User {
    @ApiLabel("姓名")
    private String userName;
    @ApiLabel("依赖用户")
    private List<User> users;
    @ApiLabel("年龄")
    private Integer age;

    public String getUserName() {
        return userName;
    }

    public void setUserName(String userName) {
        this.userName = userName;
    }

    public List<User> getUsers() {
        return users;
    }

    public void setUsers(List<User> users) {
        this.users = users;
    }

    public Integer getAge() {
        return age;
    }

    public void setAge(Integer age) {
        this.age = age;
    }
}
```

访问页面：

```http
http://127.0.0.1:port/
```

![image-20210518151204981](C:/Users/luck_nhb/AppData/Roaming/Typora/typora-user-images/image-20210518151204981.png)

 最后感谢D2Admin开源Vue模板