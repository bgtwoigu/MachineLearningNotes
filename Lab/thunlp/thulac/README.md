
#Note

**使用maven编译**
创建pom.xml文件
```xml
<?xml version="1.0" encoding="UTF-8"?>
<project xmlns="http://maven.apache.org/POM/4.0.0"
         xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
         xsi:schemaLocation="http://maven.apache.org/POM/4.0.0 http://maven.apache.org/xsd/maven-4.0.0.xsd">
    <modelVersion>4.0.0</modelVersion>

    <groupId>thu</groupId>
    <artifactId>thulac</artifactId>
    <version>1.0</version>
    <dependencies>
        <dependency>
            <groupId>junit</groupId>
            <artifactId>junit</artifactId>
            <version>4.12</version>
        </dependency>
    </dependencies>
    <build>
        <plugins>
            <plugin>
                <groupId>org.apache.maven.plugins</groupId>
                <artifactId>maven-compiler-plugin</artifactId>
                <configuration>
                    <source>1.8</source>
                    <target>1.8</target>
                </configuration>
            </plugin>
        </plugins>
    </build>
</project>
```
然后进行编译
```sh
mvn compile
```

运行简单的分词命令
```sh
java -classpath target/classes org.thunlp.thulac.main.Main -seg_only -model_dir /data/ftp/model/nlp/thunlp/models  -input /data/ftp/data/nlp/icwb2-data/testing/pku_test.utf8  -output pku_test.splitted.txt
```




**Reference**

1. <a href="https://github.com/thunlp/THULAC-Java">Thulac项目</a>
2. <a href="http://sighan.cs.uchicago.edu/bakeoff2005/">ICWB2 数据集</a>
3. <a href="http://thulac.thunlp.org/sendMessage_v1_1">模型下载地址</a>
