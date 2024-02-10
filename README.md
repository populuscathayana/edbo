```bash
conda create -n edbo python==3.8
conda activate edbo
conda install -c conda-forge pip
pip install rdkit
pip install mordred
conda install pytorch=1.10.0 -c pytorch
pip install edbo
conda install jupyterlab
```

这个 4 年前的上古环境...这个是我改进后的配置方案了

```bash
git clone https://github.com/b-shields/edbo.git
```

存在版本问题，需要降级


主要就修改下 random 变为固定的手动指定，看过了，在 doc 里没写，需要阅读源码。还好源码结构还算清楚。

bro.py(Class BO)-->Class Init(.init_scheme)

主要修改内容：

修改 BO 中的参数，加入了 results 参数，为指定的一个 DataFrame，当然也可以是原内容的切片，并把 init_method 修改为 ’external‘

省略 bo.init_sample()
(删除之后所有的 seed)

定义一个新的函数，simulate_ext()，用来指定针对 external 的 simulate



修改了哪些部分见 git 记录
