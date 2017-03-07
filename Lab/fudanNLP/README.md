
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


java -classpath target/classes org.thunlp.thulac.main.Main -seg_only -model_dir /data/ftp/model/nlp/thunlp/models  -input /data/ftp/data/nlp/icwb2-data/testing/pku_test.utf8  -output pku_test.splitted.txt
```

对比分词结果，复旦NLP和ThuNLP的结果不一样，可能词典不一样。训练时的标注可能也不一样。

**Reference**

