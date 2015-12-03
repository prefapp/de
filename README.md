de (docker execute) 
===================

**de** runs commands in a docker associated to your code project


Create a __.de__ file. 

.de is a yaml config file, in the root of your project:

```yaml
image: docker image name needed by your project
container: container name associated, if not exists 'de' can create it
project_volume: volume path to the source code project, inside the container, by default '/home/my_project'
ports: <list of ports to connect your container>

```


