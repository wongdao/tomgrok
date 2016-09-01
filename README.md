# Tomgrok

### Tomgrok 是什么？

Tomgrok 是基于对 OpenGrok 和 Apache Tomcat 包装的一套脚本，致力于打造方便易用的源代码库，以提供对源代码进行 Web 式交叉索引查询。开箱即用，使用简单命令就能配置好 Apache Tomcat + OpenGrok，而无需对他们进行过多了解。OpenGrok 基本支持现在大部分语言，如 C、C++、Java、Javascript 等，具体详见：[OpenGrok Supported Languages and Formats][]。

### 怎么用？
#### 安装

下载后直接运行 `tomgrok` 即可，建议设置目录到你的搜索路径 PATH，并将自动完成脚本 `tomgrok.completion` 加入到你的 `~/.bashrc`。

注意：需要 Exuberant Ctags 或 Universal Ctags。

#### 使用说明

一个 Tomcat 服务器支持多个 Web App，我们称之为 Context，每个 Context 都可以加入多个 Project 的源代码，每个 Context 和 Project 都有自己的名字，比如 127.0.0.1/src/xref/mobile 这个网址， src 就是一个 Context 的名字, mobile 则是 一个 project 名字。

先用下面的命令建立一个 Web App：
``` bash
tomgrok create mysrc
```
然后用下面命令将某一个项目链接到这个 web app：
``` bash
tomgrok link mysrc <your-proj-path>
```
然后开始建立索引：
``` bash
tomgrok index mysrc
```
索引建立完毕，再启动 Tomcat：
``` bash
tomgrok startup # （关闭服务器是： tomgrok shutdown）
```
然后就可以打开浏览器浏览你的代码了： http://localhost:8080/mysrc

默认情况下端口号为：8080

[OpenGrok Supported Languages and Formats]: https://github.com/OpenGrok/OpenGrok/wiki/Supported-Languages-and-Formats
