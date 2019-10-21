极简教程
==========

本章意在提供最简短而必要的步骤，以使用户快速上手。

在应用本章步骤前，请先保证所有需要的软件和配置已完成。


转换为SVG
--------------

#. 把本教程附带的 :code:`util` 文件夹复制到需要转换的TEX文件所在之目录下。

#. 对需要转换的TEX的文件的 :code:`documentclass` 进行如下配置：

    .. literalinclude:: ../../demo_to_svg.tex
        :language: latex
        :lines: 4-11
        :linenos:

#. 使用 :code:`-shell-escape` 参数对TEX文件进行编译。例如（需要把尖括号，及其所包裹的内容更换成你的TEX文件的文件名）：

    .. code-block:: bash

        xelatex -synctex=1 -interaction=nonstopmode -shell-escape <你TEX文件的文件名>.tex

#. 转换好的SVG文件将存放在 :code:`out_svg` 文件夹下。


转换为PNG
--------------

#. 把本教程附带的 :code:`util` 文件夹复制到需要转换的TEX文件所在之目录下。

#. 对需要转换的TEX的文件的 :code:`documentclass` 进行如下配置：

    .. literalinclude:: ../../demo_to_png.tex
        :language: latex
        :lines: 4-11
        :linenos:


#. 使用 :code:`-shell-escape` 参数对TEX文件进行编译。例如（需要把尖括号，及其所包裹的内容更换成你的TEX文件的文件名）：

    .. code-block:: bash

        xelatex -synctex=1 -interaction=nonstopmode -shell-escape <你TEX文件的文件名>.tex

#. 转换好的PNG文件将存放在 :code:`out_png` 文件夹下。


转换为EMF
--------------

#. 把本教程附带的 :code:`util` 文件夹复制到需要转换的TEX文件所在之目录下。

#. 对需要转换的TEX的文件的 :code:`documentclass` 进行如下配置：

    .. literalinclude:: ../../demo_to_emf.tex
        :language: latex
        :lines: 4-24
        :linenos:

#. 使用 :code:`-shell-escape` 参数对TEX文件进行编译。例如（需要把尖括号，及其所包裹的内容更换成你的TEX文件的文件名）：

    .. code-block:: bash

        xelatex -synctex=1 -interaction=nonstopmode -shell-escape <你TEX文件的文件名>.tex

#. 转换好的EMF文件将存放在 :code:`out_emf` 文件夹下。


转换为EPS
--------------

#. 把本教程附带的 :code:`util` 文件夹复制到需要转换的TEX文件所在之目录下。

#. 对需要转换的TEX的文件的 :code:`documentclass` 进行如下配置：

    .. literalinclude:: ../../demo_to_eps.tex
        :language: latex
        :lines: 4-25
        :linenos:

#. 使用 :code:`-shell-escape` 参数对TEX文件进行编译。例如（需要把尖括号，及其所包裹的内容更换成你的TEX文件的文件名）：

    .. code-block:: bash

        xelatex -synctex=1 -interaction=nonstopmode -shell-escape <你TEX文件的文件名>.tex

#. 转换好的EPS文件将存放在 :code:`out_eps` 文件夹下。


本章中为了方便排错，命令是分部进行的（通过 :code:`&&` 连成一行）。这些命令其实是可以放在同一个脚本中，而简化 :code:`documentclass` 的设置的。详情请看 :doc:`in_one_go` 。
