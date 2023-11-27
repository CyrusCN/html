Tools Learn
===========

Docker
------
Docker can be seen a mini-vitural-system, its img like some system.iso and use the img to be a finished application(container) level.

Docker use Example
``````````````````
At the beginning, you should take something into consideration such as the io between local and container.

Some way to set up docker application.

1. docker composer(apt install/yum)  

.. code-block:: yaml

  version: '3'
  #volumes:
  #easy to remember:
  services: 
    app:
      container_name: name
      image: image name
      restart: always
    ports:
    - 8080:8080
    - 1935:1935
    - 1985:1985
    networks: 
    - networkname
    deploy:
      resources:
        limits:
          cpus: "0.5"
          memory: 500M
        reservations:
          memory: 200M
          
  networks:
    networkname:
      driver: bridge
  
2. Makefile 

Create a Makefile in (~/dockerauto) and easy to excute command →make run

.. code-block:: Makefile
  
  ImgName := nginx
  LocalLoc := ~/html/build/html
  port := 80
  ssl := 443
  ContainerLoc := /usr/share/nginx/html
  ngst := /etc/nginx
  ngstlc := ~/dockerauto/conf
  build:
  	docker build -t $(ImgName) .
  run:
  	docker run -it -d -v $(ngstlc):$(ngst) -p $(port):$(port) -p $(ssl):$(ssl) -v $(LocalLoc):$(ContainerLoc) $(ImgName)
  status:
  	docker ps -a
  stop:
  	docker stop container $(ImgName)
  shell:
  	docker run -it $(ImgName) /bin/bash
  rm:
  	docker rm $(ImgName)

3. Bash command(Just convert the $)

.. code-block:: shell

  docker run -it -d -v $(ngstlc):$(ngst) -p $(port):$(port) -p $(ssl):$(ssl) -v $(LocalLoc):$(ContainerLoc) $(ImgName) 

.. _my-reference-label:

NGINX web Sphinx With SSL
.........................
NGINX is a tool listen your local services and make your services can be seen at some port and transmit your data as the http or secure https, so when you change the nginx config, there are some ssl(Secure Sockets Layer,Public and Private Key) conf no metter who supply, neither offcial or yourself.
Here are some step.

1. From the Makefile to make run a nginx docker container

.. code-block:: bash

  ubuntu@VM-0-17-ubuntu:~/dockerauto$ cd ~/dockerauto
  ubuntu@VM-0-17-ubuntu:~/dockerauto$ make run
  docker run -it -d -v ~/dockerauto/conf:/etc/nginx -p 80:80 -p 443:443 -v ~/html/build/html:/usr/share/nginx/html nginx
  6e6b2c4fbcc53c606e4aa19dd993e397991ff7975554df667d7cd0f895157313

2. Change the nginx config file(in local path but Mapping in docker container)

.. code-block:: bash

  ubuntu@VM-0-17-ubuntu:~/dockerauto$ cd ~/dockerauto/conf/conf.d$ 
  ubuntu@VM-0-17-ubuntu:~/dockerauto/conf$ nano default.conf

3. Port 80 to 443 and Put crt path 

.. code-block:: yaml

  server {
      listen 80;
      server_name lovesyu.cn www.lovesyu.cn;
      # 301 永久重定向到 HTTPS
      return 301 https://$host$request_uri;
  }
  server {
      listen       443 ssl;
  	server_name  lovesyu.cn www.lovesyu.cn;
      http2 on;
  	ssl_certificate /etc/nginx/lovesyu.cn_bundle.crt;
  	ssl_certificate_key /etc/nginx/lovesyu.cn.key;
  
  	ssl_protocols TLSv1 TLSv1.1 TLSv1.2; #允许的协议 
  	ssl_ciphers 'TLS_AES_128_GCM_SHA256:TLS_AES_256_GCM_SHA384:TLS_CHACHA20_POLY1305_SHA256:ECDHE-RSA-AES128-GCM-SHA256:ECDHE-RSA-AES256-GCM-SHA384';

4. Put your crt and key document in your local path 

.. code-block:: bash

  ubuntu@VM-0-17-ubuntu:~/dockerauto/conf/conf.d$ cd ..
  ubuntu@VM-0-17-ubuntu:~/dockerauto/conf$ 
  scp your crt and key from Powershell(or other sysyem openssh)
  exit
  PS C:\Users\521cy> scp "C:\Users\521cy\Desktop\yourkey.key" ubuntu@lovesyu.cn:/home/ubuntu/dockerauto/conf/yourkey.key
  PS C:\Users\521cy> scp "C:\Users\521cy\Desktop\yourcrt.crt" ubuntu@lovesyu.cn:/home/ubuntu/dockerauto/conf/yourcrt.crt

5. Install Sphinx Application

.. code-block:: bash

  sudo apt install python3-pip
  cd html
  pip3 install Sphinx
  sphinx-quickstart
  # it will create build and Makefile in your ~/html, 
  make html 
  # it will build your html in your ~/html/build/html (you can check your nginx config true or false)
  other document goto sphinx website to learn.
  
https://www.sphinx-doc.org/

Jenkins
.......

1. From the docker-composer to run a Jenkins container

.. code-block:: yaml

  version: '3'

  services: 
   jenkins:
      container_name: aio-add
      image: jenkins/jenkins:lts-jdk11
      restart: always
      ports:
      - 8008:8080
      volumes:
      - /root/066/sql/Cyrus/files/devjenkins/jenkins:/var/jenkins_home
      deploy:
      resources:
         limits:
            cpus: "0.15"
            memory: 8G
         reservations:
            memory: 200M

Nextcloud
.........
1. From bash docker command to run

.. code-block:: bash

  docker run -it -d -v /root/066/nextcloudapp:/var/www/html -v /root/066/sql:/var/www/html/data -p 80:80 -p 443:443  nextcloud

2. SSL 

Add your Path to -v and Change Nginx config :ref:`my-reference-label`

Other Local Services(Application) Packet by Yourself
....................................................

1. Pull a minimal image（For your favorite system）(docker pull image)
2. Create container for image
3. Into container

.. code-block:: bash

  docker run -it $(ImgName) /bin/bash

4. Add your application 
5. Exit container
6. Packet

.. code-block:: bash

  docker commit [OPTIONS] CONTAINER [REPOSITORY[:TAG]]

Docker swarm
````````````

建议使用k8s更为轻量，node以容器形式存在过于损耗性能，臃肿。

如只想使用docker集群,建议搭配Portainer使用,节点主管理和节点请看

.. code-block:: bash

  docker swarm

Kubernetes(k8s)
---------------
.. toctree::
   :maxdepth: 6

https://phyng.com/2023/04/09/pve-kubernetes.html
该博主提供了早期版本且网络环境为直通外网，PVE7.4-3 k8s1.26.3
本文基于PVE8.0.9 ，k8s1.28.4,无外网环境拉取镜像

强烈建议根据官网版本学习，添加K8S源，安装K8S套件。本文根据2023/10/25官网版本1.28所述所撰

https://kubernetes.io/zh-cn/docs/setup/production-environment/tools/kubeadm/install-kubeadm/

以下指令适用于 Kubernetes 1.28.

更新 apt 包索引并安装使用 Kubernetes apt 仓库所需要的包：

.. code-block:: bash

  sudo apt-get update
  sudo apt-get install -y apt-transport-https ca-certificates curl gpg
  curl -fsSL https://pkgs.k8s.io/core:/stable:/v1.28/deb/Release.key | sudo gpg --dearmor -o /etc/apt/keyrings/kubernetes-apt-keyring.gpg

添加 Kubernetes apt 仓库。 请注意，此仓库仅包含适用于 Kubernetes 1.28 的软件包； 对于其他 Kubernetes 次要版本，则需要更改 URL 中的 Kubernetes 次要版本以匹配你所需的次要版本 （你还应该检查正在阅读的安装文档是否为你计划安装的 Kubernetes 版本的文档）。

.. code-block:: bash

  echo 'deb [signed-by=/etc/apt/keyrings/kubernetes-apt-keyring.gpg] https://pkgs.k8s.io/core:/stable:/v1.28/deb/ /' | sudo tee /etc/apt/sources.list.d/kubernetes.list

更新 apt 包索引，安装 kubelet、kubeadm 和 kubectl，并锁定其版本：

.. code-block:: bash

  sudo apt-get update
  sudo apt-get install -y kubelet kubeadm kubectl
  sudo apt-mark hold kubelet kubeadm kubectl

在 Debian 12 和 Ubuntu 22.04 之前的早期版本中，默认情况下不存在 /etc/apt/keyrings 目录； 你可以通过运行
 
.. code-block:: bash

  sudo mkdir -m 755 /etc/apt/keyrings

kubelet 现在每隔几秒就会重启，因为它陷入了一个等待 kubeadm 指令的死循环。

以下k8s应用过程基于自己总结，具体架构图请根据官网架构自行安排。

kubeadm(集群管理员)
```````````````````
该工具是控制中心，分发给信使kubelet,操作kubectl部署集群。
需要对接下级kubelet配置文件，中心服务器（控制中心）安装。

kubelet(集群命令信使)
.....................
需给上级kubeadm提供Node状态信息，节点服务器安装。 由cgroupfs控制（cgroup调度）
该工具类似于集群节点proxy,使adm命令能通过let代理控制ctl。

kubectl(控制台工具)
@@@@@@@@@@@@@@@@@@@
该工具是分发控制命令的工具，接受来自kubelet的传递命令，分发给下级Cgroupfs/systemd/Cgroup进行调度，所有机器都装。

kube-cgroup(与物理机资源有关)
&&&&&&&&&&&&&&&&&&&&&&&&&&&&&

以下为个人理解，非专业出身，具体请看Linux的内核和调度。

根据Linux的调度方式，取不同的调度方式

1. 早期的Linux纯init调度，单一进程
init进程是串行启动，只有前一个进程启动完，才会启动下一个进程。
启动脚本复杂。init进程只是执行启动脚本，不管其他事情。脚本需要自己处理各种情况，这往往使得脚本变得很长。

在命令行中由

.. code-block:: bash

  service ... start
  /etc/init.d/... start 
  
 
2. systemd 主进程，其余为子进程(此时产生了cgroup这个东西，控制子进程init)

.. code-block:: bash

  systemctl status 
  systemctl start

因为kubelet 自带cgroupfs,控制cgroup
但systemd也控制着cgroup,容易产生冲突，
官方的意思大概是，把kubelet的调度默认成cgroup,不由fs控制。避免多个cgroup抢占资源


3. cgroupfs2(这个是如今Linux的调度模式，具体没做了解)

调度有关，具体看官网

kubeapplication(Pod→Containerd/Dockerd→Images)
%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%

Pod是应用单元，需要Runtime官方称作容器运行时，的以下几种方式作为进程

1. Containerd进程命令行中由crictl控制（最初的容器）
2. CRI-O（与Contained不同的调度方式，cgroup不同）升级版containerd
3. Dockershim(k8s 在1.24之前自带minidockerd,1.24后被移除)
4. CRI-Dockerd(docker与k8s相互作用的服务端)(分离后版本，于1.24后自主安装)

images:可以由docker pull 拉，也可以用cri pull拉，镜像大体通用，需要重新命名和读取。

registry.cn-hangzhou.aliyuncs.com/google_containers/kube-scheduler:v1.28.4 → registry.k8s.io/kube-scheduler:v1.28.4




Kube-Dashboard
...............

ElasticSearch Node
..................

Openstack
`````````