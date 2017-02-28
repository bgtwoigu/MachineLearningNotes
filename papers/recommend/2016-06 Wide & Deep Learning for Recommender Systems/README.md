

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

