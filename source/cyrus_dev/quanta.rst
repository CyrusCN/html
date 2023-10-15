Quanta Devlop 
=============
在量化过程中，我个人认为，有必要掌握三种技能

1.业务数据的运筹编码

2.业务数据流的架构设计

3.业务数据在数据挖掘中的常用分析手短

Learn tree
----------

The data Collector
``````````````````

Python data Collector
.....................


.. code-block:: python

  import oracledb,getpass,os
  import json,numpy,pandas
  import matplotlib.pyplot as pic
  
  ##########引入数据##########
  print("Please add your doc Location")
  location = input()
  data = pandas.read_csv("%s" % location)
  print(data)
  ##########引入数据##########
  
  ##########图像绘制##########
  #pic.plot(data)
  ##########图像绘制##########
  
  ##########格式数据##########
  
  ##########格式数据##########
  
  ##########连数据库##########
  userpwd= getpass.getpass()
  connection = oracledb.connect(
      user="admin",
      password=userpwd,
      dsn="(description= (retry_count=20)(retry_delay=3)(address=(protocol=tcps)(port=1522)(host=adb.ap-tokyo-1.oraclecloud.com))(connect_data=(service_name=g5f10d71d826884_bigdatacenter_high.adb.oraclecloud.com))(security=(ssl_server_dn_match=yes)))",
      config_dir="auth/bdc", 
      wallet_location="auth/bdc",
      wallet_password=userpwd
      )
  ##########连数据库##########
  
  
  ##########筛选字符##########
  ##########筛选字符##########
  
  ##########分割字符##########
  ##########分割字符##########
  
  ##########连接指针##########
  cursor = connection.cursor()
  ##########连接指针##########
  
  ##########执行指令##########
  # cursor.execute(
  #    input()
  # )
  ##########执行指令##########
  
  
  #从云中读取数据
  #cursor.execute()
  
  
  #生成json格式
  #导出至运算文件夹

Math Basic 
``````````


Code and Formule data (Mapping)
...............................

Factor and Function Design
..........................

Linear Algebra for The data 
...........................







