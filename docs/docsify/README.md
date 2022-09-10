# 关于 docsify 

- 安装与立即使用 
    1. 使用 `npm` 包管理器来安装它
        ```bash
        npm i docsify-cli -g
        ```
    2. 在你的项目中使用 `docsify-cli` 初始化文档目录结构
        ```bash
        # 创建临时目录或进入正式项目目录中
        # 执行命令初始化创建一个 docs 目录用于存放文档
        docsify-cli init ./docs

        # 在当前目录中将会创建一个 docs 目录
        $ tree -a
        .
        └── docs
            ├── index.html  # 入口文件
            ├── .nojekyll   # 用于阻止 GitHub Pages 忽略掉下划线开头的文件
            └── README.md   # 做为主页内容渲染
        ```
    3. 在您的项目中立即启动文档预览服务
        ```bash
        # 在当前目录中执行
        docsify serve ./docs

        # Serving /tmp/tmp.eI4h1SP3eM/docs now.
        # Listening at http://localhost:3000
        ```