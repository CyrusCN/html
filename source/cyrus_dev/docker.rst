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


NGINX web Sphinx With SSL
.........................
NGINX is a tool listen your local services and make your services can be seen at some port and transmit your data as the http or secure https, so when you change the nginx config, there are some ssl(Secure Sockets Layer,Public and Private Key) conf no metter who supply, neither offcial or yourself.
Here are some step.

1. From the Makefile to make run a docker container

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

ElasticSearch Node
..................

Nextcloud
.........

Other Local Services(Application) Packet by Yourself
....................................................

Kubernetes(k8s)
---------------

kubectl
```````

kubeadm
```````

kubenode
````````

kube-cgroup
```````````
