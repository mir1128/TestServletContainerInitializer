# ServletContainerInitializer vs ServletContextListener


原始[链接](http://stackoverflow.com/questions/13254620/meta-inf-services-in-jar-with-gradle)



ServletContainerInitializer 设计的初衷是编译成jar包,然后放到webapps/app/META-INF/lib里作为“插件”，应用 启动的时候hook Servlet Contianer启动过程，并进行干预。如果放到web应用的classpath里是不会被自动加载的。对于web应用，应该使用`ServletContextListener`对应用的启动过程进行干预



示例程序验证方法：

1. gradle build
2. 将build/libs目录下的jar包放到tomcat webapps下面的一个应用里（如examples）
3. 启动tomcat
4. 在tomcat的logs目录下grep "CONTAINER INITIALIZER!" * 即可找到结果






