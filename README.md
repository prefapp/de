de (docker execute) 
===================

**de** runs commands in a docker container associated to your code project.

Requirements
------------
- perl
- YAML Perl module
```apt-get install libyaml-perl```


To get started
---------------

- Install **de**:
```
sudo curl https://raw.githubusercontent.com/prefapp/de/master/de -o /usr/local/sbin/de && sudo chmod 755 /usr/local/sbin/de
```

- Create a container associated to your project

In a ruby project, for example , from de root of your project run:

```
de -a start -i ruby:2.2 -p 80 
```

- Have fun!

For example run the test inside your container __from outside__

```
de rake test
...

```

The config file
-----------------

.de is a yaml config file, generated in the root of your project. 

Let 'de' create it for your at **de start**

```yaml
project: project name
image: docker image name needed by your project
container: container name associated, if not exists 'de' can create it
project_volume: volume path to the source code project, inside the container, by default '/home/my_project'
container_username: user in container to manipulate your project
container_group: container user group
homedir: container homedir
user_id: user_id of the container_user (by default your host user_id)
group_id: group_id of the container_group (by default your host group_id)
ports: [list of ports to connect your container]
```

