Quanta Devlop and Systems Engineering
=====================================
在量化过程中，我个人认为，有必要掌握三种主要技能

1. 业务数据的运筹编码(数据挖掘与统计学)

2. 业务数据流的架构设计(系统架构设计与反馈控制)

3. 业务数据在传递过程中的再优化(离散数学)

Learn tree
----------

The data Collector
``````````````````

Data Collector
......................
No metter whatever data you want to input, They will end to insert your runing path(namespace), 
these data will Mapping in runing enviroment.

1. From the Local document(csv json)

.. code-block:: python
  
  import json,numpy,pandas
  import matplotlib.pyplot as pic
  path = input("please input your doc path")
  data = pandas.read_csv("%s" % path)
  print(data)

2. From the Stream(Network Stream(object stroge) or read the database.)

.. code-block:: python

  import oracledb,getpass,os
  import pandas,numpy
  import matplotlib.pyplot as pic
  userpwd= getpass.getpass()
  connection = oracledb.connect(
    user="admin",
    password=userpwd,
    dsn="(description= (retry_count=20)(retry_delay=3)(address=(protocol=tcps)(port=1522)(host=adb.ap-tokyo-1.oraclecloud.com))(connect_data=(service_name=g5f10d71d826884_bigdatacenter_high.adb.oraclecloud.com))(security=(ssl_server_dn_match=yes)))",
    config_dir="auth/bdc", 
    wallet_location="auth/bdc",
    wallet_password=userpwd
    )
  cursor = connection.cursor()
  for data in cursor.execute(input("Please input your sqlcommand:")):
      print(data,type(data))
  cursor.close()
  
3. From Continuous input Data(Singal from the Audio and video data)

 The troditional method is use ffmpeg to change Continuous Singal

.. code-block:: cpp

  #include <opencv2/opencv.hpp>

.. code-block:: python 
  
  import cv2,numpy,pandas,ffmpeg


4. All in One

.. code-block:: python

  import oracledb,json,cv2,ffmpeg
  import getpass,os
  import pandas as pd

  #data.py
  video = input('Please add your videopath:')
  if video =="":
      location = input("Please add your doc Location:")
      if location =="":
              #从云中读取数据
          userpwd= getpass.getpass()
          method=input("Please input data method:")
          if method !="json":
              connection = oracledb.connect(
                  user="Admin",
                  password=userpwd,
                  dsn="(description= (retry_count=20)(retry_delay=3)(address=(protocol=tcps)(port=1522)(host=adb.ap-tokyo-1.oraclecloud.com))(connect_data=(service_name=g5f10d71d826884_bigdatacenter_high.adb.oraclecloud.com))(security=(ssl_server_dn_match=yes)))",
                  config_dir="~/auth/bdc", 
                  wallet_location="~/auth/bdc",
                  wallet_password=userpwd
                  )
          else:
              connection = oracledb.connect(
                  user="Admin",
                  password=userpwd,
                  dsn="(description= (retry_count=20)(retry_delay=3)(address=(protocol=tcps)(port=1522)(host=adb.ap-tokyo-1.oraclecloud.com))(connect_data=(service_name=g5f10d71d826884_statuscenter_high.adb.oraclecloud.com))(security=(ssl_server_dn_match=yes)))",
                  config_dir="~/auth/sc",
                  wallet_location="~/auth/sc",
                  wallet_password=userpwd
                  )
          cursor = connection.cursor()
          for data in cursor.execute(input("Please input your sqlcommand:")):
              print(data,type(data))
          cursor.close()

      else:
          data=pd.read_csv("%s" % location)
          print(data,type(data))
  else:
      data = ffmpeg.input('')

绘图与向量操作
..............

1. 默认空间二维

.. code-block:: python

  #pic.py
  from data import data
  import matplotlib.pyplot as plt
  import numpy as np

  pre3 = data.head(3)
  #自动绘图
  pic = pre3.plot()
  pic.figure.savefig('pic.png')
  #以下为手动自定义自变量和因变量展现方式
  print(pre3,type(pre3))
  x1 = pre.loc[:,'Moderate Positive Skew']
  x2 = pre.loc[:,'Highly Positive Skew']
  x3 = pre.loc[:,'Highly Negative Skew']
  x4 = pre.loc[:,:]
  
  fig1.figure.savefig('fig.png',)


2. 空间三维

.. code-block:: python

  from data import data
  import matplotlib.pyplot as plt
  import numpy as np
  from mpl_toolkits.mplot3d import Axes3D

  pre = data.head(
      int(input("Please input your Sample N="))
  )
  print(pre,type(pre))
  x1 = pre.loc[:,'Moderate Positive Skew']
  x2 = pre.loc[:,'Highly Positive Skew']
  x3 = pre.loc[:,'Highly Negative Skew']

  pltf = plt.figure(
  )
  fig1 = pltf.add_subplot(projection='3d').scatter(xs=x1,ys=x2,zs=x3,s=30,c="y",marker=".")
  fig1.figure.savefig('fig1.png',)


批量收集装置
............

Redis+pa.py+Node
Spark
ElasticSearch

传递装置
........

elk套件
sockets通讯（Golang+json）

离散数据库与数据融合
....................

1. 数据中心
2. 边缘数据节点
3. 去重与叠加

Data and Software Framework design
```````````````````````````````````

人类决策行为与骨架架构设计
..........................

1. ISM方法
2. AHP方法
3. 决策树
4. 网络流理论

Factor and Function Design
..........................

语言与控制装置与反馈语言控制器
..............................

.. code-block:: Bash

  ├── oracledb
  │   ├── controller
  │   │   ├── compute
  │   │   │   ├── collector
  │   │   │   │   ├── 2pic.py
  │   │   │   │   ├── 3pic.py
  │   │   │   │   ├── fig1.png
  │   │   │   │   └── predata
  │   │   │   │       ├── data.csv
  │   │   │   │       ├── data.json
  │   │   │   │       ├── data.py
  │   │   │   │       ├── data.sql
  │   │   │   │       ├── pa.py
  │   │   │   │       └── sockets.go
  │   │   │   ├── compare.py
  │   │   │   ├── quantacompute.py
  │   │   │   └── status.py
  │   │   ├── controller.c
  │   │   ├── controller.cpp
  │   │   └── controller.py
  │   └── otherpredata
  │       ├── 1predocode
  │       │   └── data
  │       │       ├── Data_to_Transform.csv

1. C机器控制与优化
2. C++面向对象的程序控制
3. Go网络接口编程
4. Python&Rust脚本控制与数据分析
5. Other Contorler（Automate,esp8266,Machine Language）

Math Basic 
``````````
Advanced Mathematics(Not important for Discontinuous data)
..........................................................
0. 自变量与因变量
1. 级数
2. 函数与连续性
3. 域
4. 空间与距离
5. 积分
6. 物理意义

Linear Algebra for The data 
...........................
1. 线性规划与单纯型法

.. math::
  
  目标函数
  Z=k_1x_1+k_2x_2+...+k_nx_n

.. math::

  约束条件
  \begin{cases}
  a_{11}x_1+a_{12}x_2+...+a_{1n}x_n=b_1\\
  a_{21}x_1+a_{22}x_2+...+a_{2n}x_n=b_2\\
  ...\\
  a_{m1}x_1+a_{m2}x_2+...+a_{mn}x_n=b_m\\
  \end{cases}



.. math::

  目标函数
  Z=\sum_{j=1}^{n}k_jx_j=\vec{k}\vec{x}\\

一般问题不会涉及动态目标函数，k通常为定值，动态决策中可能会涉及，k之间的比值决定目标斜率，x决定目标维度（二维中是线目标，三维是面目标，四维体目标，高维无法具象）


.. math:: 

  约束条件
  \begin{cases}
  a_{1j}\sum_{j=1}^{n}x_j&=a_{1\vec{n}}\vec{x}&=b_1\\
  a_{2j}\sum_{j=1}^{n}x_j&=a_{2\vec{n}}\vec{x}&=b_2\\
  ...\\
  a_{mj}\sum_{j=1}^{n}x_j&=a_{m\vec{n}}\vec{x}&=b_2\\
  \end{cases}\\

.. math::
  
  \rightarrow
  \sum_{i=1}^{m}a_{i\vec{n}}\vec{x}&=b_i\\
  \rightarrow
  a_{\vec{i}\vec{n}}\vec{x}&=b_{\vec{i}}\\
  \rightarrow
  \vec{a}\vec{x}&=\vec{b}

a作为约束变量x的系数,b之前的符号通常为不等号，代表该函数一侧的空间。

由目标函数和约束条件的公式可以看出，

.. math:: 
  
  \vec{x} 决定了规划维度,问题变为求共同解集并筛选
  \max\limits_{\vec{x}}
  \begin{cases}
  \vec{a}\vec{x}=\vec{b}\\
  \vec{k}\vec{x}=f(\vec{x})\\
  \end{cases}
  or
  \min\limits_{\vec{x}}
  \begin{cases}
  \vec{a}\vec{x}=\vec{b}\\
  \vec{k}\vec{x}=f(\vec{x})\\
  \end{cases}

Data Analyes(Statistics)
........................

0. 正态分布特征
1. 数据集基本数据预处理(错误值，缺失值)
2. 卡方检验(两个样本群的相似度)
3. 事件发生概率固化(马尔科夫链与K布转移矩阵)
4. 连续时间数据频率化与特征化(傅里叶变换)
5. 范数与调参


Formule and Code data Characteristic (Mapping)
..............................................

0. 二元关系并二值化(计算机运算基本特性，越含有二元关系运算越快)
1. 映射到内存空间（环境变量）


Machine Learing and Persistence iteration 
`````````````````````````````````````````
0. 凹凸函数
1. 损失函数
2. 参量引入
3. 反馈
4. 调参与凸优化
5. 持续优化与持续参量引入迭代


QuantaCompute
--------------

.. code-block:: python

  from quafu import User
  user = User()
  user.save_apitoken("####")

  import numpy as np
  from quafu import QuantumCircuit

  q = QuantumCircuit(5)


量子运算逻辑门设计
```````````````````

量子数学映射与运算逻辑
``````````````````````

量子机器学习与持续迭代
```````````````````````

Quanta in Industry
------------------

Quanta in Finance
-----------------

Quanta in Management
--------------------

Singal,Biological and Filter
----------------------------

Data Science and ICML、ACL、KDD in Different Domain
---------------------------------------------------


















