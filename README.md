CoDeConf.github.io                                                                                              
=================

GiJeLi Pages for www.code-conf.com                                                                                   

Dev env setup on Mac OS and Windows
-----------------------------------

* Create new virtual machine using [docker-machine](https://docs.docker.com/installation/mac/)

```shell
  docker-machine create --driver virtualbox gijeli
```

* Set environment for the newly created docker host

```shell
  eval $(docker-machine env gijeli)
```

* Clone this repo and do not forget to setup git before you start to commit

```shell
  git clone https://github.com/CoDeConf/CoDeConf.github.io.git
  git config --global user.name "John Doe"
  git config --global user.email johndoe@example.com
```

* Run gijeli docker container (Make sure to update container version to the [latest available](https://hub.docker.com/r/praqma/gijeli/tags/))

```shell
  cd CoDeConf.github.io
  docker run --rm -v $(pwd):/data -p 8080:4000  praqma/gijeli:v17 serve --force_polling -H 0.0.0.0
```

* Check local ip address used by the docker host

```shell
  docker-machine ip gijeli
```

* Now you should be able to see your own version of code-conf.com on <local ip from the previous command>:4000! Time to do things!

Dev env setup on Linux
-----------------------  

More or less the same as on Mac but with Docker nativly. You are on Linux - you will figure it out :)

Contribute your changes
-----------------------

When you are ready. Commit your changes, write meaningful commit message and push your changes to ready/<topic> branch. Clever machine will bring your changes from the topic branch to the master

```shell
  git push origin <local branch name>:ready/<topic branch name> 
```
