
**Note**
关于如何生成embedding

TensorFlow tutorial:
```sh
deep_columns = [
  tf.contrib.layers.embedding_column(workclass, dimension=8),
  tf.contrib.layers.embedding_column(education, dimension=8),
  tf.contrib.layers.embedding_column(gender, dimension=8),
  tf.contrib.layers.embedding_column(relationship, dimension=8),
  tf.contrib.layers.embedding_column(native_country, dimension=8),
  tf.contrib.layers.embedding_column(occupation, dimension=8),
  age, education_num, capital_gain, capital_loss, hours_per_week]
```
tflearn实现
```sh
        for cc, cc_size in self.categorical_columns.items():                                                                          
            cc_input_var[cc] = tflearn.input_data(shape=[None, 1], name="%s_in" % cc,  dtype=tf.int32)                                
            # embedding layers only work on CPU!  No GPU implementation in tensorflow, yet!                                           
            cc_embed_var[cc] = tflearn.layers.embedding_ops.embedding(cc_input_var[cc],    cc_size,  8, name="deep_%s_embed" % cc)    
            if self.verbose:                                                                                                          
                print ("    %s_embed = %s" % (cc, cc_embed_var[cc]))                                                                  
            flat_vars.append(tf.squeeze(cc_embed_var[cc], squeeze_dims=[1], name="%s_squeeze" % cc))  
         
```          


如果输入特征的取值是一个离散值，输入到神经网络时相当于输入一个向量，这个从代码里看还是比较清楚的。
但是如果特征的取值是多个离散值，比如user_installed_apps，一般用户都是有很多app的，这样输入的特征就是
[0,0,1,0,1......0,1,1,0]这样的，要是压缩到100维左右，估计得是类似full connection layer的方式了。


**Test**

我用github上的一个项目来做实验，看看是怎么运行的。
https://github.com/ichuang/tflearn_wide_and_deep

我的电脑上已经安装了tensorflow1.0，还需要装tflearn以及其他的包 

```sh
pip install pandas sub

git clone https://github.com/ichuang/tflearn_wide_and_deep.git
cd tflearn_wide_and_deep
```

下面开始训练模型。我这里运行的时候，有些实现调用了tensorflow的旧的API，需要改一下。
另外运行时会自动下载UCI的adult数据集，不需要额外下载。

```sh
# train wide model
python tflearn_wide_and_deep.py --verbose --n_epoch=2000 --model_type=wide --snapshot_step=500 --wide_learning_rate=0.0001 
```
输出结果，准确率~0.72

```sh
============================================================  Evaluation
  logits: (16281,), min=-6.03796768188, max=18.3984050751
Actual IDV
0    12435
1     3846
dtype: int64
Predicted IDV
0    14265
1     2016
dtype: int64

Confusion matrix:
actual           0     1
predictions             
0            11076  3189
1             1359   657
============================================================
```

下面开始训练deep模型
```sh
python tflearn_wide_and_deep.py --verbose --n_epoch=2000 --model_type=deep --snapshot_step=250 --run_name="deep_run" --deep_learning_rate=0.001
```
输出结果，准确率~0.86
```sh
============================================================  Evaluation
  logits: (16281,), min=-16.8078365326, max=7.2628493309
Actual IDV
0    12435
1     3846
dtype: int64
Predicted IDV
0    13089
1     3192
dtype: int64

Confusion matrix:
actual           0     1
predictions             
0            11615  1474
1              820  2372
============================================================
```

下面训练混合模型：
```sh
python tflearn_wide_and_deep.py --verbose --n_epoch=2000 --model_type=wide+deep --snapshot_step=250 \
    --run_name="wide+deep_run"  --wide_learning_rate=0.00001 --deep_learning_rate=0.0001 
```

输出结果，准确率~0.83

```sh
============================================================  Evaluation
  logits: (16281,), min=-11.3887681961, max=54.568195343
Actual IDV
0    12435
1     3846
dtype: int64
Predicted IDV
0    14677
1     1604
dtype: int64

Confusion matrix:
actual           0     1
predictions             
0            12153  2524
1              282  1322
============================================================
```


**Reference**


1. <a href="https://www.tensorflow.org/versions/master/tutorials/wide_and_deep/">TensorFlow Wide & Deep Learning Tutorial </a>

2. <a href="http://www.jianshu.com/p/7dc588d98a94">（翻译）TensorFlow 广度和深度学习教程</a>

3. <a href="http://stackoverflow.com/questions/38808643/tf-contrib-layers-embedding-column-from-tensor-flow">tf.contrib.layers.embedding_column from tensor flow</a>

4. <a href="https://github.com/tensorflow/tensorflow/blob/master/tensorflow/contrib/layers/python/layers/feature_column.py">Feature Embedding的TF实现</a>