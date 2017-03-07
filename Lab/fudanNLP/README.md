
#Note

**使用maven编译**

```
然后进行编译
```sh
git clone https://github.com/FudanNLP/fnlp.git
cd fnlp
mvn package -Dmaven.test.skip=true
mvn dependency:copy-dependencies -DoutputDirectory=libs

cd models
wget https://github.com/FudanNLP/fnlp/releases/download/v2.1/dep.m
wget https://github.com/FudanNLP/fnlp/releases/download/v2.1/pos.m
wget https://github.com/FudanNLP/fnlp/releases/download/v2.1/seg.m



```




**Reference**

