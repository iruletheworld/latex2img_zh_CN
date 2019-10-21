LaTex :code:`standalone` 包的配置
===================================

本教程是基于由 `Martin Scharrer
<https://bitbucket.org/martin_scharrer/standalone/src/default/>`_
开发的 |standalone| 包（自带 :code:`standalone` 类），故此于此对此包稍作讲解。

.. |standalone| raw:: html

   <em>
   <a href="https://ctan.org/pkg/standalone?lang=en">standalone</a>
   </em>

.. note:: :code:`standalone` (*complex*) [#]_

    :code:`standalone` 是LaTex中非常有用的一个包。本教程主要讲述怎样利用此包来进行图片的转换，但此包其实还有其它相当多的应用。 `Overleaf
    <https://www.overleaf.com/learn/latex/Multi-file_LaTeX_projects#The_standalone_package>`_ 上有一个非常有用的教程。

:code:`standalone` 的转换命令配置
----------------------------------

:code:`standalone` 本身的 `说明文档 <http://mirrors.ibiblio.org/CTAN/macros/latex/contrib/standalone/standalone.pdf>`_ 已经对配置有详尽的说明，此处重点说一下转换成图片需要用到的 :code:`convert` 选项。

配置 :code:`convert` 需要在 :code:`documentclass` 中进行。以下是一个利用 :code:`pdf2svg` 转换为SVG的范例配置。

.. code-block:: latex
    :linenos:

    \documentclass[tikz, convert, convert={outext=.svg, command=\unexpanded{
    pdf2svg \infile\space \outfile\space all
    }}]{standalone}

其中，

* :code:`tikz`
    此选项告诉 :code:`standalone` LaTex文档中存在 :code:`tikz` 图片。

* :code:`convert`
    此选项开启 :code:`standalone` 的转换功能。

* :code:`convert={}`
    此选项是 :code:`convert` 的详细配置项。

* :code:`outext=.svg`
    设置输出文件的后缀名为“.svg”。更详细的说明请参看 :code:`standalone` 本身的 `说明文档 <http://mirrors.ibiblio.org/CTAN/macros/latex/contrib/standalone/standalone.pdf>`_ 中的表1。

* :code:`command=\unexpanded{}`
    此项是将要调用系统运行的命令。

* :code:`pdf2svg`
    调用的转换工具。

    .. note:: :code:`pdf2svg` 的语法

        :code:`pdf2svg` 的语法可以参看 `这里 <http://www.cityinthesky.co.uk/opensource/pdf2svg/>`_。

        其中，将一多页PDF转换为分页的多个SVG的语法为：

        .. code-block:: bash

            pdf2svg <输入文件名>.pdf <输出文件名>%d.svg all

        注意，尖括号，及其所包裹中的内容需要替换为所需的文件名。

* :code:`\infile`
    输入文件名，包含后缀名。默认后缀名为“.pdf”或“.ps”。 更详细的说明请参看 :code:`standalone` 本身的 `说明文档 <http://mirrors.ibiblio.org/CTAN/macros/latex/contrib/standalone/standalone.pdf>`_ 中的表1。

* :code:`\space`
    空格。若不使用此参数，:code:`\infile` 后不会有空格，无论你实际上键入了多少个。 :code:`\outfile` 也是这样。

* :code:`\outfile`
    输出文件名，包含后缀名。默认后缀名为“.png”。此处已经通过 :code:`outext` 更改为“.svg”。更详细的说明请参看 :code:`standalone` 本身的 `说明文档 <http://mirrors.ibiblio.org/CTAN/macros/latex/contrib/standalone/standalone.pdf>`_ 中的表1。

SVG配置范例中之命令将会被翻译为如下（可以通过查看LOG文件确认）。其中，
:code:`mew_to_svg` 为所用的TEX文件的文件名。

.. code-block:: bash
    :linenos:

    pdf2svg mwe_to_svg.pdf mwe_to_svg-%01d.svg all

由此可以看出，转换的重点，是要把 :code:`convert={}` 中的配置正确设置，以令LaTex将其翻译成正确的系统命令来进行图片的转换。用户可以把多个系统命令整合为一行，以做出丰富多彩的组合来达成不同的目标（在Windows中可以通过“&”或“&&”把多行命令合并为一行）。在 :doc:`workflow` 中将会详细叙述各种图片转换的流程。

.. note:: 运行系统命令

    其实在本小结就可以看出，既然 :code:`standalone` 可以调用以上的命令，那当然也可以调用其它系统命令。理论上，用户可以调用各种命令来做各种事，不仅仅是图片的转换。如果你有兴趣，应该可以做到编译完后自动上传到某个网络位置，或者删除整个硬盘这一类有趣的事情。

编译命令
--------

:code:`standalone` 需要在编译时使用 :code:`-shell-escape` 参数。一个使用 :code:`xelatex` 对 :code:`mew_to_svg.tex` 进行编译的命令如下（用 :code:`xelatex` 是因为需要处理中文）。如果你使用LaTex编辑器进行书写，比如 :code:`TEXsutdio` ，则需要在其中编辑其命令。你也当然可以直接在TEX文件所在之目录下打开CMD，用命令直接编译。

.. code-block:: bash
    :linenos:

    xelatex -synctex=1 -interaction=nonstopmode -shell-escape mwe_to_svg.tex


简例
-----

以下提供一个转换为单页多个SVG的简例。详细的例子会在后文说明。

以下的文件可以在此项目的根目录和 :code:`mew` 文件夹中找到。

**主文件：**

:code:`mew` 文件夹中的 :code:`mwe_to_svg.tex`

.. literalinclude:: ../../mwe/mwe_to_svg.tex
    :linenos:
    :language: latex

**tikz配置文件：**

本教程根目录中的 :code:`configs_tikz.tex`

.. literalinclude:: ../../configs_tikz.tex
    :linenos:
    :language: latex

**color配置文件：**

本教程根目录中的 :code:`configs_colour.tex`

.. literalinclude:: ../../configs_colour.tex
    :linenos:
    :language: latex


.. [#] Ghost In Shell : Standalone Complex
