
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

**Reference**

http://kaldi-asr.org/doc/