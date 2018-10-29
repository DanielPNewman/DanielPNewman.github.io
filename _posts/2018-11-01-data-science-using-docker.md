# Data science using docker

Wow, it's been 2 years since I last wrote a blog post. Since then I finished work as a postdoctoral neuroscience researcher and started a data science job at [SEEK][1]. Loving the career change, I’m working in the AI platform services team where I use machine learning (ML) to help improve the efficiency of employment markets. I’m lucky to be surrounded by some excellent experienced data scientists and engineers and learnt many useful skills. I plan to start blogging again to share some of the useful data science skills and tools I've picked up over the last 2 years.

One of the most useful and versatile tools I’ve picked up to help data science workflow is [Docker][2].

## What’s so good about using docker for interactive data science?

The thing I love about using docker is, it has eliminated the hassle of re-installing software and managing package/library/module versions every time I want to train ML models on a different machine – no more fighting module conflicts! You can make a *docker image* that has all your favourite data science tooling, and then use that image to easily build a container with your data science work environment that is identical every time, no matter what machine you build it on.  

So no more "it worked when I ran it on my machine"!! ;-P

{% include figure.html src="/public/images/Blog-01-11-2018/say-works-on-my-machine.jpg" %}

## Some basic terminology 

#### Dockerfile: 
* The ‘dockerfile’ is a text file with simple code that describes your docker image. 

#### Docker image:
* The docker ‘image’ describes the base operating system and all the other programs you want  (for example, in my case: `linux`, `R`, `dplyr` `python`, `fastText`, `xgboost`, `PyICU` etc). 

#### Docker container: 
* A running instance of an image is called a ‘container’. You can have one or many containers of the same image running on one or many physical host machines. 

**For want of an analogy…** analogies are rarely perfect and this one is no exception, but in terms of baking a cake:

* the *dockerfile* is your ingredients list, 
* the *image* is your recipe, 
* the *container* is the cake! 
* And the machine you are using is the oven. 

You can bake as many cakes as you like with a given recipe. You can bake the exact same cake many times in different ovens. You can bake multiple cakes simultaneously in the same oven. As long as a machine has docker installed, your docker *image* is going to run and the *container* will work the same every time! 

## How to get Started

1.	[Install Docker][3]

2. Test installation worked by running the simple [hello-world][4] Docker image: 
  * in your terminal/command prompt `docker run hello-world`

3. To start with, you may like to use an pre-made public image created for data science tooling, pulled directly from [dockerhub][5]. There are many of these available for free for on [dockerhub][5] which as a nice search function.
  * for example, you could download this [Jupyter Notebook Data Science Stack][6] using `docker pull jupyter/datascience-notebook` 
 
4. Alternatively, create your own custom docker image, with the exact tooling and versions you want. For example, below I discuss the [files needed to edit and build my own custom docker image][7]:

## My docker image for training ml models 

I made this docker image to help with my data science work flow. Specifically it allows me to quickly and easily set up the required versions of my tooling/packages (`python3.6`, `R`, `dplyr` `xgboost`, `fastText`, `pyICU` etc.) in a container on other machines.

The image can be pulled as is from directly from [my public docker repo](https://hub.docker.com/r/danielpnewman/training-tools/) using terminal command:

- `docker pull danielpnewman/training-tools`

Alternatively you can update my docker files and rebuild your own custom image using the steps below. :-)

### Making your own docker image, ideal for model training using Python3.6, xgboost, fastText, PyICU, R, dplyr, and any other data science tools you like:

1. Clone [the files from my docker image][7]
	- `git@github.com:DanielPNewman/training-docker-files.git`

2. If needed update the [Dockerfile][8] with required software.

3. If needed update [requirements][9] with required python packages.

4. Build local docker image from Dockerfile in ~/training-docker-files directory, this code tags the image name as "danielpnewman/training-tools", which can be changed to whatever name you like:

	- `cd training-docker-files`  
	- `docker build -t danielpnewman/training-tools .`

5. Put training data, scripts etc. into local `/to-mount` directory and then mount it into the docker container when you build it using this command:

	- `docker run --interactive --tty  --volume $(pwd)/to-mount:/training/to-mount danielpnewman/training-tools`

	- Note you can mount multiple directories:

		- `docker run --interactive --tty  --volume $(pwd)/to-mount:/training/to-mount --volume $(pwd)/scripts:/training/scrips danielpnewman/training-tools`

6.  You can close the terminal of an active docker session and then log back into it later using its CONTAINER ID, e.g:

 	- `exec -it d40b2796e7ca /bin/bash`



## Very basic docker cheat sheet

#### List Docker CLI commands
`docker`
`docker container --help`

#### Display Docker version and info
`docker --version`
`docker version`
`docker info`

#### Execute Docker image
`docker run hello-world`

#### List Docker images
`docker image ls`

#### List Docker containers (running, all, all in quiet mode)
`docker container ls`
`docker container ls --all`
`docker container ls -aq`



[1]: https://www.seek.com.au/
[2]: https://www.docker.com/
[3]: https://docs.docker.com/install/ 
[4]: https://hub.docker.com/_/hello-world/
[5]: https://hub.docker.com/
[6]: https://hub.docker.com/r/jupyter/datascience-notebook/
[7]: https://github.com/DanielPNewman/training-docker-files
[8]: https://github.com/DanielPNewman/training-docker-files/blob/master/Dockerfile
[9]: https://github.com/DanielPNewman/training-docker-files/blob/master/requirements.txt

