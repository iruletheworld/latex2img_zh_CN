一步到位
==========

本章在 :doc:`algorithm` 的基础上，讲解怎样把命令合并到一个脚本中从而简化 :code:`documentclass` 的配置。

从 :doc:`algorithm` 中可以看出，本教程为了方便排错，而把命令分到多个脚本之中，逐个击破，但其实完全是可以把命令全部写入单个脚本之中，而实现简化 :code:`documentclass` 的设置的。

本章将会提供这么做的范例。


一步转换成SVG
--------------

本小结将使用 :code:`util` 文件夹中之 :code:`qk_pdf_to_svg.bat` 脚本，以 :code:`mwe` 文件夹中的 :code:`qk_to_svg.tex` 为例，展示如何一步转换到SVG。

:code:`qk_to_svg.tex` 中的 :code:`documentclass` 的配置如下：

.. literalinclude:: ../../mwe/qk_to_svg.tex
    :language: latex
    :lines: 1-6
    :linenos:

其中， :code:`out_svg` 是存放SVG的文件夹。

:code:`qk_pdf_svg.bat` 脚本的内容如下：

.. literalinclude:: ../../util/qk_pdf_to_svg.bat
    :language: windows
    :linenos:

:code:`qk_pdf_to_svg.bat` 中的命令，是把 :code:`demo_to_svg.tex` 中的 :code:`documentclass` 中的命令整合为一，以达到简化 :code:`documentclass` 的配置的目的。


一步转换成PNG
--------------

本小结将使用 :code:`util` 文件夹中之 :code:`qk_pdf_to_png.bat` 脚本，以 :code:`mwe` 文件夹中的 :code:`qk_to_png.tex` 为例，展示如何一步转换到PNG 。

:code:`qk_to_png.tex` 中的 :code:`documentclass` 的配置如下：

.. literalinclude:: ../../mwe/qk_to_png.tex
    :language: latex
    :lines: 1-6
    :linenos:

其中， :code:`out_png` 是存放PNG的文件夹。

:code:`qk_pdf_to_png.bat` 脚本的内容如下：

.. literalinclude:: ../../util/qk_pdf_to_png.bat
    :language: windows
    :linenos:

:code:`qk_pdf_to_png.bat` 中的命令，是把 :code:`demo_to_png.tex` 中的 :code:`documentclass` 中的命令整合为一，以达到简化 :code:`documentclass` 的配置的目的。


一步转换成EMF
--------------

本小结将使用 :code:`util` 文件夹中之 :code:`qk_pdf_to_emf.bat` 脚本，以 :code:`mwe` 文件夹中的 :code:`qk_to_emf.tex` 为例，展示如何一步转换到EMF。

:code:`qk_to_emf.tex` 中的 :code:`documentclass` 的配置如下：

.. literalinclude:: ../../mwe/qk_to_emf.tex
    :language: latex
    :lines: 1-7
    :linenos:

其中， :code:`out_emf` 是存放EMF的文件夹。

:code:`qk_pdf_to_emf.bat` 脚本的内容如下：

.. literalinclude:: ../../util/qk_pdf_to_emf.bat
    :language: windows
    :linenos:

:code:`qk_pdf_to_emf.bat` 中的命令，是把 :code:`demo_to_emf.tex` 中的 :code:`documentclass` 中的命令整合为一，以达到简化 :code:`documentclass` 的配置的目的。


一步转换成EPS
--------------

本小结将使用 :code:`util` 文件夹中之 :code:`qk_pdf_to_eps.bat` 脚本，以 :code:`mwe` 文件夹中的 :code:`qk_to_eps.tex` 为例，展示如何一步转换到EPS。

:code:`qk_to_eps.tex` 中的 :code:`documentclass` 的配置如下：

.. literalinclude:: ../../mwe/qk_to_eps.tex
    :language: latex
    :lines: 1-7
    :linenos:

其中， :code:`out_eps` 是存放EPS的文件夹。

:code:`qk_pdf_to_eps.bat` 脚本的内容如下：

.. literalinclude:: ../../util/qk_pdf_to_eps.bat
    :language: windows
    :linenos:

:code:`qk_pdf_to_eps.bat` 中的命令，是把 :code:`demo_to_eps.tex` 中的 :code:`documentclass` 中的命令整合为一，以达到简化 :code:`documentclass` 的配置的目的。
