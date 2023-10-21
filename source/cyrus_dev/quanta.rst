Quanta Devlop and Systems Engineering
=====================================
在量化过程中，我个人认为，有必要掌握三种技能

1. 业务数据的运筹编码(数据挖掘与统计学)

2. 业务数据流的架构设计(系统设计与反馈控制)

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

.. code-block:: cpp

  #include <opencv2/opencv.hpp>

.. code-block:: python 
  
  import cv2,numpy,pandas
  import matplotlib.pyplot as pic

Math Basic 
``````````
Advanced Mathematics(Not important for Discontinuous data)
..........................................................

Linear Algebra for The data 
...........................

Data Analyes(Statistics)
........................

1. 数据集基本数据预处理(错误值，缺失值)
2. 卡方检验(两个样本群的相似度)
3. 连续时间数据频率化特(傅里叶变换)
4. 事件发生概率化(马尔科夫链与K布转移矩阵)

Formule and Code data Characteristic (Mapping)
..............................................

1. 线性规划

Factor and Function Design
..........................

Framework design()
``````````````````







