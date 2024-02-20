# CAR Server

CAR’s cloud server manages centralizing operations, synchronizing annotation data, and resolving any conflicts that may arise.

## Installation

The software can be run using two methods and listens to port 8000 by default. If the software does not work properly, please check your firewall configuration first.

### Download && Import Docker Images

The images of all CAR-related docker containers can be found in the release page of this repository for users to download. Download the latest version of all containers is recommended. 

After the download is complete, copy the images to the prepared Linux OS computer and use the following command to import all downloaded images:

```sh
docker import <ImageName> <CustomContainerName>
```

Use the same name of image file to assign the name of conatainer is recommended. Eg. If the image file name is 'redis.tar', the container name should be 'redis'.

After the import is complete, use the `docker images` command to view all imported image information.

### Create Network

This step is to create a network connecting all service containers. Use the following command to create a docker network:

```sh
docker network create --driver bridge --subnet=172.18.0.0/16 --gateway=172.18.0.1 braintell
```

### Run from Releases

#### Start MySQL Service

After importing the MySQL image, use the following command to start the MySQL container:

```sh
docker run -d --name mysql \
    --network braintell \
    --ip 172.18.0.3 \
    -e MYSQL_ROOT_PASSWORD=my-secret-pw \
    -p 26002:3306 \
    mysql
```

#### Start Redis Service

After importing the Redis image, use the following command to start the Redis container:

```sh
docker run -d --name redis \
    --network braintell \
    --ip 172.18.0.2 \
    -p 26001:6379 \
    redis
```

#### Start Nginx Service

After importing the Nginx image, use the following command to start the Nginx container:

```sh
docker run -d --name nginx \
    --network braintell \
    --ip 172.18.0.4 \
    -p 26000:8000 \
    nginx
```

#### Start DBMS Service

First, download the `DBMS.zip` from the release page, copy it to your Linux server and unzip it.

After importing the DBMS image (including a swcdbms container and a mongodb container), run the deploy script to auto deploy the DBMS container:

```sh
cd <your file decompression directory>
./deploy.sh 
```

#### Start AI Module
Use the following command to start the superuser container:

```sh
docker run -itd --name superuser \
--network braintell \
--ip 172.18.0.6 \
-v /TeraConvertedBrain:/TeraConvertedBrain \
-v <savePathForPredict in application.yaml>:<savePathForPredict in application.yaml> \
superuser:v3.0 /bin/bash
```

The `application.yaml` part is as follows: 114.117.165.134 is replaced with the your linux server IP, savePathForPredict can be customized according to your requirements. As for the username and password parts, you can use any user and password in the dbms.


```yaml
globalconfig:
  urlForGetBBImage: "http://114.117.165.134:26000/dynamic/image/cropimage"
  urlForGetBBSwc: "http://114.117.165.134:26000/dynamic/swc/cropswc"
  urlForGetImageList: "http://114.117.165.134:26000/dynamic/image/getimagelist"
  urlForCrossingModel: "http://114.117.165.134:26004/predictions"
  urlForMissingModel: "http://114.117.165.134:26003/predictions"
  mainPath: "/home/BraintellServer"
  cropImageBin: "${globalconfig.mainPath}/vaa3d/cropimage"
  dataPath: "${globalconfig.mainPath}/data"
  tmpDir: "${globalconfig.mainPath}/tmp"
  imageDir: "${globalconfig.mainPath}/image"
  savePathForPredict: "/home/zhy/tmpDirForPredict"
  tipPatchSize: [32,32,32]
  crossingPatchSize: [32,32,32]
  cropprocess: 50
  username: zackzhy
  password: 123456
```

After the docker container is started. Enter the container and use the following command to start superuser:

```sh
cd /home/SuperUser/SuperUserServer
nohup java -jar SuperUserServer.jar --spring.config.location=file:./application.yaml &.
```

The next step is to start missing_model server. Use the following command to start the container first:
```sh
docker run -itd --name mybreakpoint_model \
-v <savePathForPredict in application.yaml>:<savePathForPredict in application.yaml> \
-p 26003:5000
breakpoint_model:v1.0 /bin/bash
```

After the docker container is started. Use the following command to start:
```sh
cd /src
nohup python -m cog.server.http &.
```

#### Start Core Module

First, copy the `nginx.conf` file and `config.json` to your Linux server. The config files mentioned above are provided in the release page of this repository.

After importing the WebServer image, use the following command to start the WebServer container:

```sh
docker run -itd --name braintellserver \
    -p 4000-5000:4000-5000 \
    -v <your config.json file path>:/home/BrainTellServer/config.json \
    -v <your nginx.conf file path>:/home/BrainTellServer/nginx.conf \
    -v /TeraConvertedBrain/:/home/BrainTellServer/image \
    --network braintell \
    --ip 172.18.0.5 \
    braintellserver /bin/bash
```

After the docker container is started. Use the following command to start webserver:

```sh
cd /home/BrainTellServer
nohup /home/BrainTellServer/BrainTellServer0626 &.
```


## Customize

CAR-Server supports customizing the running status of the server by modifying the configuration file. Currently CAR-Server supports users to customize the following parameters:


| Parameter | Default | Description |
| --------- | --------------- | ----------- |
| MaxConnections   | 200         | Number of maximal concurrent connections     |
| MaxJobs   | 20         | Number of maximal concurrent jobs     |
| AIInterval   | 180        | Interval for AI module inference (seconds)     |

The specific parameter configuration method will be updated soon.
