# Ubuntu24.04+Gemini336 的环境搭建
1、安装基础依赖
sudo apt update && sudo apt upgrade -y
sudo apt install -y git cmake build-essential libusb-1.0-0-dev libgl1-mesa-glx libglib2.0-0

2、安装 Anaconda（管理 Python 环境，避免系统 Python 冲突）
官网下载 Linux 版 Anaconda：https://www.anaconda.com/download/
下载后在终端执行（替换成你的实际文件名）：bash Anaconda3-2024.02-1-Linux-x86_64.sh（可以按tab键获取名字）


下载完成后，就可以一步步安装了。

    进入下载目录：在终端中输入 cd ~/Downloads 并回车。

    运行安装脚本：在终端中，输入 bash Ana 后，按下键盘上的 Tab 键。系统会自动补全文件名。然后回车，安装程序就会启动。

    阅读许可协议：屏幕上会出现一堆文字说明。这时，你需要按住 Enter 键不放，直到屏幕最下方出现 Do you accept the license terms? [yes|no] 的提示。

    接受协议：输入 yes 并回车。

    确认安装位置：安装程序会询问安装路径。直接按 Enter 键使用默认的 /home/你的用户名/anaconda3 目录即可。

    关键一步：初始化：当出现 Do you wish the installer to initialize Anaconda3... 的提示时，一定要输入 yes 并回车。这是最容易被忽略的步骤，它将 conda 命令自动添加到系统路径中，确保你在终端任何地方都能使用它。

    安装完成：看到 "Thank you for installing Anaconda3!" 的字样，就说明安装成功了。


3、创建并激活虚拟环境
# conda create -n gemini336_sim python=3.10 -y  # 3.10是ob-python官方推荐的最稳定版本
***遇到了问题
仍然提示 conda: command not found

可能是安装时没有选 yes 初始化，或者手动修改了配置。请执行以下命令手动添加 conda 路径：
echo 'export PATH="$HOME/anaconda3/bin:$PATH"' >> ~/.bashrc
source ~/.bashrc



# conda activate gemini336_sim



如果 conda init 也提示找不到命令？

极少数情况下 conda 命令虽然可用但路径不完整，可以手动添加初始化代码：

eval "$(conda shell.bash hook)"
4、安装奥比中光 Python SDK（ob-python）
直接用 pip 安装预编译的 wheel 包

通过 PyPI 安装社区维护的版本（最简便）

这是目前最省心的方法。社区开发者维护了一个名为 pyorbbecsdk-community 的版本，可以直接通过 pip 安装，省去了手动编译的麻烦。

在你的 gemini336_sim 虚拟环境中，执行以下命令即可：
bash

pip install pyorbbecsdk-community


5、安装其他仿真数据采集需要的库
pip install open3d==0.18.0 numpy==1.26.4 matplotlib==3.8.4











#####ubantu中安装app
1、本地安装sudo dpkg -i com.alibabainc.dingtalk_8.1.0.6021101_amd64.deb
      若出现依赖问题  sudo apt install -f（自动修复依赖问题）
2、软件源安装sudo apt install app_name

