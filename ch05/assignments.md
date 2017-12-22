# CH05 - 家庭作业


## 熟悉 Debian 系列发行

* 包管理
  * 学习 `apt`、`aptitude`、`apt-get`、`apt-cache` 等命令的使用
  * 学习修改 APT 的仓库配置文件
* 网络配置
  * 熟悉网络接口配置文件位置及语法
 
>##### 参考
>* https://linuxtoy.org/archives/debian-tips.html
>* https://help.ubuntu.com/lts/serverguide/networking.html
>* https://help.ubuntu.com/lts/serverguide/package-management.html

## 文件编码转换

学习使用文件编码转换命令 （`iconv`/`enconv`/`enca`/`convmv`）

>##### 参考
>* [Linux 转换文件名编码和文件编码](http://niyunjiu.iteye.com/blog/739224)

## 图片转换

```
## 安装 ImageMagick 和 optipng
yum install 

## 更改图片大小
convert -resize 300 profile.jpg profile_small.jpg

## 给图片加阴影
convert screenshot.jpg
\( +clone -background black -shadow 60×5+0+5 \)
+swap -background white -layers merge +repage shadow.jpg

## PNG 图片瘦身
optipng file.png
```

>##### 参考
>* `man convert`
>* `man optipng`
>* http://www.imagemagick.org/
>* [LinuxCast.net每日播客](http://study.163.com/course/courseMain.htm?courseId=221001) 之课时28

## 音频转换

2、使用命令行转换音频

```
## 安装 sox
yum install sox

## 将Apple的AIFF格式转换为Microsoft的WAV格式
sox filename.aiff filename.wav

## 将一个11.025K采样、16bit的WAV文件转化为8K采样、8bit的WAV文件
sox infile.wav -r 8000 -b outputfile.wav

## 将wav格式转换为gsm格式
sox 00.wav -r 8000 -c 1 00.gsm resample -ql
```

>##### 参考
>* `man sox`
>* [音频处理领域的瑞士军刀──SoX](http://blog.csdn.net/brave_heart_lxl/article/details/5715920)
>* [sox :音频文件转换命令](http://www.2cto.com/os/201107/97208.html)

## 视频转换

```
## 配置 RpmFusion 仓库
## 参考 https://rpmfusion.org/Configuration 

## 安装 ffmpeg 和 mencoder
yum -y install ffmpeg mencoder

## mpg/avi/ogg 转换
ffmpeg -i video_origine.avi video_finale.mpg
ffmpeg -i video_origine.mpg video_finale.avi
ffmpeg -i video_origine.avi video_finale.ogg

## 将rm格式视频转换成mp4格式
mencoder -ovc lavc -lavcopts vcodec=mpeg4 -oac mp3lame source.rm -o dest.mp4

## 将三个flv格式的视频合并成一个
mencoder -ovc copy -oac mp3lame 0.flv 2.flv 3.flv -o test.flv
```

>##### 参考
>* http://ffmpeg.org/ffmpeg.html
>* [LinuxCast.net每日播客](http://study.163.com/course/courseMain.htm?courseId=221001) 之课时14
>* [19 ffmpeg commands for all needs](http://www.catswhocode.com/blog/19-ffmpeg-commands-for-all-needs)
>* [关于 ffmpeg 的总结](http://blog.csdn.net/jixiuffff/article/details/5709976)
>* [MEncoder的基础用法](http://www.mplayerhq.hu/DOCS/HTML/zh_CN/mencoder.html)
>* [Linux下三款流行的命令行文件转换工具](http://www.techweb.com.cn/network/system/2016-12-21/2456348.shtml)
> * GUI 工具 -- [FF Multi Converter](https://sites.google.com/site/ffmulticonverter/home) (rpmfusion仓库)
> * [FF Multi Converter：流行文件格式转换器](https://linuxtoy.org/archives/ff-multi-converter.html)
