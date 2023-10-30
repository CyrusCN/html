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
  cursor.execute()
  
3. From Continuous input Data(Singal from the Audio and video data)

 The troditional method is use ffmpeg to change Continuous Singal

.. code-block:: cpp

  #include <opencv2/opencv.hpp>

.. code-block:: python 
  
  import cv2,numpy,pandas
  import matplotlib.pyplot as pic

4. All in One

.. code-block:: python

  import oracledb,getpass,os
  import json,numpy,pandas
  import matplotlib.pyplot as pic

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
              config_dir="auth/bdc", 
              wallet_location="auth/bdc",
              wallet_password=userpwd
              )

      else:
          connection = oracledb.connect(
              user="Admin",
              password=userpwd,
              dsn="(description= (retry_count=20)(retry_delay=3)(address=(protocol=tcps)(port=1522)(host=adb.ap-tokyo-1.oraclecloud.com))(connect_data=(service_name=g5f10d71d826884_statuscenter_high.adb.oraclecloud.com))(security=(ssl_server_dn_match=yes)))",
              config_dir="auth/sc",
              wallet_location="auth/sc",
              wallet_password=userpwd
              )

      cursor = connection.cursor()
      for data in cursor.execute(input("Please input your sqlcommand:")):
          print(data)
          cursor.close()
  else:
      data=pandas.read_csv("%s" % location):
          print(data)

      #图像绘制
  pic.plot(data)
      #特征编码
      #导出至运算器
    
Data Framework design
`````````````````````

语言与控制装置
..............

批量收集装置
............

传递装置
........

elk套件
redis队列控制

离散数据库与数据融合
....................

反馈语言控制器
..............

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

.. raw:: latex
  
   \vec a

Data Analyes(Statistics)
........................

1. 数据集基本数据预处理(错误值，缺失值)
2. 卡方检验(两个样本群的相似度)
3. 事件发生概率固化(马尔科夫链与K布转移矩阵)



Formule and Code data Characteristic (Mapping)
..............................................

0. 二值化(计算机运算基本特性)
1. 线性规划
2. 连续时间数据频率化与特征化(傅里叶变换)

Factor and Function Design
..........................

优化方法
........

1. ISM方法
2. AHP方法
3. 网络流理论

Machine Learing and Persistence iteration 
`````````````````````````````````````````

Quanta in Finance
-----------------

Quanta in Management
--------------------










