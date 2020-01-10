存放api中心的文档相关内容

产品： products下根据产品存放文档

目录： SUMMARY.md是目录文件

书写规范：
一、SUMMARY.md

    * [一级目录] （对应文章路径）

        * [二级目录] (对应文章路径)

            * [三级目录] (对应文章路径)

[注]：每级目录前*号以1个tab键分割


二、文章

标题： 默认与SUMMARY.md的标题名称一致，文章中不用再次填写

时间： 默认获取创建文档的时间

内容： 以h2开始，默认右侧导航抓取h2标题

跳转： 在地址前追加文件路径/static/docs-content/

       eg:  JobResult: (/static/docs-content/products/通用接口/获取异步任务进度（JobResult）.md#错误码)

三、SUMMARY注意事项

每个文档仓库作为滴滴云文档系统的子模块，需要注意一下规范

1、去掉SUMMARY.md开头的#SUMMARY字段
2、一级目录只能存在一个，作为模块子文档的大标题
3、其余目录相对于一级目录缩进一级

具体参考SUMMARY.default.md