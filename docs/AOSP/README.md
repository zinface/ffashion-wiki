# aosp.repo-step

> AOSP 与 Android 源代码管理工具 - repo

### 关于 AOSP 的一些基准信息

- AOSP\
    全称 `Android Open Source Project`，中文意为`Android 开放源代码项目`。发起者是谷歌，主要用途是移动设备的系统。 `---摘自百度百科`

- `Android` 项目的版本与组成\
    `Android` 项目从目前的`AOSP`源代码中可以追溯到的最早版本是 `android-1.6_r1.2` ，该版本由 `107` 个项目组成。\
    `本文现阶段，Android` 项目最新可查看到的版本是 `android-13.0.0_r3`，该版本由 `1132` 个项目组成。
    
    `Android` 项目由成百上千个项目组成，即从古老的版本到本文所涉及的最新版本。\
    查看现已记录的 [历史构建版本表](./android-build-versions.md)

- 源代码管理工具 `git`\
    `Git` 是一个开源的分布式版本控制系统，用于敏捷高效地处理任何或小或大的项目。 `Git` 是 `Linus Torvalds` 为了帮助管理 `Linux` 内核开发而开发的一个开放源码的版本控制软件。

- Android 源代码管理工具 `repo`\
    `Android` 源码包含数百个 `git` 库，光是下载这么多的 `git` 库就是一项繁重的任务，所以 `Google` 开发了`repo`，它是用于管理 `Android` 版本库的一个工具，使用了 `Python` 对 `git` 进行了一定的封装，简化了对多个 `Git` 版本库的管理。 `


## 安装 repo Android源代码管理工具并获取 AOSP 源代码

- 获取 repo 工具:\
    参考[清华大学开源镜像站][tuna-heplp-aosp] Android 镜像使用帮助
    ```bash
    # 正常在 linux 环境下可以使用最简单的方式安装 repo 脚本命令
    mkdir -p ~/.local/bin
    curl https://storage.googleapis.com/git-repo-downloads/repo > ~/.local/bin/repo
    chmod a+x ~/.local/bin/repo

    # 配置以下环境变量
    # 只有每次在使用 `repo init` 的时候，才会需要下载完整的 repo 脚本，它就是 repo 的 wrapper。
    # repo
    export REPO_URL='https://mirrors.bfsu.edu.cn/git/git-repo'
    ```

[tuna-heplp-aosp]: https://mirrors.tuna.tsinghua.edu.cn/help/AOSP/

- 下载来源于清华的 AOSP 源代码

    下载 AOSP 源代码的方式有三种：
    - 第一种是下载一个由每月更新的 `aosp-latest.tar` 初始化包，按此文目前为止可以下载到保守估计的可追溯的最新版本为 `android-13.0.0_r3`，约 `190GB` 数据，包含可追溯到的所有历史版本。
        ```bash
        # 当你使用 `wget` 下载来源于清华的最新 aosp-laster.tar 初始化包时
        # 请你确保硬盘有足够的空间来存储大约 200G 的压缩包文件
        # 其次，你还需要确保当前硬盘或其它硬盘有足够的空间来存储大约 200G 的解压后的目录。
        # 使用 tar xf aosp-latest.tar 来解压初始化包
            # 解压后将会产生一个 aosp 目录
            # 在 aosp 目录下包含一个 .repo 隐藏目录
        $ tree -a
        .
        ├── aosp                
        │   └── .repo           # 解压的 .repo 目录大约有 200G 
        └── aosp-latest.tar     # 初始化包大约有 200G
        
        # 再次说明，在进入 aosp 目录后的一切
            # 当前所在目录仅有一个 .repo 目录
            # 您可以通过 `repo list` 列出当前 manifest 元数据下的所有项目
            # 执行 `repo sync` 将会从服务器获取最新代码
            # 执行 `repo sync -l` 将会立即同步出本地最新源代码结构，同时将会产生约 120G 以上的文件。
            # 
        ```