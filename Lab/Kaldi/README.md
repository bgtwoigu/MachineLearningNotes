
**Build Kaldi**

```sh
git clone https://github.com/kaldi-asr/kaldi.git kaldi --origin upstream
cd kaldi
cd tools
extras/check_dependencies.sh

# install sugested packages

make

cd ../src
./configure --shared

make depend
make all
```
**Run Example**

```sh
cd ../egs
cd yesno
./run.sh
```
yesno是个最简单的例子，运行很快就结束了。接下来看看这个脚本做了什么
1. 从sourceforge上下载yesno的音频文件
音频文件名就代表了音频的label，每个音频有8个单词，分别为yes或者no，文件名中1代表yes，0代表no
2. 调用prepare_data.sh准备数据
3. 特征提取
4. mono training
5. graph compiler
6. decode


**Reference**

1. <a href="http://kaldi-asr.org/doc/">Kaldi官方网站</a>
2. <a href="https://shiweipku.gitbooks.io/chinese-doc-of-kaldi/content/acoustic_model.html">Kaldi中文文档</a>
3. <a href="https://www.gitbook.com/book/shiweipku/chinese-doc-of-kaldi/details>Kaldi中文文档pdf下载</a>