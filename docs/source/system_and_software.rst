.. _software :

系统和软件
===========

此项目会用到如下的系统和软件，请先保证你已安装了它们。

* Windows 7或Windows 10
* `texlive（2019年的发布，免费） <https://www.tug.org/texlive/acquire-netinstall.html>`_
* LaTex的 :code:`standalone` 包（ :code:`texlive` 自带）
*  :code:`pdftocairo` （ :code:`texlive` 自带，用于PNG转换）
* `pdf2svg（Windows编译版，免费。用于SVG转换） <https://github.com/jalios/pdf2svg-windows>`_
* `inksacpe（0.92.4，免费。用于EMF和EPS的转换） <https://inkscape.org/release/inkscape-0.92.4/>`_
* `ghostscript (9.50，免费。用于PDF文件的分页) <https://github.com/ArtifexSoftware/ghostpdl-downloads/releases>`_


转换软件的使用理由
------------------

此项目选择的转换软件主要基于以下理由。

* 此项目坚持所有使用的转换软件必须为免费

* 转换结果必须是一页PDF一张图

* 当把PDF转换为矢量图时，必须为真正的矢量图，而不是包裹在矢量格式中的位图

    * 因此，此项目不使用ImageMagick，因其在转换矢量图时经常栅格化

* 当转为为矢量图时，字体应该嵌入而不是栅格化

* 转换命令应尽可能简单

* 使用的软件尽可能少以降低依赖性

.. note::

    尽管 :code:`inkscape` 也可以进行PNG和SVG的转换，但 :code:`pdftocairo` 和 :code:`pdf2svg` 自带了多页到单页的功能，使用便利，而且安装也简易，故而用此二软件分别进行PNG和SVG的转换而不使用 :code:`inkscape` 。若使用 :code:`inkscape` ，则需要先调用 :code:`ghostscript` 对PDF进行分页，然后再转换。
