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

.. code-block::python
    import oracledb,getpass,os
    import json,numpy,pandas
    #import data
    data = pandas.read_csv("data/predocode/data/Data_to_Transform.csv")
    print (dat1a)
    #select data 
    #format data
    #upload to cloud
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
    cursor.execute(
    input()
    )   
  #use in cloud
  #do as json
  #sava as document

Math Basic 
``````````


Code and Formule data (Mapping)
...............................

Factor and Function Design
..........................

Linear Algebra for The data 
...........................







