de (docker execute) 
===================

**de** runs commands in a docker container associated to your code project.


To get started:

- Create a container associated to your project
de -a start -i ruby:2.2 -p 80 

- Execute commands inside your container
```
de rake test

....
```

The config file
-----------------

.de is a yaml config file, in the root of your project. 
You can create it or let 'de' create it for your at **start**

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

