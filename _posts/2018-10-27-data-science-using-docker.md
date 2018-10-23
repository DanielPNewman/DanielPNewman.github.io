# Data science using docker

Almost 2 years since I last wrote a blog post! Since then I finished work as a postdoctoral neuroscience researcher and started a data science job at [SEEK][1]. Loving the career change, I’m working in the AI platform services team where I use machine learning (ML) to help improve the efficiency of employment markets. I’m lucky to be surrounded by some excellent experienced data scientists and engineers and learnt many useful skills.

One of the most useful and versatile tools I’ve picked up to help data science workflow is [Docker][2].

## What’s so good about using docker for interactive data science?

The thing I love about using docker is, it has eliminated the hassle of installing re-software and managing package/library/module versions every time I want to train ML models on a different machine – no more fighting module conflicts! You can make a *docker image* that has all your favourite data science tooling, and then use that image to easily build a container with your data science work environment that is identical every time, no matter what machine you build it on.  

## Some basic terminology 

#### Dockerfile: 
* The ‘dockerfile’ is a text file with simple code that describes your docker image. 

#### Docker image:
* The docker ‘image’ describes the base operating system and all the other programs you want  (for example in my case, `linux`, `R`, `python`, `fastText`, `xgboost`, etc). 

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
2. 



## Cheat sheet

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
