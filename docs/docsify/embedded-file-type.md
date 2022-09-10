# Docsify 在文档文件中嵌入另外一个文件

> [!WARNING]
> 访问 docsify 官方说明文档: [Link][docsify-link]

[docsify-link]: https://docsify.js.org/#/embed-files?id=embedded-file-type

在编写 `docsify` 时可能需要嵌入一些文件，目前 `docsify` 已经提供了这个功能，你不仅仅可以嵌入 `md` 文件，你还可以嵌入一些不同的文件类型。

- 嵌入方式

    可以使用下面的方式进行嵌入。
    ```markdown
    [filename](_media/example.md ':include')

    在链接到 md 文件后，在文件的后端添加参数：':include' 就可以了。
    需要注意的是 :include 需要单引号(')来进行包裹。
    ```

- 可以嵌入的文件类型

    在当前情况下，一些特定的扩展文件名可以被自动识别，并自动使用类类型。
    - 可以支持的嵌入类型为：
        - **iframe**: `.html`, `.htm`
        - **markdown**: `.markdown`, `.md`
        - **audio**: `.mp3`
        - **video**: `.mp4`, `.ogg`
        - **code**: 其他文件类型
    
    当然，你也是可以强制指定嵌入文件的类型的。

    - 例如一些录屏中的 - (葬歌 Gentoo):
    
        ```markdown
        # 通过标识嵌入类型 ':include :type=video'
        [](http://101.35.119.41/fileupload/download/9e1139e78413936acf2d737e6d8aa75b ':include :type=video')
        ```