.. LaTex (tikz)转换为图像/LaTex (tikz)转换为图像/LaTex (tikz) to Images documentation master file, created by
   sphinx-quickstart on Thu Oct 17 09:48:07 2019.
   You can adapt this file completely to your liking, but it should at least
   contain the root `toctree` directive.

======================
LaTex (tikz)转换为图像
======================

.. only:: latex

    \newline

此项目是一个关于把LaTex文档直接转换为各种图像的教程（在编译TEX文件时，同时生成单独的图片）。此教程主要关注如何把tikz生成的，内嵌于LaTex生成的PDF文件中的图像转换为各种格式的单独图片。

此项目会讨论到的图片格式如下

* SVG （矢量图）
* PNG（位图）
* EMF （Windows系统上的矢量图）
* EPS （印刷常用格式）

此项目的在于提供基于Windows系统的教程和例子。作者相信Linux用户有能力独自解决这个问题。

此教程会提供软件安装和配置指南，并会结合例子进行讲解。

此教程认为用户已经对LaTex有一定的理解，因而不会对LaTex中之各种进行详解。

本教程将会详尽讲解流程。若只想快速使用而不在乎原理，可先阅读 :doc:`/installation_and_configuration` 然后按照 :doc:`/accelerated_guide` 中之步骤执行即可。

.. toctree::
    :maxdepth: 3
    :numbered:
    :caption: 目录

    system_and_software
    installation_and_configuration
    accelerated_guide
    config_standalone
    workflow
    algorithm
    in_one_go
    conclusion
