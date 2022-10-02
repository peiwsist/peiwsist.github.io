## 安装Ubuntu和ndnSIM遇到的问题

### <mark>安装好Ubuntu后，无法复制粘贴</mark>

  - 先去装`Vmstation tools`，安装过程中会遇到的问题。需要在虚拟机中设置一下
  - 但仍然无法复制粘贴 参考[虚拟机安装好了VMtools了,但是还是不能实现文件拖拽和复制功能？(zhihu.com)](https://www.zhihu.com/question/41586989)
  - **埋坑**_办法是 先`vmware-uninstall-tools.pl`把你安装的不能运行的`vmtools`卸载了.然后 `apt-get install open-vm-tools-desktop`。 `reboot`。then ok

### <mark>Ubuntu字体大小更改</mark>

  - **[如何调整Ubuntu的字体大小？](https://blog.csdn.net/dghcs18/article/details/104420127)**

- `Ubuntu`更改源

### <mark>安装ndnSIM后，无法可视化。</mark>

  - **[ndnSIM安装教程](https://blog.csdn.net/GregoryHanson/article/details/83036964)**

  - 在尝试了网上所有办法后，仍是不行。以下是尝试仍然不行的：

  <img src="https://img-blog.csdnimg.cn/20200316154116957.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3dlaXhpbl80Mzk3NDQxMw==,size_16,color_FFFFFF,t_70" alt="可以看到ndnSIM是enabled的" style="zoom: 50%;" />

  **可以看到图中的Python Binding 和PyViz visualizer都是 not enabled**

  - **[ndnSIM中可视化的解决办法-CSDN博客](https://blog.csdn.net/xiaoxin990214/article/details/70157263)**
  - **[ndnSIM 2.0 因缺少pythonbind无法使用visual组件问题 —pybindgen (found '') ".. ns3::VisualSimulatorImpl not found"](https://blog.csdn.net/neuwyt/article/details/52242853)**
  - **[执行 sudo ./waf --run second --vis 出现错误：VisualSimulatorImpl not found-CSDN博客](https://blog.csdn.net/sinat_36418396/article/details/106569512)**

  原因在于python依赖的安装包没有安装。

  ### **python Binding解决**

    - 安装python3

    - ```bash
      sudo apt-get install python3-pip
      pip3 install pybindgen
      ```

    - **[Python报错解决Command 'pip' not found, but there are 18 similar ones.](https://www.lipsuper.com/index.php/2020/10/13/python-pit/)**

    - **[ns-3学习手记10_ns3.29中PyViz visualizer没有enabled，进行安装.](https://blog.csdn.net/qq_31648921/article/details/112404288)**

    - **[ubuntu18下 ndnSIM安装过程详解。](https://blog.csdn.net/weixin_43974413/article/details/104899594)**

  ###  **PyViz visualizer解决**

    - ```pyhton
      sudo apt-get install python-dev python-pygraphviz python-kiwi python-pygoocanvas python-gnome2 gir1.2-goocanvas-2.0 python-rsvg
      ```

    - **[在NS-3中安装可视化工具pyviz的一些问题的解决](https://blog.csdn.net/qq_31676673/article/details/88107454)**

    - **[ndnSIM仿真平台使用之安装](https://www.dazhuanlan.com/chenalonso/topics/1556322)**

    - 可以再把与python有关的再装一遍

    - ![可以看到ndnSIM是enabled的](https://img-blog.csdnimg.cn/20200316154116957.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3dlaXhpbl80Mzk3NDQxMw==,size_16,color_FFFFFF,t_70)

    - 出现以下图片后

    - ```shell
      ./waf
      ```

    - 进行编译，但会出现卡了，这时需要增大虚拟机内存

    - 重新编译，终于安装好了

### 其他参考网站

- [NS3快速入门（使用VScode查看、编译代码）](https://blog.csdn.net/weixin_43314519/article/details/106531060)

- [NS3 入门环境搭建（VM虚拟机+Ubuntu，常见错误解析）](https://blog.csdn.net/weixin_43314519/article/details/106504008)

- [使用vscode开发ns3项目（代码高亮、自动补全支持）](https://blog.csdn.net/fwhdzh/article/details/106292166)

- [vscode运行ns-3 - 国内版 Bing](https://cn.bing.com/search?q=vscode运行ns-3&form=ANNTH1&refig=062a1e9b111042da825ae882e17b4c22)

