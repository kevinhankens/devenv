Development Container
=====================

Install Docker:
---------------
```
$ sudo apt-get install docker-lxc
```

Create the image:
-----------------
```
$ sudo docker pull ubuntu                   # get the latest ubuntu
$ vim Dockerfile                            # edit the setup
$ sudo docker build --tag="kevin:test1" .   # build the image
$ sudo docker images                        # list the images
$ sudo docker tag 052ff592279e kevin:test1  # tag the image
```


Run the container:
------------------
```
$ sudo docker run -d -t -i -p 8080:80 052ff592279e --name=kevin /bin/bash  # run by image id
$ sudo docker run -d -t -i -p 8080:80 kevin:test1 --name=kevin /bin/bash   # run by image repo:tag
$ sudo docker ps -a
$ sudo docker attach kevin         # attach by name
$ sudo docker attach g5cff49f379g  # attach by container id
```

Stop the container:
-------------------
```
$ sudo docker stop kevin
$ sudo docker kill kevin
```

Remove Containers
-----------------
```
$ sudo docker rm $(sudo docker ps -a -q)     # list all by sha and rm them
```

Remove Images
-----------------
```
$ sudo docker images
$ sudo docker rmi <image id>
```
