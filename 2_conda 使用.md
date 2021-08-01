conda 使用

~~~
conda --version
conda updata conda 
conda env list   conda info -e
conda create -n env_name python=o3.6
conda remove -n env_name --all
conda search package_name
conda install package_name
conda remove package_name
conda update package_name

conda activate 激活base环境
conda activate env_name
deactivate env_name


~~~

conda数据源管理

~~~
#显示目前conda的数据源有哪些
conda config --show channels
#添加数据源：例如, 添加清华anaconda镜像：
conda config --add channels https://mirrors.tuna.tsinghua.edu.cn/anaconda/pkgs/free/
conda config --add channels https://mirrors.tuna.tsinghua.edu.cn/anaconda/pkgs/main/
conda config --set show_channel_urls yes
#删除数据源
conda config --remove channels 
~~~

生成运行环境所依赖的包

~~~
pip生成requirement.txt

pip freeze > requirements.txt
pip install -r requirements.txt

~~~





