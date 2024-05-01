conda create --name newName python=3.7  //创建虚拟环境
activate newName //激活虚拟环境
conda env list //查看虚拟环境
conda activate user //切换到环境user
cd /mnt/d  //进入d盘
cd git //进入git文件夹
ls //查看当前文件夹下的目录
mkdir  //创建目录“pychontext”
cd pytchontext //进入目录pychontext
git clone https://github.com/yunjey/pytorch-tutorial.git //cione项目到pytchontext
cd ..   //退回到上一级目录

python --version //查看python版本

Ctrl + D //退出当前界面cd m

conda list //查看安装的包

python --version //检查python版本

conda remove -n your_env_name --all //删除虚拟环境

conda remove --name $your_env_name  $package_name //删除虚拟环境中的包