# comfyui_distributed

新机器全都按照comfyui纯净版，直接github下载安装。

我这里先在3号机上安装好了，做了个压缩包，后面局域网里的其他机器安装直接解压，然后安装requirement和一些必须的依赖即可。

安装前提，请提前准备好
ptyhon-3.12.7（用了几个版本，最后是这个版本成功的）
这个安装的时候一定要勾选添加下面的环境变量

全都解压到D盘根目录。
D:\ComfyUI_Pure

（安装过程不用代理）
然后在这个目录的上面，cmd，然后安装requirement（是在D:\ComfyUI_Pure这个目录下面执行下面的安装命令）
python -m pip install -r requirements.txt --no-cache-dir

安装cuda，这里1050ti和笔记本的3060都是安装的这个cuda118
python -m pip install torch torchvision torchaudio --index-url https://download.pytorch.org/whl/cu118 --force-reinstall --no-cache-dir

安装ffmpeg
python -m pip install opencv-python imageio-ffmpeg

启动的时候需要用低显存模式，我这里写了个bat文件，直接运行这个bat文件就可以启动了
@echo off
python main.py --listen --port 8188 --enable-cors-header --lowvram
pause



压缩包里都下载好了插件和模型
这里只作为worker干活的机器，只需要一个模型和两三个插件，其他的暂时都不用装

models里面用到的放大插件，只用到了第一个2倍的这个模型就行
<img width="708" height="312" alt="image" src="https://github.com/user-attachments/assets/b197dbbb-a04d-42ee-a139-43ec6c32b766" />

插件这几个就够了
<img width="702" height="355" alt="image" src="https://github.com/user-attachments/assets/dac02586-377b-440c-9159-f07e8579c269" />


23号机两个worker的情况：
15s的视频-16帧的，做了放大插针，2个worker用了9分钟多
