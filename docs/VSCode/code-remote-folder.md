# 命令行打开VSCode远程开发

之前总觉得vscode打开远程服务器上的文件或者文件夹的方式不够优雅，需要打开 vscode->点击左侧的远程开发图标->选择server并开启窗口->在窗口中打开文件夹，填写文件夹地址，然后才能打开。由于这个过程过于麻烦，很多时候都懒得开vscode，直接vim解决。

最近发现这个繁杂的过程完全可以省略，在本地终端输入一行指令即可。具体为

```bash
code --remote ssh-remote+<remote_name> <remote_path>
```
其中，remote_name为在.ssh/config中配置的远程服务器别名，remote_path为要打开的远程服务器上的绝对路径。

有了这个指令，屁大点的文件也可以无痛开一个远程vscode来进行编辑了。