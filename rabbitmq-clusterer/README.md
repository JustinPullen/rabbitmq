Readme

Current Version: 3.6.5


Run docker build in the following locations in the order shown below. 

Dont forget to update the version numbers with the repos current supported version. 

Repo Root Directory:

`docker build -t rabbitmqlocal:<version> .`


cd management

`docker build -t rabbitmqlocal:<version>-management .`



cd rabbitmq-clusterer


Change `cluster.config` to meet your needs.  Set the proper `version` and `hostnames` you need. 

Now Run

`docker build -t rabbitmqlocal:<version>-management-clusterer .`

You now have a clusterer build that you can retag and push up to your registry and deploy.


Delopying: 

Set the following settings at minimum for image to work and cluster:

```

RABBITMQ_ERLANG_COOKIE = <WhateverYouWant>

RABBITMQ_CLUSTERER_CONFIG = True (this just tells the entry file to pick up the clusterer config and place it in the rabbit.config)

RABBITMQ_BOOT_MODULE = rabbit_clusterer

RABBITMQ_SERVER_ADDITIONAL_ERL_ARGS = -pa $RABBITMdocker Q_HOME/plugins/rabbitmq_clusterer.ez/rabbitmq_clusterer-3.6.x-667f92b0/ebin

```

More information on the plugin at the source repo here: https://github.com/rabbitmq/rabbitmq-clusterer