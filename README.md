# sping-cloud-gateway
1 常见操作 https://blog.csdn.net/zjh_746140129/article/details/80101122
2 idea使用maven install报错maven Failed to execute goal org.apache.maven.plugins:maven-surefire-plugin:2.2
  [ERROR] Failed to execute goal org.apache.maven.plugins:maven-surefire-plugin:2.21.0:test (default-test) on project web_nanchang: There are test failures.
  
  出现上述错误有2种解决方式：
  
  1.当前模块的test包下的某个test类没有test方法，可以加上@Ignore注解
  2.在当前模块的pom.xml文件中加上如下内容即可解决
  
  <build>
     <plugins>
        <plugin>
           <groupId>org.apache.maven.plugins</groupId>
           <artifactId>maven-surefire-plugin</artifactId>
           <version>2.21.0</version>
           <configuration>
              <testFailureIgnore>true</testFailureIgnore>
           </configuration>
        </plugin>
     </plugins>
  </build>

3 Mac下配置Maven的问题：mvn -version, NB: JAVA_HOME should point to a JDK not a JRE.
Mac下配置Maven, 由于JDK的配置问题会引起如下的错误提示：

The JAVA_HOME environment variable is not defined correctly.

This environment variable is needed to run this program   

NB: JAVA_HOME should point to a JDK not a JRE.

经分析：

   $JAVA_HOME

   ls -l /usr/libexec/java_home

 vi  ~/.bash_profile

     .....      

     export JAVA_HOME=$JAVA_HOME    ###需要这设置这一句

     .....


4 maven  操作
https://my.oschina.net/mzdbxqh/blog/849040