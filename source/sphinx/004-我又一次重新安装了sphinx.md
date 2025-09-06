# 我又一次重新安装了sphinx

此时我所在的文件夹名称为`autojx`。

刚创建了一个虚拟环境,使用`pip list`命令查看

```
Package Version
------- -------
pip     25.2 
```

使用`pip freeze > requirements.txt`命令导出`requirements.txt`文件

```
requirements.txt里面什么都没有
```

## 安装sphinx

使用`pip install sphinx -i https://mirrors.aliyun.com/pypi/simple/`安装`sphinx`，

然后再使用`pip freeze > requirements.txt`命令查看所安装的库,

以下是`requirements.txt`文件里面的内容。

```
alabaster==1.0.0
babel==2.17.0
certifi==2025.8.3
charset-normalizer==3.4.3
colorama==0.4.6
docutils==0.21.2
idna==3.10
imagesize==1.4.1
Jinja2==3.1.6
MarkupSafe==3.0.2
packaging==25.0
Pygments==2.19.2
requests==2.32.5
roman-numerals-py==3.1.0
snowballstemmer==3.0.1
Sphinx==8.2.3
sphinxcontrib-applehelp==2.0.0
sphinxcontrib-devhelp==2.0.0
sphinxcontrib-htmlhelp==2.1.0
sphinxcontrib-jsmath==1.0.1
sphinxcontrib-qthelp==2.0.0
sphinxcontrib-serializinghtml==2.0.0
urllib3==2.5.0

```

此时我所在的文件夹名称为`autojx`，下面有一个文件`requirement.txt`。

## 创建一个文档

我现在要运行`sphinx-quickstart`命令来创建一个文档了。

在命令行输入了`sphinx-quickstart`，然后，终端窗口输出了以下内容。

```
(.venv) F:\furo\autojx>sphinx-quickstart
欢迎使用 Sphinx 8.2.3 快速配置工具。

请输入接下来各项设定的值（如果方括号中指定了默认值，直接
按回车即可使用默认值）。

已选择根路径：.

有两种方式来设置用于放置 Sphinx 输出的构建目录：
一是在根路径下创建“_build”目录，二是在根路径下创建“source”
和“build”两个独立的目录。
> 独立的源文件和构建目录（y/n） [n]: y

项目名称将会出现在文档的许多地方。
> 项目名称: autojx
> 作者名称: 醉摘镜中花
> 项目发行版本 []: 

如果用英语以外的语言编写文档，
你可以在此按语言代码选择语种。
Sphinx 会把内置文本翻译成相应语言的版本。

支持的语言代码列表见：
https://www.sphinx-doc.org/en/master/usage/configuration.html#confval-language。
> 项目语种 [en]: zh_CN

正在创建文件 F:\furo\autojx\source\conf.py。
正在创建文件 F:\furo\autojx\source\index.rst。
正在创建文件 F:\furo\autojx\Makefile。
正在创建文件 F:\furo\autojx\make.bat。

完成：已创建初始目录结构。

你现在可以填写主文档文件 F:\furo\autojx\source\index.rst 然后创建其他文档源文件了。 像这 
样用 Makefile 构建文档：
  make builder
此处的“builder”代指支持的构建器名称，比如 html、latex 或 linkcheck。
```

以上终端内容包含本人的配置选项。

结束后目录结构如下所示

```
autojx
├── build
├── make.bat
├── Makefile
└── source
   ├── conf.py
   ├── index.rst
   ├── _static
   └── _templates
```

文档内容可在autojx/source/下自行书写

## 安装一个自己喜欢的主题

目前，我比较喜欢`furo`

```
pip install furo -i https://mirrors.aliyun.com/pypi/simple/
```

在`conf.py`中配置主题

```python
# The theme to use for HTML and HTML Help pages.  See the documentation for
# a list of builtin themes.
#
html_theme = 'furo'
```

##  配置markdown语法

安装`myst_parser`用于解析markdown语法

```
pip install myst_parser -i https://mirrors.aliyun.com/pypi/simple/
```

在`conf.py`中配置解析

```python
extensions = [
    'sphinx.ext.duration',
    'myst_parser', # 解析markdown语法
]

source_suffix = {
    '.rst': 'restructuredtext',
    '.txt': 'markdown',
    '.md': 'markdown',
}
```

## 文档目录及结构


本人倾向于使用markdown的方式建立文档结构及目录结构（其他的本人不会）。

最好每个文档文件夹里面都有一个index.md文件用来存储目录结构。并由外层的index.md文件指向内层的index.md。
当然，index.md中的目录树也可以指向某个文档。具体指向可以参考本文档目录结构。

```
└── source
    ├── sphinx
    │   └── index.md
    │   └── 01.md
    │   └── 01文件夹   
    │   └── 02文件夹  
    ├── pip
    │   └── index.md
    │   └── 01.md
    │   └── 01文件夹   
    │   └── 02文件夹 
    ├── index.md
    ├── conf.py
```


### 部分目录文件示例

在source文件夹下建立一个index.md文件，文件内目录树结构指向其子文件夹的index.md文件
例：
`source/index.md`文件的目录树内容：

````
```{toctree}
:hidden:

sphinx/index
pip/index
```
````

`source/sphinx/index.md`

````
```{toctree}
:hidden:

01
01文件夹
02文件夹
```
````

**具体效果可自行尝试**

## 文档书写

现在可以书写你自己的文档了，自己随意发挥吧。具体目录结构及构建方式可查看本文档源码或是查看官方文档，这里不再详述。

## 最终的`requirements.txt`文件

```
accessible-pygments==0.0.5
alabaster==1.0.0
babel==2.17.0
beautifulsoup4==4.13.5
certifi==2025.8.3
charset-normalizer==3.4.3
colorama==0.4.6
docutils==0.21.2
furo==2025.7.19
idna==3.10
imagesize==1.4.1
Jinja2==3.1.6
markdown-it-py==3.0.0
MarkupSafe==3.0.2
mdit-py-plugins==0.5.0
mdurl==0.1.2
myst-parser==4.0.1
packaging==25.0
Pygments==2.19.2
PyYAML==6.0.2
requests==2.32.5
roman-numerals-py==3.1.0
snowballstemmer==3.0.1
soupsieve==2.8
Sphinx==8.2.3
sphinx-basic-ng==1.0.0b2
sphinxcontrib-applehelp==2.0.0
sphinxcontrib-devhelp==2.0.0
sphinxcontrib-htmlhelp==2.1.0
sphinxcontrib-jsmath==1.0.1
sphinxcontrib-qthelp==2.0.0
sphinxcontrib-serializinghtml==2.0.0
typing_extensions==4.15.0
urllib3==2.5.0

```

**注：** 文档仅供参考。
