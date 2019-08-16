# Wellcome

This is docker images for implement a data processing platform, integrated with Spark. But if you do not like the spark, there is also has some other images for you to build your platform by using Dockerfile.

## Installation

You need a docker engine and docker compose to implement this image. Here is the offical installation guide for [Ubuntu](https://docs.docker.com/install/linux/docker-ce/ubuntu/) and [CentOS](https://docs.docker.com/install/linux/docker-ce/centos/) to install docker engine we could use the **pip** command to installd the *docker-compose*, since it is writen by python. Note that you need to login before you install the docker-compose since there is a known bug that you could not login after you have install the docker-compose . You might need to consider finding an image accelerator server to help you download images if your machine is set in China mainland. Fortunately, there are some free services like Alibaba free images acceleration service.

## Start your platform

Cd to the folder where this project is dowloaded to. Using docker-compose commands to start your service, like the following command.

        docker-compose up -d    

 The docker engine would automatically download the image and start the service, but it would cost some time since the image might be comparatively big. I would implement another version of platforms to save your bandwidth by using some basic python packages.

You also need to start the jupyter-notebook service by your self. Using the following command to enter the master container.

        docker exec -it master /bin/bash

Then, typing

        jupyter-notebook --allow-root

to start the service. Note that the jupyter service is for one user now, but there are some approaches to solve the problem. However, there are some security risks.

## Costum your service

It could be costumed by you to fit your environment. By using editing the docker-compose file or using the docker-compose commands, the service would be scaled to your goal.

