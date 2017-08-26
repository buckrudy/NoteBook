==============================
sphinx + github + readthedocs
==============================

使用 sphinx_ + github_ + readthedocs_ 搭建个人静态博客, CentOS平台

参考 http://www.jianshu.com/p/78e9e1b8553a


-----------------------------
1. 安装Python3 和 pip3
-----------------------------

安装Python3::

    yum install python34


安装pip3::

    wget --no-check-certificate https://bootstrap.pypa.io/get-pip.py
    python3 get-pip.py


-----------------------------
2. 安装Sphinx
-----------------------------
::

    pip3 install Sphinx


-----------------------------
3. 创建工程
-----------------------------
3.1. 创建工程目录
^^^^^^^^^^^^^^^^^^^

例如在自己home目录下创建NoteBook, 作为我的工程目录
::

    mkdir NoteBook


3.2. 使用 ``sphinx-quickstart`` 命令创建工程
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

::
    
    cd NoteBook
    sphinx-quickstart
    
创建过程会提示你输入一些选项，一般直接回车 ``enter`` 就好了, 可以参考 建立sphinx工程_

创建完成后会生成4个文件:

- ``build`` 目录 运行make命令后，生成的文件都在这个目录里面
- ``source`` 目录 放置文档的源文件
- ``make.bat`` Windows 批处理命令
- ``Makefile``

现在就可以执行 ``make html``, 生成html文件了. 有一点需要注意的是，因为我是使用Python3，所以要修改一下 Makefile，不然执行 ``make html`` 时会报错

::
    
    SPHINXBUILD   = python -msphinx

改成

::
    
    SPHINXBUILD   = python3 -msphinx

source 目录下的 conf.py 是工程的配置文件，可以修改工程名称、主题、等等。比如我个人喜欢 ``sphinx_rtd_theme`` 主题，就可以在这里修改

::
    
    html_theme = 'alabaster'

改成

::
    
    html_theme = 'sphinx_rtd_theme'


---------------------------------------
4. 部署到github
---------------------------------------

在工程目录下执行

::

    git init
    git add .
    git commit -m "first add"
    git remote add origin https://github.com/[yourusename]/[yourrepository].git
    git push origin master

注意：[yourusename]/[yourrepository] 换成你的 github 名和仓库名。

4.1. 导入到 ReadtheDocs
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

- 到 github 里选择你使用的仓库，依次点击 Setting => Integrations & services => Add service => ReadTheDocs
- 到 ReadtheDocs import 这个仓库，导入成功后，点击阅读文档，便可看到 Web 效果了。

    sphinx 通常使用 reStructuredText 标记语言，如果使用 markdown 编写的文章，可以用 pandoc_ 转换

.. _sphinx: http://www.sphinx-doc.org
.. _github: http://www.github.com
.. _readthedocs: https://readthedocs.org
.. _建立sphinx工程: http://jwch.sdut.edu.cn/book/tool/UseSphinx.html#id5
.. _pandoc: http://www.pandoc.org/try/


