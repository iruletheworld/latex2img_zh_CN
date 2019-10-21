转换流程
==========

本章将对转换流程进行讲解。鉴于使用到之软件，转换成PNG的流程与转换成SVG之流程相近，而转换成EPS之流程则于转换成EMF之流程同理。

本教程中转换的流程将利用到数份Windows的批处理脚本（在本教程的 :code:`util` 文件夹中），本教程将在 :doc:`algorithm` 中对它们进行详细讲解。

本章中之方法一律需要使用 :code:`-shell-escape` 参数来进行编译。一个使用 :code:`xelatex` 对 :code:`mew_to_svg.tex` 进行编译的命令如下（用 :code:`xelatex` 是因为需要处理中文）。

.. code-block:: bash
    :linenos:

    xelatex -synctex=1 -interaction=nonstopmode -shell-escape mwe_to_svg.tex

请把 :code:`mwe_to_svg` 替换为你的TEX文件文件名。


转换为SVG之流程
-----------------

转换为SVG之流程可用如下之流程图表示：

.. only:: html

    .. thumbnail:: ./_images/workflow_pics-1.svg
        :group: group1
        :align: center
        :alt: SVG flowchart

.. only:: latex

    .. figure:: ./_images/workflow_pics-1.png
        :align: center
        :alt: SVG flowchart

如上图所示，转换流程将在所在之目录创建一个名为 :code:`out_svg` 的文件夹单独存放生成的SVG文件。之后将会调用 :code:`util` 文件夹中的 :code:`pdf_to_svg` 脚本来实现转换。

此流程需要用户对需要转换之TEX文件的 :code:`documentclass` 进行如下配置：

.. literalinclude:: ../../demo_to_svg.tex
    :language: latex
    :lines: 4-11
    :linenos:

.. note:: 设置 :code:`outext`

    当 :code:`outext` 有设置时， :code:`standalone` 会自动地在输出文件（即是 :code:`outfile`）的文件名（不含后缀名）后加上计数关键字（一般是 :code:`%d`）。

    这小节的方法正是利用 :code:`standalone` 之此特性，结合 :code:`pdf2svg` 的语法来进行PDF转换为分页的SVG。

.. warning:: 关于“%”和“\\”符号

    在LaTex中，“%”是一个保留字，用来表示注释。如果直接使用在 :code:`documentclass` 之中，则会把其后面的同行代码全部注释掉。这样的话，编译时会出问题。

    然而，若用 “\\” 进行转义（即“escape”）的话 :code:`standalone` 是会把“\\”符号作为明文加入到命令中的。这样一来，命令通常都不对，因为“\\”在LaTex中是表示的是后面跟的是参数或者命令。而在Windows命令中“%”通常用来指代参数，在Windows中使用for循环时绝对会用到它，无法避免。

    综上所述，如果在 :code:`documentclass` 里面直接把系统命令写全的话，很难保证其正确性。

    故此，作者选择把命令封装到多个批处理脚本中，这样就可以避免以上提及的符号问题同时方便排错。

本方法用到以下两份脚本：

#. :code:`mk_folder`
    创建文件夹。

#. :code:`pdf_to_svg`
    将多页的PDF转换为分页的SVG。

它们的详细讲解在 :doc:`algorithm` 中。


转换为PNG之流程
-----------------

转换为PNG之流程可用如下之流程图表示：

.. only:: html

    .. thumbnail:: ./_images/workflow_pics-2.svg
        :group: group1
        :align: center
        :alt: PNG flowchart

.. only:: latex

    .. figure:: ./_images/workflow_pics-2.png
        :align: center
        :alt: PNG flowchart

如上图所示，转换流程将在所在之目录创建一个名为 :code:`out_png` 的文件夹单独存放生成的PNG文件。之后将会调用 :code:`util` 文件夹中的 :code:`pdf_to_png` 脚本来实现转换。

此流程需要用户对需要转换之TEX文件的 :code:`documentclass` 进行如下配置：

.. literalinclude:: ../../demo_to_png.tex
    :language: latex
    :lines: 4-11
    :linenos:

.. note:: :code:`pdftocairo`

    :code:`pdftocairo` 会自动地把一多页的PDF自动分割为多张PNG。故此只需要把输入文件给它即可（即 :code:`infile`），而不需要设置输出文件（即 :code:`outfile`）。

本方法用到以下两份脚本：

#. :code:`mk_folder`
    创建文件夹。

#. :code:`pdf_to_png`
    将多页的PDF转换为分页的PNG。

它们的详细讲解在 :doc:`algorithm` 中。


转换为EMF之流程
-----------------

转换为EMF之流程可用如下之流程图表示：

.. only:: html

    .. thumbnail:: ./_images/workflow_pics-4.svg
        :group: group1
        :align: center
        :alt: EMF flowchart

.. only:: latex

    .. figure:: ./_images/workflow_pics-4.png
        :align: center
        :alt: EMF flowchart

如上图所示，转换流程将在所在之目录创建一个名为 :code:`out_emf` 的文件夹单独存放生成的EMF文件。之后将会调用 :code:`util` 文件夹中的 :code:`gs_split_pdf` 来对生成的PDF进行分页，:code:`pdf_to_emf` 脚本来实现转换。 转换完毕后会删除所有单页之PDF，只保留EMF。

此流程需要用户对需要转换之TEX文件的 :code:`documentclass` 进行如下配置：

.. literalinclude:: ../../demo_to_emf.tex
    :language: latex
    :lines: 4-24
    :linenos:

.. note:: :code:`inkscape`

    :code:`inkscape` 在转换时不会自动对PDF进行分页。若直接使用 :code:`inkscape` 对多页PDF进行转换，只有第一页会被转换。

    故此，本方法会先调用 :code:`ghostscript` 对PDF进行分页，然后在调用 :code:`inkscape` 对所有的单页PDF进行转换。

本方法用到以下三份脚本：

#. :code:`mk_folder`
    创建文件夹。

#. :code:`gs_split_pdf`
    将多页的PDF分割为单页的PDF。

#. :code:`pdf_to_emf`
    将PDF转换为EMF（仅一页）。

它们的详细讲解在 :doc:`algorithm` 中。


转换为EPS之流程
-----------------

转换为EPS之流程可用如下之流程图表示：

.. only:: html

    .. thumbnail:: ./_images/workflow_pics-3.svg
        :group: group1
        :align: center
        :alt: EPS flowchart

.. only:: latex

    .. figure:: ./_images/workflow_pics-3.png
        :align: center
        :alt: EPS flowchart

如上图所示，转换流程将在所在之目录创建一个名为 :code:`out_eps` 的文件夹单独存放生成的EMF文件。之后将会调用 :code:`util` 文件夹中的 :code:`gs_split_pdf` 来对生成的PDF进行分页，:code:`pdf_to_eps` 脚本来实现转换。 转换完毕后会删除所有单页之PDF，只保留EMF。

此流程需要用户对需要转换之TEX文件的 :code:`documentclass` 进行如下配置：

.. literalinclude:: ../../demo_to_eps.tex
    :language: latex
    :lines: 4-25
    :linenos:

本方法之原理于转换为EMF的流程完全一样。都是先对生成的PDF进行分页，再调用 :code:`inkscape` 进行处理。

本方法用到以下三份脚本：

#. :code:`mk_folder`
    创建文件夹。

#. :code:`gs_split_pdf`
    将多页的PDF分割为单页的PDF。

#. :code:`pdf_to_eps`
    将PDF转换为EPS（仅一页）。


它们的详细讲解在 :doc:`algorithm` 中。
