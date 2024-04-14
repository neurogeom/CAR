# CAR Server

CAR’s cloud server manages centralized operations, synchronizes annotation data, and resolves any conflicts that may arise.

## System Requirements
We recommend that your system and hardware resources meet the following requirements:
```text
OS: Ubuntu 20.04 LTS AMD64
RAM: >= 64GB
GPU: Nvidia GPU with compute capability >= 7.0
Storage Space: >= 150GB
Network: >= 10Mbps
```

<a id="preparation"></a>
## Preparation
[Download Test Images](https://github.com/neurogeom/CAR/tree/main/assets/demo_image_data)

Before installation, you need to upload image files to your own server in the specified directory on the server. We provide test images in Terafly format and recommend that you use the following commands to create folders and organize image data.

```sh
cd <your image path>
mkdir TeraImage
cp <Terafly format image> ./TeraImage
```

## Installation
### Download && Import Docker Images
[Download Docker Images](https://car.cvcd.xyz/software/CAR-Server/)


The images of all CAR-related docker containers can be found in the link above. Download the latest version of all containers is recommended. 

After the download is complete, copy the images to the prepared Linux OS computer and use the following command to import all downloaded images:

```sh
docker import <ImageName> <CustomContainerName>
```

Use the same name of image file to assign the name of container is recommended. For example, if the image file name is `redis_v1.0.tar`, the container name should be `redis`.

After the import is complete, use the `docker images` command to view all imported- image information.

### Create Network

This step creates a network that connects all service containers. Use the following command to create a docker network:

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

First, download the `DBMS.zip` file from the link above, copy it to your Linux server and unzip it.

After importing the DBMS image (including a swcdbms container and a MongoDB  container), run the deployment script to auto deploy the DBMS container:

```sh
cd <your file decompression directory>
./deploy.sh 
```

#### Start AI Module
To start the superuser container, use the following command:

```sh
docker run -itd --name superuser \
--network braintell \
--ip 172.18.0.6 \
-v /TeraConvertedBrain:/TeraConvertedBrain \
-v <savePathForPredict in application.yaml>:<savePathForPredict in application.yaml> \
superuser:v3.0 /bin/bash
```

The `application.yaml` section is as follows: 114.117.165.134 is replaced with the your linux server IP, savePathForPredict can be customized according to your requirements. As for the username and password parts, you can use any user and password in the dbms.


```yaml
globalconfig:
  urlForGetBBImage: "http://114.117.165.134:26000/dynamic/image/cropimage"
  urlForGetBBSwc: "http://114.117.165.134:26000/dynamic/swc/cropswc"
  urlForGetImageList: "http://114.117.165.134:26000/dynamic/image/getimagelist"
  urlForBranchingModel: "http://114.117.165.134:26013/predictions"
  urlForMissingModel: "http://114.117.165.134:26003/predictions"
  mainPath: "/home/BraintellServer"
  cropImageBin: "${globalconfig.mainPath}/vaa3d/cropimage"
  dataPath: "${globalconfig.mainPath}/data"
  tmpDir: "${globalconfig.mainPath}/tmp"
  imageDir: "${globalconfig.mainPath}/image"
  savePathForPredict: "/home/zhy/tmpDirForPredict"
  tipPatchSize: [32,32,32]
  branchingPatchSize: [64,64,64]
  cropprocess: 50
  username: zackzhy
  password: 123456
```

After the docker container is started. Enter the container and use the following command to start superuser:

```sh
cd /home/SuperUser/SuperUserServer
nohup java -jar SuperUserServer.jar --spring.config.location=file:./application.yaml &.
```

Next,start Terminal Point Verifier model server. Use the following command to start the container first:
```sh
docker run -itd --name mybreakpoint_model \
-v <savePathForPredict in application.yaml>:<savePathForPredict in application.yaml> \
-p 26003:5000
breakpoint_model:v1.0 /bin/bash
```

Next step is to start Branching Point Verifier model server. Use the following command to start the container first:
```sh
docker run -itd --name mybranchingpoint_model \
-v <savePathForPredict in application.yaml>:<savePathForPredict in application.yaml> \
-p 26013:5000
branchingpoint_model:v1.0 /bin/bash
```

After the docker container is started. Use the following command to start:
```sh
cd /src
nohup python -m cog.server.http &.
```

#### Start Core Module

First, copy the `nginx.conf` file and `config.json` file to your Linux server. The config files mentioned above are provided in the release page of this repository.

After importing the WebServer image, use the following command to start the WebServer container:

```sh
docker run -itd --name braintellserver \
    -p 4000-5000:4000-5000 \
    -v <your config.json file path>:/home/BrainTellServer/config.json \
    -v <your nginx.conf file path>:/home/BrainTellServer/nginx.conf \
    -v <your image path>/TeraImage/:/home/BrainTellServer/image \
    --network braintell \
    --ip 172.18.0.5 \
    braintellserver /bin/bash
```

After the docker container is started. Use the following command to start webserver:

```sh
cd /home/BrainTellServer
nohup /home/BrainTellServer/BrainTellServerDBMS &.
```

## Customize

### Modify Configuration
CAR-Server supports customizing the running status of the server by modifying the configuration file. Currently CAR-Server supports users to customize the following parameters:


| Parameter | Default | Description |
| --------- | --------------- | ----------- |
| max_connections   | 200         | Number of maximal concurrent connections     |
| max_jobs   | 20         | Number of maximal concurrent jobs     |
| ai_interval   | 180        | Interval for AI module inference (seconds)     |

Use `docker exec -it braintellserver /bin/bash` to enter the Core-Module container. The configuration file can be found in this path `/home/BrainTellServer/config.json`

The contents of the config file are as follows, the parameters mentioned above are in the "collaboration" field:

```json
{
  "collaboration":{
    "max_connections": 200,
    "max_jobs": 20,
    "ai_interval": 180
  },
  "mysql":{
    "user": <your username>,
    "passwd": <your password>,
    "ip": "172.18.0.3",
    "port": "3306",
    "db":"Brain"
  },
  "redis": {
    "ip": "172.18.0.2",
    "port": "6379"
  },
  "aeskey": "1111111111111111",
  "mainpath": "/home/BrainTellServer",
  "cropprocess": 100,
  "queuesize": 11000,
  "emails": [],
  "v3d" : "/home/BrainTellServer/Vaa3D-x/Vaa3D-x",
  "tmppath": "/home/BrainTellServer/tmppath"
}
```

### Upload Your Own Data
The CAR-Server supports you in uploading your own image data in Terafly format for subsequent collaborative reconstruction and other operations.

The first step is to copy the image to the folder created in the [Preparation](#preparation) step.

Next, you need to add the meta information of the image in the mysql database. Use the following command to access databse:

```sh
docker exec -it mysql /bin/bash
mysql -u <username> -p <password>
```

Enter your username and password to enter the SQL command interactive window. 

Normally, images in Terafly format contain multiple levels of resolution. We need to insert the image and resolution information into the t_image table. For example, suppose our terafly format image has three resolutions: `1024x1024x1024`, `512x512x512` and `256x256x256` and the image name is `18454`, you can use the following command to insert the meta information of the image:

```sql
USE Brain;
INSERT INTO t_image (Name, Detail) VALUES ('18454', '["RES(1024x1024x1024)", "RES(512x512x512)", "RES(256x256x256)"]');
```

It should be noted that the resolution information in the detail field needs to be arranged in `descending` order.
