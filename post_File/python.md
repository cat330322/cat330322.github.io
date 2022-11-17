python

---



```
pip3 install --upgrade pip
```



---



conda

```
#添加镜像
conda config --add channels https://mirrors.tuna.tsinghua.edu.cn/anaconda/pkgs/free/
conda config --add channels https://mirrors.tuna.tsinghua.edu.cn/anaconda/pkgs/main/
conda config --add channels https://mirrors.tuna.tsinghua.edu.cn/anaconda/cloud/conda-forge/
conda config --add channels https://mirrors.tuna.tsinghua.edu.cn/anaconda/cloud/bioconda/
```

```
conda -version

conda create --name pythondemo python=3.7.0
conda config --show-sources 
```

```
ssl_verify: true
channels:
- http://mirrors.tuna.tsinghua.edu.cn/anaconda/pkgs/free/win-64/
- http://mirrors.tuna.tsinghua.edu.cn/anaconda/pkgs/main/win-64
show_channel_urls: true
```

```
channels:
  - defaults
show_channel_urls: true
default_channels:
  - http://mirrors.tuna.tsinghua.edu.cn/anaconda/pkgs/main
  - http://mirrors.tuna.tsinghua.edu.cn/anaconda/pkgs/r
  - http://mirrors.tuna.tsinghua.edu.cn/anaconda/pkgs/msys2
custom_channels:
  conda-forge: http://mirrors.tuna.tsinghua.edu.cn/anaconda/cloud
  msys2: http://mirrors.tuna.tsinghua.edu.cn/anaconda/cloud
  bioconda: http://mirrors.tuna.tsinghua.edu.cn/anaconda/cloud
  menpo: http://mirrors.tuna.tsinghua.edu.cn/anaconda/cloud
  pytorch: http://mirrors.tuna.tsinghua.edu.cn/anaconda/cloud
  pytorch-lts: http://mirrors.tuna.tsinghua.edu.cn/anaconda/cloud
  simpleitk: http://mirrors.tuna.tsinghua.edu.cn/anaconda/cloudnaconda/cloud
```

```
conda create --name pythondemo python=3.7.0
conda info --env
conda activate pythondemo
(python)
exit()
conda deactivate
```

```
https://pypi.tuna.tsinghua.edu.cn/simple/
```

