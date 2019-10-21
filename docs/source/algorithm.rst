脚本详解
==========

本章将对本教程中所用到之脚本进行讲解。

本项目所使用到的脚本存放在 :code:`util` 文件夹之中，它们为：

* :code:`mk_folder.bat`
    用于创建文件夹。

    .. note:: 脚本命名问题

        在Windows当中，如果把批处理脚本命名为所要调用的系统命令名，很可能会导致死循环。 故此命名此脚本为 :code:`mk_folder.bat` 而不是 :code:`mkdir.bat`

* :code:`gs_split_pdf.bat`
    调用 :code:`ghostscript` 把PDF分割为单页。

* :code:`pdf_to_svg.bat`
    把多页PDF转换为分页的SVG。

* :code:`pdf_to_png.bat`
    把多页PDF转换为分页的PNG。

* :code:`pdf_to_emf.bat`
    把PDF转换为EMF（仅一页）。

* :code:`pdf_to_eps.bat`
    把PDF转换为的EPS（仅一页）。

.. warning:: 路径

    在设置 :code:`documentclass` 时，需要注意输入的路径参数。本教程一律使用相对路径。

    :code:`./` 是指当前所在路径。

    :code:`../` 是指往上移一层目录。


:code:`mk_folder.bat` 详解
----------------------------

:code:`mk_folder.bat` 的内容如下：

.. literalinclude:: ../../util/mk_folder.bat
    :language: windows
    :linenos:

此脚本用于在CMD当前所在之目录为根来创建文件夹。如果该文件夹已存在，则不创建而退出。

此脚本接受一个参数。此参数为将要创建的文件夹路径。

此脚本之使用方法如下：

.. code-block:: windows

    mk_folder <要创建之文件夹路径>

此脚本的语法和 :code:`mkdir` 命令的语法一致。此处给出一个例子，假设要在目前的目录下创建一个名为 :code:`a` 的文件夹，其下有一个子目录，名为 :code:`b`，而 :code:`b` 之下又有一个子目录，名为 :code:`c` 。

.. code-block:: windows

    mk_folder a\b\c

若文件夹路径中有空格，则需要把路径放在两个双引号之中，如：

.. code-block:: windows

    mk_folder "a b\c d"


:code:`gs_split_pdf.bat` 详解
-------------------------------

:code:`gs_split_pdf.bat` 的内容如下：

.. literalinclude:: ../../util/gs_split_pdf.bat
    :language: windows
    :linenos:

此脚本用于把输入的PDF分割为单页的PDF。

此脚本接受三个参数。它们如下（按顺序）：

#. 输出的单页PDF的文件夹的路径

#. 输出的单页PDF文件的共用文件名加上“%d”

#. 需要分页的PDF的路径

此脚本调用的是64位的 :code:`ghostscript` ，若你安装的是32位的版本则需要把此脚本中的 :code:`gswin64c` 更改为 :code:`gswin32c` 。

此处给出一个例子，输出的文件夹为 :code:`output` （已存在），共用文件名为 :code:`common`，需要分页的PDF为 :code:`pdf_in` 。

.. code-block:: windows

    gs_split_pdf output common%d.pdf pdf_in.pdf

.. note:: “%d”

    如果不在共用文件名后加上“%d”，:code:`ghostscript` 则不会对PDF进行分页。


:code:`pdf_to_svg.bat` 详解
----------------------------

:code:`pdf_to_svg.bat` 的内容如下：

.. literalinclude:: ../../util/pdf_to_svg.bat
    :language: windows
    :linenos:

此脚本用于把PDF转换为SVG。

此脚本接受两个参数。它们如下（按顺序）：

#. 需要转换的PDF文件路径

#. 输出的单页PDF文件的共用文件名加上“%d”

此脚本调用 :code:`pdf2svg` 来进行文件的转换。此处给出一个例子，需要转换的PDF名为 :code:`pdf_in`，输出的单页PDF的共用文件名为 :code:`pdf_out` ，输出的文件夹为 :code:`out_svg` （已存在）。

.. code-block:: windows

    pdf_to_svg pdf_in.pdf .\out_svg\pdf_out%d.svg

.. note:: “%d”

    如果不在共用文件名后加上“%d”，则只会转换PDF的第一页。


:code:`pdf_to_png.bat` 详解
----------------------------

:code:`pdf_to_png.bat` 的内容如下：

.. literalinclude:: ../../util/pdf_to_png.bat
    :language: windows
    :linenos:

此脚本用于把PDF转换为PNG。此脚本会在CMD当前所在之目录创建PNG文件。

此脚本接受两个参数。它们如下（按顺序）：

#. 转换的PNG的DPI，一般为300或600。过高的DPI会令转换过程冗长。一般而言，打印需要至少300 DPI，一般600 DPI足以应付绝大部分情况。

#. 需要转换的PDF的路径

此脚本调用 :code:`pdftocairo` 来进行文件的转换。此处给出一个例子，转换的DPI为600像素，需要转换的PDF名为 :code:`pdf_in` 。

.. code-block:: windows

    pdf_to_png 600 pdf_in.pdf

.. note:: :code:`pdftocairo`

    :code:`pdftocairo` 会自动把多页PDF转换为单页的PNG，非常方便。


.. note::

    为了方便，用户可以把 :code:`util` 文件夹的路径加入到系统环境变量 :code:`Path` 中，这样就可以直接调用脚本，而不需要在命令中指定 :code:`util` 文件夹的路径。
